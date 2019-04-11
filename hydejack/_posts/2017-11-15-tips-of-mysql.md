---
id: 69
title: Tips of MySQL
date: 2017-11-15T04:47:46+00:00
author: Lucas
layout: post
guid: http://www.lucas-liu.com/?p=69
permalink: /2017/11/15/tips-of-mysql/
categories:
  - Database
  - MySQL
---
  * If you want to select limit rows which start after specific row, try this:

<pre class="brush: sql; title: ; notranslate" title="">select * from table order by name limit 5 offset 5; </pre>

&nbsp;

  * To select columns and display them as other names:

<pre class="brush: sql; title: ; notranslate" title="">select name as country, population as pop from country order by name; </pre>

&nbsp;

  * Sorting results by specific columns (sort the column first which is the closest to the order by, DESC is the keyword for descending order):

<pre class="brush: sql; title: ; notranslate" title="">select name, region from country order by region desc, name desc; </pre>

&nbsp;

  * Using LIKE keyword (uppercase and lowercase are treated the same):

<pre class="brush: sql; title: ; notranslate" title="">select name, population from country where name like '%island%' order by name; </pre>

&nbsp;

  * If you want to use a single quote to the table, eg. O&#8217; Brien, try this:

<pre class="brush: sql; title: ; notranslate" title="">select * from table where name = 'O'' Brien'; </pre>

&nbsp;

  * &#8216;%&#8217; is a wildcard for multiple characters and &#8216;_&#8217; is a wildcard for single character.

&nbsp;

  * To select rows which contain specific values, we can use IN keyword:

<pre class="brush: sql; title: ; notranslate" title="">select * from country where continent in ('Europe', 'Asia'); </pre>

&nbsp;

  * We can use logic expression like OR, AND, NOT. after WHERE expression.

