---
id: 84
title: 'Example: JDBC Good Practice'
date: 2017-11-16T13:44:59+00:00
author: Lucas
layout: post
guid: http://www.lucas-liu.com/?p=84
permalink: /2017/11/16/sample-jdbc-good-practice/
categories:
  - Java
---
Suppose we are using MySQL on AWS RDS.

[Github Link](https://github.com/Lucas12138/JDBC-good-practice)

There could be three classes as follows:

**ConnectionManager:**

<pre class="brush: java; title: ; notranslate" title="">import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class ConnectionManager {

private static ConnectionManager instance = null;

private final String USERNAME = "*****";

private final String PASSWORD = "*****";

private final String M_CONN_STRING
= "jdbc:mysql://rds-mysql-t*******************.amazonaws.com:3306/";

private final String DBNAME = "*****";

private Connection conn = null;

private ConnectionManager() {
}

public static ConnectionManager getInstance() {
if (instance == null) {
instance = new ConnectionManager();
}
return instance;
}

private boolean openConnection() {
try {
conn = DriverManager.getConnection(M_CONN_STRING + DBNAME, USERNAME, PASSWORD);
return true;
} catch (SQLException e) {
System.err.println(e);
return false;
}

}

public Connection getConnection() {
if (conn == null) {
if (openConnection()) {
System.out.println("Connection opened");
return conn;
} else {
return null;
}
}
return conn;
}

public void close() {
System.out.println("Closing connection");
try {
conn.close();
conn = null;
} catch (Exception e) {
}
}

}

</pre>

**Admin:**

<pre class="brush: java; title: ; notranslate" title="">import java.io.Serializable;

public class Admin implements Serializable {

// becoming java beans, not useful in simple client application though
private static final long serialVersionUID = -5169442789450234938L;
private int adminId;
private String userName;
private String password;

public int getAdminId() {
return adminId;
}

public void setAdminId(int adminId) {
this.adminId = adminId;
}

public String getUserName() {
return userName;
}

public void setUserName(String userName) {
this.userName = userName;
}

public String getPassword() {
return password;
}

public void setPassword(String password) {
this.password = password;
}

}
</pre>

**AdminManager:**

<pre class="brush: java; title: ; notranslate" title="">import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class AdminManager {

private static Connection conn = ConnectionManager.getInstance().getConnection();

public static void displayAllRows() throws SQLException {
String sql = "select adminId, userName, password from admin";
try (Statement stmt = conn.createStatement(); ResultSet rs = stmt.executeQuery(sql);) {
System.out.println("Admin table: ");
while (rs.next()) {
StringBuffer bf = new StringBuffer();
bf.append(rs.getInt("adminId") + ": ");
bf.append(rs.getString("userName") + ", ");
bf.append(rs.getString("password"));
System.out.println(bf.toString());

}
}
}

public static Admin getRow(int adminId) throws SQLException {
String sql = "select * from admin where adminId = ?";
ResultSet rs = null;
try (PreparedStatement stmt = conn.prepareStatement(sql);) {
stmt.setInt(1, adminId);
rs = stmt.executeQuery();

if (rs.next()) {
Admin bean = new Admin();
bean.setAdminId(adminId);
bean.setUserName(rs.getString("userName"));
bean.setPassword(rs.getString("password"));
return bean;
} else {
System.err.println("No rows were found");
return null;
}

}
}

public static boolean insert(Admin bean) throws SQLException {
String sql = "insert into admin (userName, password) " + "values(?, ?)";
ResultSet keys = null;

try (PreparedStatement stmt = conn.prepareStatement(sql, Statement.RETURN_GENERATED_KEYS);) {
stmt.setString(1, bean.getUserName());
stmt.setString(2, bean.getPassword());
int affected = stmt.executeUpdate();
if (affected == 1) {
keys = stmt.getGeneratedKeys();
keys.next();
int newKey = keys.getInt(1);
bean.setAdminId(newKey);

} else {
System.err.println("No rows affected");
return false;
}

} catch (SQLException e) {
System.err.println(e);
return false;
} finally {
if (keys != null) {
keys.close();
}
}
return true;
}

public static boolean update(Admin bean) throws SQLException {
String sql = "update admin set " + "userName = ?, password = ? " + "where adminId = ?";
try (PreparedStatement stmt = conn.prepareStatement(sql);) {
stmt.setString(1, bean.getUserName());
stmt.setString(2, bean.getPassword());
stmt.setInt(3, bean.getAdminId());
int affected = stmt.executeUpdate();
if (affected == 1) {
return true;
} else {
return false;
}

} catch (SQLException e) {
System.err.println(e);
return false;
}
}

public static boolean update2(Admin bean) throws SQLException {
// Not as efficient as the first one
String sql = "select * from admin where adminId = ?";
ResultSet rs = null;
try (PreparedStatement stmt = conn.prepareStatement(sql, ResultSet.TYPE_SCROLL_INSENSITIVE,
ResultSet.CONCUR_UPDATABLE);) {

stmt.setInt(1, bean.getAdminId());

rs = stmt.executeQuery();

if (rs.next()) {
rs.updateString("userName", bean.getUserName());
rs.updateString("password", bean.getPassword());
rs.updateRow();
return true;
} else {
return false;
}

} catch (SQLException e) {
System.err.println(e);
return false;
} finally {
if (rs != null) {
rs.close();
}
}
}

public static boolean delete(int adminId) throws SQLException {
String sql = "delete from admin where adminId = ?";
try (PreparedStatement stmt = conn.prepareStatement(sql);) {
stmt.setInt(1, adminId);
int affected = stmt.executeUpdate();
if (affected == 1) {
return true;
} else {
return false;
}
} catch (SQLException e) {
System.err.println(e);
return false;
}
}
}
</pre>