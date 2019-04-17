---
id: 202
title: 'Example: JDBC Better Practice(Stream SQL Request)'
date: 2018-07-25T17:37:41+00:00
author: Lucas
layout: post
guid: http://www.lucas-liu.com/?p=202
permalink: /2018/07/25/example-jdbc-better-practicestream-sql-request/
categories:
  - Java
---
Months before, I gave an [example]({{site.baseurl}}/2017/11/16/sample-jdbc-good-practice/) about JDBC &#8220;good&#8221; practice. To be honest, I have been prepared to learn some better practices in the future. Because that one is too basic. I know there may not be a best practice of JDBC existing. But, I did learn some lessons from CMU courses and an internship in Japan. I would like to show you some interesting ideas. If you want to access the code, please feel free to check it [here](https://github.com/Lucas12138/StreamSqlRequest).

1) ResultSet and PreparedStatement always keep close to each other. Therefore, we can make them into a class, **DBResult**. Besides, normally, we need to keep track of affected rows number and generated keys. So, we include them in that class as well.

2) SqlRequest is not only a ConnectionManager now. Except for taking care of opening and closing connections, it will **treat** SQL string as well. 2 features are added here for the treat. We will be able to push **parameter**/**member** to the SQL request, which can remove a lot of duplicate code like setInt, setString etc. and make it easier to work with different data types. The other feature is the **callback** style. Java itself uses many callbacks, like [ActionListener](http://www.informit.com/articles/article.aspx?p=1998555&seqNum=3). To be simple, it&#8217;s passing interface as a parameter of a method. It can make code structure more flexible and elegant. In our case, we can easily add logic in **DAO.treat** as a lambda expression, which is actually creating an anonymous class that implements the **Handler** interface and overrides the interface&#8217;s onResult method. It&#8217;s very handy. I didn&#8217;t imagine that this callback style works so well with JDBC.

3) **DBBean** is added and very useful, too. It will be the parent of other specific beans. The reason for using this class is we will be able to generate beans with values inside. And we won&#8217;t have to set the value for each field every time. Basic **reflection** is used here. **buildFrom** is the method to build the bean from the ResultSet. In the example, AdminBean is a specific bean which extends from DBBean. One thing we need to be careful is that we should keep the field name in java and the field name in MySQL consistent.

4) **DAO** handles basic, general CRUD (create, read, update, delete) operations. And the create includes insert and upset. upset will check the key and update on duplicate. It can be helpful sometimes. Similar to bean structure, DAO is a parent class as well. More specific logic should be added to lower levels, like AdminDAO. There can be a TODO here, which is when there&#8217;re many complex queries, we should consider adding one more layer between DAO and AdminDAO (could be named as AdminCRUD etc.). And AdminCRUD will include some SQL string to handle some basic queries and the AdminDAO will take care of the complex logic after data are retrieved from the database. It&#8217;s better to implement the login in java rather than SQL string. Otherwise, the code size can grow extremely big.

5) Streaming when possible! Streaming here doesn&#8217;t only mean the stream().map() etc. **AdminStreamerDAO** is a DAO with streaming style. **streamedRead** won&#8217;t return anything. But, it uses callback and buffers to set an upper bound of memory usage. People do come across very **large tables** from time to time. Streaming can be necessary for those. OOM (out of memory) may be a common issue without streaming. Another important condition is that the primary key or efficient indexes should have **at least 2 fields**. Then, it can stream on one field and fetch beans partially with buffers.

I believe this might still not be the best practice. And there should have already had many good frameworks to use. But, I suppose ideas above are good enough for production level with not very high requirements or demands.

Finally, I would love to have your thoughts or comments. Please let me know if you can make it even better! Thanks!

&nbsp;

&nbsp;