&nbsp;

  * Except LIKE and IN, we can also filter results by REGEXP: [MySQL REGEXP Usage](http://www.runoob.com/mysql/mysql-regexp.html)

&nbsp;

  * Assuming test has 3 columns (a, b, c), we can insert results of a query into the test table:

<pre class="brush: sql; title: ; notranslate" title="">insert into test(a, b, c) select id, name, description from item; </pre>

&nbsp;

  * Updating the table:

<pre class="brush: sql; title: ; notranslate" title="">update test set c = "Hello World" where a = 1; </pre>

&nbsp;

  * Deleting a row from the table:

<pre class="brush: sql; title: ; notranslate" title="">delete from test where a = 2; </pre>

&nbsp;

  * Deleting all the rows of the table:

<pre class="brush: sql; title: ; notranslate" title="">truncate table test; </pre>

&nbsp;

  * Deleting the table (everything! including the metadata):

<pre class="brush: sql; title: ; notranslate" title="">drop table test; </pre>

&nbsp;

  * Using DISTINCT keyword to avoid duplicate results:

<pre class="brush: sql; title: ; notranslate" title="">select name from test; </pre>

vs.

<pre class="brush: sql; title: ; notranslate" title="">select distinct name from test </pre>

&nbsp;

  * To select rows with NULL, we can only use IS keyword:

<pre class="brush: sql; title: ; notranslate" title="">select * from test where a is null; </pre>

&nbsp;

  * Creating a database, opening and switching to that database (then create a table and insert some values) :

<pre class="brush: sql; title: ; notranslate" title="">create database foo;

-- switching to the database

use foo;

create table bar (a int, b text);

insert into bar values (1, 'bar');

select * from bar; </pre>

&nbsp;

  * Deleting a database:

<pre class="brush: sql; title: ; notranslate" title="">drop database foo; </pre>

&nbsp;

  * Creating a table and showing the details of it:

<pre class="brush: sql; title: ; notranslate" title="">-- use innodb if you can

-- charset will influence the collation which is the rule for comparing and sorting data

create table test (

id integer,

name varchar(255),

zip char(10)

) engine = Innodb default charset = utf8;



-- the next line is a mysql specific statement

-- it will show the table's details

describe test;



-- show all the tables' details in the database

show table status;



-- select the table test using LIKE

show table status like 'test';

</pre>

  * It is a good pratice to use IF EXISTS keyword:

<pre class="brush: sql; title: ; notranslate" title="">drop table if exists test; </pre>

&nbsp;

  * Index is one of the constraints of SQL:

&nbsp;

  * To show the indexes of a table:

<pre class="brush: sql; title: ; notranslate" title="">show indexes from test; </pre>

&nbsp;

  * Creating indexes while creating the table:

<pre class="brush: sql; title: ; notranslate" title="">drop table if exists test;

create table test(

id integer,

a varchar(255),

b varchar(255),

index ab (a, b)

-- key name will be ab

);

show indexes from test; </pre>

&nbsp;

  * Using indexes can speed up the looking up process, but it should be used correctly.

[SQL Indexes Pros & Cons (When to use indexes)](http://blog.csdn.net/pang040328/article/details/4164874)

[Why indexes can speed up the process? (Including some introductions to indexes)](http://www.cnblogs.com/xxiaoye/p/3679899.html)

&nbsp;

  * Using not null and setting default values:

<pre class="brush: sql; title: ; notranslate" title="">drop table if exists test;

create table test(

-- auto_increment will increase the id while inserting items

id integer auto_increment not null default 47,

a varchar(255)

) </pre>

&nbsp;

  * Primary key will include the not null and unique by design.

&nbsp;

  * Foreign key example:

<pre class="brush: sql; title: ; notranslate" title="">create table orders(

orderid int not null,

ordernumber int not null,

personid int,

primary key (orderid),

foreign key (personid) references persons(personid)

) </pre>

&nbsp;

  * To be more specific: [SQL Constraints](https://www.w3schools.com/sql/sql_constraints.asp)

&nbsp;

  * Selecting the last id that was inserted into the database:

<pre class="brush: sql; title: ; notranslate" title="">select last_insert_id(); </pre>

&nbsp;

  * To manipulate the columns of a table, we can use ALTER keyword:

<pre class="brush: sql; title: ; notranslate" title="">alter table test add d varchar(10);

alter table test drop d;

-- we can also decide the position of the added column

alter table test add b varchar(10) after a; </pre>

&nbsp;

  * MySQL supports 3 fundamental data types: Numeric, String, Dates and Times.

It also supports special types like Boolean, Enumerations and Sets.

&nbsp;

  * To check the timezone of current database system (including setting time zone) :

[Time Zone List](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)

<pre class="brush: sql; title: ; notranslate" title="">show variables like '%time_zone%';

-- display current timestamp

select now();

&nbsp;

-- to set the time zone to us eastern

set time_zone = 'US/Eastern'; </pre>

&nbsp;

  * Bit:

<pre class="brush: sql; title: ; notranslate" title="">drop table if exists test;

create table test (

id serial,

a bit(3),

b bit(5)

); </pre>

&nbsp;

  * Boolean:

<pre class="brush: sql; title: ; notranslate" title="">drop table if exists test;

create table test (

a boolean,

b boolean

); </pre>

&nbsp;

  * Enumeration:

<pre class="brush: sql; title: ; notranslate" title="">drop table if exists test;

create table test (

id serial,

a enum( 'A', 'B', 'C')

);

insert into test (a) values ('A');

insert into test (a) values ('B');

insert into test (a) values ('C');

-- which is equal to the following

insert into test (a) values (1);

insert into test (a) values (2);

insert into test (a) values (3); </pre>

&nbsp;

  * Set:

<pre class="brush: sql; title: ; notranslate" title="">-- it is similar to enumeration but it can insert multiple values

drop table if exists test;

create table test (

id serial,

a set( 'A', 'B', 'C')

);

insert into test (a) values ('A');

insert into test (a) values ('A', 'B');

insert into test (a) values ('A', 'B', 'C');

-- set is using bits to represent the index

-- the following will have the same result

insert into test (a) values (1); -- which is 001

insert into test (a) values (3); -- which is 011

insert into test (a) values (7); -- which is 111 </pre>

&nbsp;

  * Maximum storage per row: 65,535 bytes

&nbsp;

  * Some functions for string:

<pre class="brush: sql; title: ; notranslate" title="">-- LEFT, RIGHT, MID

select name, left(name, 3), right(name, 3), mid(name, 2, 3) from country;

&nbsp;

-- CONCAT

select concat(name, ', ', localname) from country;

&nbsp;

-- CONCAT_WS: concat with sperator

select concat_ws(', ', name, localname, region, continent) from country;

&nbsp;

-- LOCATE: locate the first string's position in the second parameter

select name, locate('island', name) from country where name like '%island%';

&nbsp;

-- UPPER, LOWER, REVERSE

select name, upper(name) from country; </pre>

&nbsp;

  * Aggregate functions like COUNT and GROUP BY keyword:

<pre class="brush: sql; title: ; notranslate" title="">select continent, count(*) as count from country group by continent order by count desc;

-- There are also some other aggregate functions, like GROUP_CONCAT, AVG, MIN, MAX, SUM, STD... </pre>

&nbsp;

  * We can use CASE keyword for flow control.

&nbsp;

  * Using transection, the time spent on the processes will be much less and we can choose to COMMIT or ROLLBACK the transations.

&nbsp;

  * Using triggers, we can add some logic to a table BEFOR or AFTER some specifc processes happen.

&nbsp;

  * SQL Stored Routines:

Stored FUNCTION

Stored PROCEDURE

&nbsp;