---
id: 209
title: 17-682 Java EE Web Application
date: 2018-11-05T01:36:35+00:00
author: Lucas
layout: post
guid: http://www.lucas-liu.com/?p=209
permalink: /2018/11/05/17-682-java-ee-web-application/
categories:
  - Web Application
---
<div id="toc_container" class="no_bullets">
  <p class="toc_title">
    Contents
  </p>
  
  <ul class="toc_list">
    <li>
      <a href="#Introduction"><span class="toc_number toc_depth_1">1</span> Introduction</a>
    </li>
    <li>
      <a href="#Concepts"><span class="toc_number toc_depth_1">2</span> Concepts</a><ul>
        <li>
          <a href="#HTTP_HTML_CSS_and_Javascript"><span class="toc_number toc_depth_2">2.1</span> HTTP, HTML, CSS and Javascript</a>
        </li>
        <li>
          <a href="#Servlets_Tomcats"><span class="toc_number toc_depth_2">2.2</span> Servlets & Tomcats</a>
        </li>
        <li>
          <a href="#Threads"><span class="toc_number toc_depth_2">2.3</span> Threads</a>
        </li>
        <li>
          <a href="#Cookies_Sessions"><span class="toc_number toc_depth_2">2.4</span> Cookies & Sessions</a>
        </li>
        <li>
          <a href="#SQL_JDBC"><span class="toc_number toc_depth_2">2.5</span>  SQL & JDBC</a>
        </li>
        <li>
          <a href="#ORM_object-relational_mapping"><span class="toc_number toc_depth_2">2.6</span> ORM (object-relational mapping)</a>
        </li>
        <li>
          <a href="#Transactions"><span class="toc_number toc_depth_2">2.7</span> Transactions</a>
        </li>
        <li>
          <a href="#MVC_model_view_controller"><span class="toc_number toc_depth_2">2.8</span> MVC (model view controller)</a>
        </li>
        <li>
          <a href="#Tag_Libraries"><span class="toc_number toc_depth_2">2.9</span> Tag Libraries</a>
        </li>
        <li>
          <a href="#AJAX_asynchronous_javascript_and_XML"><span class="toc_number toc_depth_2">2.10</span> AJAX (asynchronous javascript and XML)</a>
        </li>
        <li>
          <a href="#Security"><span class="toc_number toc_depth_2">2.11</span> Security</a>
        </li>
        <li>
          <a href="#Cloud"><span class="toc_number toc_depth_2">2.12</span> Cloud</a>
        </li>
      </ul>
    </li>
    
    <li>
      <a href="#Practice"><span class="toc_number toc_depth_1">3</span> Practice</a>
    </li>
  </ul>
</div>

# <span id="Introduction">Introduction</span>

It&#8217;s another very good course led by [Jeff Eppinger](http://www.jeffeppinger.com/jle/). Before learning this course, my knowledge about web application development is not very structural. This very interesting course guided me through the concepts of HTML, javascript, CSS, threads, cookies, sessions, JSP, JDBC, ORM, transactions, MVC, tag libraries, AJAX, security, and cloud deployment. It provides me a structural understanding of how to build a basic java web application.

# <span id="Concepts">Concepts</span>

## <span id="HTTP_HTML_CSS_and_Javascript">HTTP, HTML, CSS and Javascript</span>

SaaS (software as a service) web application is not a new thing now. But, the trend is getting more obvious that web application is taking over the desktop software. For example, Google doc is very popular now and many people prefer it to Microsoft office.

There&#8217;re 2 basic kinds of web contents, static and dynamic. Although they&#8217;re 2 very different concepts, they often come hand-in-hand. Static content means the view will be the same across all the users. Dynamic content means it won&#8217;t remain constant. It will differ given different users or different inputs. To evolve from static content to dynamic content, we need at least 4 items. Firstly, we need to generate HTML with scripts or programs. Secondly, it should be able to access and update data. Thirdly, handling concurrency issues is important. Synchronization and transactions will be helpful. Last but not least, we need tools and techniques to make it easy to manage, such as MVC patterns, frameworks, IDEs etc.

In most cases, the connection will be maintained via IP stack as below:

<img class="alignnone size-medium wp-image-211" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-24-at-2.30.19-PM-300x192.png" alt="" width="300" height="192" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-24-at-2.30.19-PM-300x192.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-24-at-2.30.19-PM.png 424w" sizes="(max-width: 300px) 100vw, 300px" /> 

To interact with web applications, the most common approach is using the browser. So what is exactly a browser? Or what methods will it provide? A browser can manage protocol, such as http and ftp. It&#8217;s a HTML rendering engine so that we can see the beautiful pages. It can do caching, has support for javascript and java applets and it has the OS integration or interface.

Most web applications are based on http protocol. URI will specify the resources to be accessed. The http connection is under TCP and on port 80 by default. There&#8217;re 3 kinds of common request methods.

  * Safe methods have no side effects(or aren&#8217;t supposed to ): GET, HEAD, TRACE and OPTIONS
  * Idempotent methods(in simple words: methods will have same effects after the first request): PUT and DELETE
  * Update method: POST

GET and POST methods can pass parameters and are most commonly used. For more details: [HTTP methods.](https://www.tutorialspoint.com/http/http_methods.htm)

The request and response really need an address to go to, just like you need to put the address when you mail to your friend. Briefly, there&#8217;re 3 layers of addresses:

  * Low level, hardware address: MAC address
  * Routable address: IP address
  * High level, logical address: DNS hostname

Requests all need a port number to locate the application. Generally, Telnet=>23, SMTP=>25, RDP=>3389, and for production, HTTP=>80, SSL=>443, MySQL=>3306, for development, HTTP=>8080, SSL=>8443

Apache and Nginx are the most popular web servers. For Apache, there&#8217;re some important directories, such as document root, audit root, configuration root, and CGI-bin root. (CGI, common gateway interface, provides a protocol for web servers to execute programs).

Here&#8217;re some common admistration considerations for HTTP servers:

<img class="alignnone size-medium wp-image-213" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-24-at-7.56.48-PM-300x244.png" alt="" width="300" height="244" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-24-at-7.56.48-PM-300x244.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-24-at-7.56.48-PM.png 469w" sizes="(max-width: 300px) 100vw, 300px" /> 

HTML is the document that HTTP uses most. By definition, HTML, hyper-text markup language, is a device independent way to represents documents. It can specify the format in the document, like titles, paragraphs, colors etc. It can also include reference documents, such as images, applets etc. Form is a very important component, which translate user input into HTTP requests to the specific URI. XHTML is an standardization of HTML. It&#8217;s more restrictive and easier to parse and process. HTML5 is the new version of HTML. It provides better support for medias, like audio and video and has removed the legacy elements. Here&#8217;s a comparasion in details: [HTML vs. XHTML vs HTML5.](https://hackr.io/blog/difference-between-html-html5-xhtml) Another very important thing is **HTML** **only support GET and POST**. If method is not specified in the html, GET is by default (without javascript involved). You cannot trust any HTML, because javascript can change the behavior.

The goal of CSS (cascading style sheets) is the separation of document structure and formatting. We should use HTML for document structure and CSS for formatting. CSS can specify or override the style of elements. Ususally, it can modify the formatting of fonts, hrefs, tables, hover etc. The CSS structure is key value pairs, <name>: <value>. It can be defined in-line using &#8220;style&#8221; attribute, in the HTML header or a separate file. CSS selector is a way to aggregate style pairs for a element, class or ID.<img class="alignnone size-medium wp-image-215" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-24-at-8.33.08-PM-300x189.png" alt="" width="300" height="189" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-24-at-8.33.08-PM-300x189.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-24-at-8.33.08-PM.png 551w" sizes="(max-width: 300px) 100vw, 300px" />

<div> and <span> are tags, which do nothing except adding style to the content. The difference between them is <div> will break lines and <span> is in-line. For more details of CSS: [CSS resources.](https://www.w3schools.com/css/)

Javascript is interpreted (no need to compile) and loosely/dynamically typed. The functions in javascript are also objects, which can also have properties. It can be defined as the content in the <script> tag or a separate file. HTML can have javascript events, such as onload, <span style="font-size: 1rem;">onclick, </span><span style="color: inherit; font-size: inherit;">onfocus, onblur, onmouseover etc. Those can invoke javascript methods when they&#8217;re triggered.</span>

DOM (document object model) is a tree of nodes represent the HTML document. It contains 3 kinds of nodes: element, attribute and text. Fields can be used to retrieve related nodes, e.g. parentNode, firstChild, lastChild, childNodes, nextSibling, previousSibling. Methods can be applied to change the element, such as appendChild(), removeChild(), modifying attributes like onclick, href, style.

<img class="alignnone size-medium wp-image-216" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-24-at-8.47.34-PM-300x149.png" alt="" width="300" height="149" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-24-at-8.47.34-PM-300x149.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-24-at-8.47.34-PM.png 597w" sizes="(max-width: 300px) 100vw, 300px" /> 

The document object is a predefined javascript variable and the root of the tree. It has some useful methods and variables: getElementById(),getElementsByName(),getElementsByTagName(), URL, cookie.

## <span id="Servlets_Tomcats">Servlets & Tomcats</span>

A reason that many people love Java is that it&#8217;s such a flexiable and adaptabel language that can almost run in all environments, terminal, IDE, browsers(applet), web servers(servlets) and even electronic cards. As long as there&#8217;s JVM, Java should be able to function.

<img class="alignnone size-medium wp-image-219" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-25-at-10.34.34-PM-300x153.png" alt="" width="300" height="153" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-25-at-10.34.34-PM-300x153.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-25-at-10.34.34-PM.png 499w" sizes="(max-width: 300px) 100vw, 300px" /> 

_Java in Browsers (applets)_

<img class="alignnone wp-image-218" style="font-size: 1rem;" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-25-at-10.34.40-PM-300x185.png" alt="" width="418" height="258" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-25-at-10.34.40-PM-300x185.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-25-at-10.34.40-PM.png 498w" sizes="(max-width: 418px) 100vw, 418px" /> 

_Java in Web Servers (servlets)_

Although applets will work in some cases, people are using more servlets that applets. There&#8217;re some reasons for this.

  * Applets may lead to java version issue. It need to make sure the JVM in the browser can run the class file sent from the server.
  * Some large applications can have very large class files. It&#8217;s not effective to send such a large amount of data.
  * In terms of accessing data on the server, servlets provide efficiency and security.

In short, Tomcat is a standing by web container that handle requests and make responses. Some key packages are javax.servlet and javax.servlet.http, which is in _$CATALINA_ROOT/lib/servlet-api.jar_.

javax.servlet.Servlet is an Interface has the following methods:

<img class="alignnone wp-image-220" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-25-at-10.52.11-PM-300x165.png" alt="" width="389" height="214" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-25-at-10.52.11-PM-300x165.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-25-at-10.52.11-PM.png 592w" sizes="(max-width: 389px) 100vw, 389px" /> 

javax.servlet.GenericServlet implements the Servlet interface and makes it easier to build customized servlets over different protocols. For HTTP, tomcat has already built one based on GenericServlet for us, which is javax.servlet.http.HttpServlet (extending the GenericServlet class). Here&#8217;re some methods for your servlets (if extending HttpServlet) to override:

<img class="alignnone size-medium wp-image-221" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-25-at-11.09.23-PM-300x87.png" alt="" width="300" height="87" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-25-at-11.09.23-PM-300x87.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-25-at-11.09.23-PM.png 494w" sizes="(max-width: 300px) 100vw, 300px" /> 

javax.servlet.http.HttpServletRequest is the interface for the http requests. There&#8217;re some common methods that are good to know: **getHeaderNames(), getHeader(name), getQueryString(), getParameterNames(), getParameter(name), getCookie(), getSession()** etc.

Similarly, javax.servlet.http.HttpServletResponse is the interface for http responses. Some selected methods are: **setContentType(), getWriter(), getOutputStream(), sendError(statusCode), sendRedirect(url), addCookie(cookie)** etc.

Now, let&#8217;s talk about the structure of a web application. **WebContent** is the folder holding pretty much everything. If you put the HTML files directly under WebContent, it will be publicly accessible by default. There&#8217;re 2 folders in the WebContent, **META-INF** and **WEB-INF** (some people say INF stands for information). META-INF is a list of content related to jar files. It&#8217;s like metadata. Usually, we don&#8217;t need to touch things in this folder. WEB-INF is very important. It contains the JAR dependencies(under lib directory), class files, and a deployment descriptor file **web.xml**. Some information can be set in the web.xml as parameters. web.xml can specify the url-pattern using servlet-mapping. It can also describe the welcome page etc. It&#8217;s very important.

In terms of tomcat administration, it has a manage interface(home page), XML files in conf and WEB\_INF and $CATALINA\_HOME/logs. The logs mainly have 3 types:

  * **stdout*.log** contains System.out output
  * **manager*.log** output from Manager app
  * **catalina*.log** info on apps loaded

The web application can be easily exported by any modern IDE as a war file. The IDE can run the war file directly. But, the war file can be easily deployed to a tomcat container without IDE as well. It only need 2 steps:

  1. Copy the war to $CATALINA_HOME/webapps
  2. Run startup.sh / shutdown.sh in $CATALINA_HOME/bin

## <span id="Threads">Threads</span>

Tomcat uses multiple threads to treat threads. Each request will start a thread. 2 threads with local variables referencing same object will share the object. When dealing with threads, it&#8217;s good to think of the variable type. It could be class variables, instance variables, and local variables. When different threads are working on shared resources, race condition may happen. Common shared resourse are:

  * Instance variables (of shared instances of a class)
  * Class variables
  * <div class="page" title="Page 16">
      <div class="section">
        <div class="layoutArea">
          <div class="column">
            <p>
              OS or DB resources (files, network, database)
            </p>
          </div>
        </div>
      </div>
    </div>

To help tackle this problem, keyword _synchronized_ helps. The synchronized statement can be used on any object (or on a method declaration). Then only one thread at a time will be able to access the object, code block or method.

In tomcat, [Coyote connector](https://tomcat.apache.org/tomcat-4.1-doc/config/coyote.html) is used to manage connections, thread pool etc. A pool of threads helps save the time to instantiate the threads and garbage collect the finished threads. It pre-instantiates a pool of threads. When a requests come, it will dispatch one thread to process the request. It can be configured in **conf/server.xml**.

<img class="alignnone wp-image-223" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-26-at-8.42.56-PM-300x51.png" alt="" width="324" height="55" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-26-at-8.42.56-PM-300x51.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-26-at-8.42.56-PM.png 557w" sizes="(max-width: 324px) 100vw, 324px" /> 

When the code logic involves copying objects, we need to be more careful on the concurrency issues. We used use defensive copy: choose whether to use [shallow copy or deep copy](https://www.geeksforgeeks.org/deep-shallow-lazy-copy-java-examples/). It is not only necessary for multithreading scenarios. A not very defensive copy constantly leads to bugs in many other scenarios as well.

## <span id="Cookies_Sessions">Cookies & Sessions</span>

What&#8217;s the purpose of cookies and sessions? It can origin to a question, which is &#8220;how can the server tell which browser the request comes from?&#8221;. That was indeed an important issue. Later, people came up with the idea of cookies? Sounds sweet. But, how does it work?

Basically, the server sends a cookie(including some data) to the browser. The browser will have a bite(without understanding the data), send it back and let the server know who ate the cookie.

<img class="alignnone size-medium wp-image-226" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-26-at-9.14.50-PM-300x211.png" alt="" width="300" height="211" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-26-at-9.14.50-PM-300x211.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-26-at-9.14.50-PM.png 691w" sizes="(max-width: 300px) 100vw, 300px" /><img class="alignnone size-medium wp-image-225" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-26-at-9.14.59-PM-300x214.png" alt="" width="300" height="214" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-26-at-9.14.59-PM-300x214.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-26-at-9.14.59-PM.png 680w" sizes="(max-width: 300px) 100vw, 300px" /> 

Then, the identification problem is solved. Cookies have headers and attributes. Some common cookies attributes are:

  * Expires – Sets max lifetime of cookie (date & time)
  * Max-Age – Sets max lifetime of cookie (seconds)
  * Domain – To which hosts to send cookie back
  * Path – For which URLs to send cookie back
  * Secure – Only send cookie on secure connections
  * HttpOnly – Don’t expose cookie to scripts

There&#8217;re 3 main types of cookies:

  * <span style="font-size: 1rem;">Session Cookie – Deleted on browser close</span>
  * <span style="font-size: 1rem;">Persistent Cookie – Stored until </span>expiration <span style="font-size: 1rem;">date</span>
  * <span style="font-size: 1rem;">Third-party Cookie – Cookies from other sites</span>

Cookie is very useful. But, it also has some downsides. The data size of it has a upperbound of 4KB. It can be modified by users. It may also be rejected by the browser.

<span style="font-size: 1rem;">To inspect cookies with chrome: right click anywhere on the page => inspect => Application => Cookies.</span>

<span style="font-size: 1rem;">Lets&#8217; move on the sessions. Sessions maintain data correlated to the browser session. Cookies are usually used to implemnt sessions (session is stored in cookies). In java, the corresponding class is </span><span style="font-size: 1rem;">HttpSession.</span>

According to this [article](https://www.journaldev.com/1907/java-session-management-servlet-httpsession-url-rewriting), there&#8217;re some other ways to do the identification:

  * HTML Hidden Field – We can create a unique hidden field in the HTML and when user starts navigating, we can set its value unique to the user and keep track of the session. This method can’t be used with links because it needs the form to be submitted every time request is made from client to server with the hidden field. Also it’s not secure because we can get the hidden field value from the HTML source and use it to hack the session.
  * URL Rewriting – We can append a session identifier parameter with every request and response to keep track of the session. This is very tedious because we need to keep track of this parameter in every response and make sure it’s not clashing with other parameters.

These 2 approaches are usually less secure than sessions and cookies if not taken good care of. But, their natures provide more effectiveness and potability over the sessions and cookies in some cases.

JSP (Java Server Page)

JSP provides the HTML with logic (or you can argue it embeds logic into HTML). When the web application is executed, the JSP will literally be compiled to servlets. The <span style="font-size: 1rem;">unquoted HTML tags will become strings in println statements in the servlets. The jsp tags will just become java code. To view the code on a standalone tomcat server, it&#8217;s under the folder: </span>_&#8230;/work/Catalina/localhost/<appname>/ org/apache/jsp._

For java statements, it should be put into <span style="font-size: 1rem;"><% and %> tags. The expressions should be put into <%= and %> tags. E.g. <% i = 1 + 1%> and i=<%= 1 + 1%>. There&#8217;re some standard variables already defined for us, such as:</span>

  * HttpServletRequest **request**
  * HttpSession **session**
  * JspWriter **out** (similar to PrintWriter)
<li class="page" title="Page 13">
  <div class="section">
    <div class="layoutArea">
      <div class="column">
        <p>
          HttpServletResponse <strong>response</strong>
        </p>
      </div>
    </div>
  </div>
</li>

Besides statements and expressions, we can go further! <%! &#8230; %> can be used to define methods and inner class. We can also import packages with <%@ page import=&#8221;&#8230;&#8221; %>. Or add comments with <%&#8211; &#8230; &#8211;>.

Next, we really need some data to play with. The JSP EL(expression language) empower us to easily access(using ${}) 4 kinds of variables (in the following order):

  1. Page attribute (Used for local variables on the page)
  2. Request attribute (attributes embedded in the request passed to the page)
  3. Session attribute (attributes stored in the session)
  4. Application attribute (Used to store application-wide information: e.g., initial parameters)

The more **transient** attributes will be **checked** **earlier**. Some java equvilant code will make it easier to understand:

$(user) equivalent in java:

<pre class="brush: java; title: ; notranslate" title="">Object o = pageContext.getAttribute("user");
if(o == null) o = request.getAttribute("user");
if(o == null) o = session.getAttribute("user");
if(o == null) o = application.getAttribute("user");
</pre>

<p class="p1">
  We can also use dot to access JavaBeans&#8217; fields. For example, $(user.userName) equivalent in java:
</p>

<pre class="brush: java; title: ; notranslate" title="">Class&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;lt;?&amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;amp;gt; c = o.getClass();
Method m = c.getMethod("getUserName");
Object value = m.invoke(o);
</pre>

## <span id="SQL_JDBC"> SQL & JDBC</span> {.p1}

Database is crucial in most web applications. But, it may also introduce new issues, such as backup, security, detecting/repairing corruption, and performance. Before the first database came to alive, people relied on the file systems in terms of persistence matters. However, the performance is pretty bad and it&#8217;s quite hard to manage.

Then, relational database is invented. It&#8217;s using a **b-tree** data structure to improve query performance and allows **secondary indices**. Besides, [**TP monitor**](https://en.wikipedia.org/wiki/Teleprocessing_monitor)(transaction processing monitor) is included to tackle the problems like consistency control, backup, failure recovery, some security etc.

SQL provides CRUD(create, read, update, delete) operation abilities and some extra functions, such as JOIN, ORDER BY, GROUP BY etc. SQL sounds like a uniform language across different RDBMS. But, it does have some very small differences among them.

<img class="alignnone size-medium wp-image-229" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-28-at-3.32.42-PM-300x175.png" alt="" width="300" height="175" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-28-at-3.32.42-PM-300x175.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-28-at-3.32.42-PM.png 612w" sizes="(max-width: 300px) 100vw, 300px" /> 

Next, we&#8217;re approaching this kind of architecture. JDBC driver will handle the low-level interactions with the database. We only need to take care of higher-level operations, connection(pool), query, transaction etc.

java.sql.Connection and java.sql.Statement are two most important interfaces. For the Statement, **executeQuery** is responsible for SELECT, SHOW, DESCRIBE, etc and **executeUpdate** should be related to INSERT, DELETE, UPDATE, CREATE, DROP. For a specific example, you can refer to [Example: JDBC Good Practice](http://www.lucas-liu.com/2017/11/16/sample-jdbc-good-practice/).

There&#8217;re some tricks to consider when working with JDBC:

  * Prepared Statements: avoid bad characters, reduce chances of SQL injection and improve performance by precompiling queies.
  * Transaction: help consistency, allow rollback, and improve performance by grouping a list of operations.
  * Connection pooling: cut down the connection overhead and save some time (similar to tomcat thread pool)

## <span id="ORM_object-relational_mapping">ORM (object-relational mapping)</span>

As we know, Java is an object-oriented programming language. It&#8217;s class or object structure is very easy to map to a database schema. That&#8217;s a very good thing we should take advantage of.

There&#8217;re at least 2 kinds of conventions to create objects representing data, [POJO and JavaBean](https://www.geeksforgeeks.org/pojo-vs-java-beans/). In simple words, JavaBean is POJO with more restrictions. We use JavaBean as a component model. Then it should satisfy the following conditions ([more details](https://docstore.mik.ua/orelly/java-ent/jnut/ch06_02.htm)):

<img class="alignnone size-medium wp-image-231" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-28-at-7.35.48-PM-300x169.png" alt="" width="300" height="169" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-28-at-7.35.48-PM-300x169.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-28-at-7.35.48-PM-768x432.png 768w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-28-at-7.35.48-PM.png 776w" sizes="(max-width: 300px) 100vw, 300px" /> 

**Reflection** is the best friend of JavaBean. People usually use reflection (java.lang.Class) to find the class of a JavaBean. In practice, it can be used with DAO, form beans, JSP EL, GUI, and RPC etc.

Because JavaBean is an object. Then, it&#8217;s possible to have some problem when copying happens. To make a defensive copy of JavaBean, there&#8217;re 3 options:

  1. Make a new bean and copy all the values to it. (require DAO know all the properties of the bean)
  2. Implement Cloneable (require bean to have the function)
  3. Use reflection (preferable)

DAO (data access object) is another class to maintain the database. It&#8217;s another abstraction layer to handle all the data/bean related operations. It will make the code more reusable. It&#8217;s not necessarily restricted to RDBMS and JDBC. DAO can also store data into memory, files, NoSQL databases and any kind of data sources. It just depends on the implementation. A DAO example can be accessed here: StreamSqlRequest [blog](http://www.lucas-liu.com/2018/07/25/example-jdbc-better-practicestream-sql-request/) and [code](https://github.com/Lucas12138/StreamSqlRequest/tree/master/src/main/java/cmu/db).

Writing Java code to achieve the SQL equivalent on the JavaBeans will require a lot of work. Imagine how many fields we need to take care of. Therefore, people created the ORM tools, object-relational mapping. The ORM tool will automatically create the database table, provide at least basic CRUD functions, handle concurrency issues by supporting the transaction and have reasonable performance. Jeff has a very good and easy-to-use ORM tool: [GenericDAO](http://www.jeffeppinger.com/GenericDAO/). For production level web applications, [Hibernate](http://hibernate.org/) is the tool.

To use an ORM tool, it mandated to have JavaBeans following the restrictions mentioned before, such as no-args constructor, getter and setter, use <span style="font-size: 1rem;">camelCase java coding convention etc.</span>

## <span id="Transactions">Transactions</span>

Previously, we learned that transactions can help data consistency, rollback and improve performance in many cases. In this section, we will talk more about transactions.

The transaction system will guarantee the **ACID** properties. Here&#8217;s a brief definition for ACID:

<div class="page" title="Page 6">
  <div class="section">
    <div class="layoutArea">
      <div class="column">
        <ul>
          <li>
            Atomicity: all or none
          </li>
          <li>
            <span style="font-size: 1rem;">Consistency: </span><span style="font-size: 1rem;">if consistent before transaction, so too after</span>
          </li>
          <li>
            <span style="font-size: 1rem;">Isolation: despite concurrent execution, there exists exactly one serial ordering </span>
          </li>
          <li>
            <span style="font-size: 1rem;">Durability: </span>committed<span style="font-size: 1rem;"> transaction cannot be undone</span>
          </li>
        </ul>
        
        <div class="section">
          <div class="layoutArea">
            <div class="column">
              <div class="page" title="Page 6">
                <div class="section">
                  <div class="layoutArea">
                    <div class="column">
                      <div class="page" title="Page 6">
                        <div class="section">
                          <div class="layoutArea">
                            <p>
                              Transactions are commonly used in file systems (fsck, chkdsk, scandisk), databases, and applications built on DB.
                            </p>
                            
                            <p>
                              Using transaction with GenericDAO is very easy (pseudo):
                            </p>
                            
                            <ol>
                              <li>
                                Transaction.begin()
                              </li>
                              <li>
                                Transaction.commit()
                              </li>
                              <li>
                                finally -> if (Transaction.isActive()) Transaction.rollback()
                              </li>
                            </ol>
                            
                            <p>
                              Now, let&#8217;s see how the ACID is enforced for complex disk data structure, e.g. b-tree. Here&#8217;s the property to solution mapping:
                            </p>
                            
                            <ul>
                              <li>
                                Atomicity: write-ahead logging
                              </li>
                              <li>
                                <span style="font-size: 1rem;">Consistency: depends on the </span>application<span style="font-size: 1rem;"> </span>
                              </li>
                              <li>
                                <span style="font-size: 1rem;">Isolation: two-phase locking </span>
                              </li>
                              <li>
                                <span style="font-size: 1rem;">Durability: write-ahead logging</span>
                              </li>
                            </ul>
                            
                            <div class="section">
                              <div class="layoutArea">
                                <div class="column">
                                  <div class="page" title="Page 19">
                                    <div class="section">
                                      <div class="layoutArea">
                                        <div class="column">
                                          <p>
                                            <strong>Write-ahead logging</strong> provides atomicity and durability. It buffers disk pages in a memory buffer cache. Log all the changes of DB to disk before the changes are written:
                                          </p>
                                          
                                          <p>
                                            1> <span style="font-size: 1rem;">When changing data pages</span>, queue<span style="font-size: 1rem;"> (to log) records that describe changes 2> </span><span style="font-size: 1rem;">When committing, queue “commit-record” into </span>log<span style="font-size: 1rem;">, flush log (to disk) 3> </span><span style="font-size: 1rem;">Before writing out cached DB pages, ensure relevant log records flushed</span>
                                          </p>
                                          
                                          <div class="page" title="Page 20">
                                            <div class="section">
                                              <div class="layoutArea">
                                                <div class="column">
                                                  <p>
                                                    To recover, when restarting after a failure, scan the log, redo the transactions with commit logs(case1) or undo the transactions without commit logs(case2). When handling a normal rollback, scan the logs and undo the related work(case3).
                                                  </p>
                                                  
                                                  <p>
                                                    In terms of logs, the first 2 very important  kinds: value logging(e.g. v1 = 10) and operation logging(e.g. add 1 to v1). A visualization is as follows:
                                                  </p>
                                                  
                                                  <p>
                                                    <img class="alignnone size-medium wp-image-238" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-10.33.04-PM-300x214.png" alt="" width="300" height="214" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-10.33.04-PM-300x214.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-10.33.04-PM.png 636w" sizes="(max-width: 300px) 100vw, 300px" /><img class="alignnone size-medium wp-image-237" style="font-size: 1rem;" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-10.33.12-PM-300x208.png" alt="" width="300" height="208" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-10.33.12-PM-300x208.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-10.33.12-PM.png 639w" sizes="(max-width: 300px) 100vw, 300px" /><img class="alignnone size-medium wp-image-236" style="font-size: 1rem;" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-10.33.21-PM-300x209.png" alt="" width="300" height="209" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-10.33.21-PM-300x209.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-10.33.21-PM.png 629w" sizes="(max-width: 300px) 100vw, 300px" /><img class="alignnone size-medium wp-image-235" style="font-size: 1rem;" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-10.33.30-PM-300x212.png" alt="" width="300" height="212" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-10.33.30-PM-300x212.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-10.33.30-PM.png 632w" sizes="(max-width: 300px) 100vw, 300px" /><img class="alignnone size-medium wp-image-234" style="font-size: 1rem;" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-10.33.39-PM-300x214.png" alt="" width="300" height="214" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-10.33.39-PM-300x214.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-10.33.39-PM.png 635w" sizes="(max-width: 300px) 100vw, 300px" /><img class="alignnone size-medium wp-image-233" style="font-size: 1rem;" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-10.33.50-PM-300x216.png" alt="" width="300" height="216" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-10.33.50-PM-300x216.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-10.33.50-PM.png 643w" sizes="(max-width: 300px) 100vw, 300px" />
                                                  </p>
                                                  
                                                  <p>
                                                    Except for the value logs and operation logs, there&#8217;re rollback logs, page-flush logs, and checkpoint logs. Those&#8217;re also very critical. Because when we want to recover the system, we don&#8217;t want to go through all the logs. That&#8217;s when those logs come to help.
                                                  </p>
                                                  
                                                  <p>
                                                    As for locking, there&#8217;re exclusive locks(e.g. mutex lock and semaphores) and shared/exclusive locks(read/write locks). So, what&#8217;s <strong>two-phase locking</strong>? Phase 1: grab locks. Phase 2: drop locks. You are not allowed to get any new locks after dropping the locks. To execute rollback, you have to hold locks. Usually, all locks are held until the commit or rollback has completed.
                                                  </p>
                                                  
                                                  <p>
                                                    Disasters do happen. We can use the following ways to solve or reduce the influence of disasters.
                                                  </p>
                                                  
                                                  <ul>
                                                    <li>
                                                      Power failure: write-ahead logging
                                                    </li>
                                                    <li>
                                                      Data disk failure: backup tapes & log (or mirror)
                                                    </li>
                                                    <li>
                                                      Log disk failure: mirror the log
                                                    </li>
                                                    <li>
                                                      Machine room failure: mirror the log elsewhere
                                                    </li>
                                                  </ul>
                                                </div>
                                                
                                                <p>
                                                  The transaction system doesn&#8217;t only apply to RDBMalsot aslo work for NoSQL although the data models may be very different.
                                                </p>
                                                
                                                <h2>
                                                  <span id="MVC_model_view_controller">MVC (model view controller)</span>
                                                </h2>
                                                
                                                <p>
                                                  Based on our experience, it&#8217;s workable to handle request with JSP only. But, it&#8217;s really not very elegant. It&#8217;s pretty awkward when the application is large. Errors are also hard to handle. It requires a lot of initialization and instantiation. A much better way to always avoid using JSP to handle request from users directly. We should only use JSP as a view and use servlets to handle the request and forward to JSP. The very important interface here is RequestDispatcher, which will forward to request. Generally, servlet environment is a better place to handle security, validation of inputs, invocation of business logic. And JSP environment is a better place to handle formatting.
                                                </p>
                                                
                                                <p>
                                                  <img class="alignnone size-medium wp-image-239" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-11.08.49-PM-300x197.png" alt="" width="300" height="197" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-11.08.49-PM-300x197.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-11.08.49-PM.png 544w" sizes="(max-width: 300px) 100vw, 300px" />
                                                </p>
                                                
                                                <p>
                                                  This is how MVC looks like.
                                                </p>
                                                
                                                <p>
                                                  The Controller.java will:
                                                </p>
                                                
                                                <ul>
                                                  <li>
                                                    Handles security checking in one place
                                                  </li>
                                                  <li>
                                                    Initializes application in one place
                                                  </li>
                                                  <li>
                                                    Handles routing of requests in one place
                                                  </li>
                                                </ul>
                                                
                                                <p>
                                                  The Controller.java will contain serval actions(Action.java is an abstract class). Action.java allows consistently invocate business logic by using a hashmap. Concrete action classes usually map to different JSP view. A good example will be discussed later (HW5 reflection).
                                                </p>
                                                
                                                <p>
                                                  Model refers to database related classes. Usually, there will be many DAOs. Therefore, it&#8217;s good to have a Model.java to handle all the initialization and aggregates the DAOs.
                                                </p>
                                                
                                                <p>
                                                  JSP will look at the request attributes or session attributes etc. forwarded to it. Passing JavaBeans is very convenient. It very easy to use. And the JSP EL will make it even easier to access the JavaBean&#8217;s fields.
                                                </p>
                                                
                                                <p>
                                                  MVC leads to SoC(<strong>Separate of Concern</strong>), which introduces modularity. Model handles database, view deals with UI and controller routes to different actions. SoC also makes it easier to build a large application with many teammates. Different people can focus on different parts that they&#8217;re familiar with.
                                                </p>
                                                
                                                <h2>
                                                  <span id="Tag_Libraries">Tag Libraries</span>
                                                </h2>
                                                
                                                <p>
                                                  As we discussed previously, servlets should not do anything related to view formatting and JSP should perform no business logic. It&#8217;s easy to servlets to achieve. But, how can JSP contain no Java code? If you have some experience working with JSP, you will notice that if you add some conditions or loops into the JSP, it will look very ugly and hard to read. Therefore, it&#8217;s difficult to debug when there&#8217;re some mistakes. As a matter of fact, a kind of tools can make it a lot easier for us to have conditions and loops etc. without Java code in JSP. That is the tag library.
                                                </p>
                                                
                                                <p>
                                                  There&#8217;re many tag libraries, such as <strong>Jakarta Taglibs</strong>, <strong>JSTL</strong>(JSP Standard Tag Library) etc. After 2 pre-requests are met, JSTL(core) will be ready to go.
                                                </p>
                                                
                                                <div class="page" title="Page 15">
                                                  <div class="section">
                                                    <div class="layoutArea">
                                                      <div class="column">
                                                        <ul>
                                                          <li>
                                                            install jstl.jar and standard.jar in WEB-INF/lib
                                                          </li>
                                                          <li>
                                                            declare use in top of .jsp file
                                                          </li>
                                                        </ul>
                                                        
                                                        <p>
                                                          For JSTL core tags, it can achieve conditions with &#8220;if&#8221;, &#8220;choose&#8221;, &#8220;when&#8221; tags. It can also achieve loops with &#8220;forEach&#8221; and &#8220;forTokens&#8221;. &#8220;forEach&#8221; will be able to loop on an array or java.util.Collection. It has a EL similar to JSP EL. But, JSTL EL also has a keyword &#8220;empty&#8221; to test null or empty string.
                                                        </p>
                                                        
                                                        <p>
                                                          Some good examples can be found <a href="https://www.javatpoint.com/jstl">here</a> and <a href="https://www.tutorialspoint.com/jsp/jsp_standard_tag_library.htm">here</a>.
                                                        </p>
                                                        
                                                        <p>
                                                          Except for the core tags, it also has some other tags for some complemental functionalities, such as format tags, function tags etc.
                                                        </p>
                                                        
                                                        <h2>
                                                          <span id="AJAX_asynchronous_javascript_and_XML">AJAX (asynchronous javascript and XML)</span>
                                                        </h2>
                                                        
                                                        <p>
                                                          AJAX is a technique for creating more interactive web applications.
                                                        </p>
                                                        
                                                        <div class="section">
                                                          <div class="layoutArea">
                                                            <div class="column">
                                                              <ul>
                                                                <li>
                                                                  Use an XMLHttpRequest object to make requests to the web server for data asynchronously (or synchronously)
                                                                </li>
                                                                <li>
                                                                  <span style="font-size: 1rem;">Receive server data as XML (or text or JSON)</span>
                                                                </li>
                                                                <li>
                                                                  <span style="font-size: 1rem;">Convert the XML into a DOM tree </span>
                                                                </li>
                                                                <li>
                                                                  <span style="font-size: 1rem;">Extract data from the XML DOM tree and change the HTML document’s DOM tree (thereby updating the page)</span>
                                                                </li>
                                                              </ul>
                                                              
                                                              <p>
                                                                It has benefits like enabling more interactive websites(page won&#8217;t be reloaded, requests can be asynchronous), and reduction on the server&#8217;s load.
                                                              </p>
                                                              
                                                              <p>
                                                                For more information about XMLHttpRequest:
                                                              </p>
                                                              
                                                              <p>
                                                                <img class="alignnone size-medium wp-image-241" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-30-at-9.44.15-AM-300x176.png" alt="" width="300" height="176" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-30-at-9.44.15-AM-300x176.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-30-at-9.44.15-AM.png 618w" sizes="(max-width: 300px) 100vw, 300px" />
                                                              </p>
                                                              
                                                              <p>
                                                                XMLHttpRequest can be sent asynchronously and when the state of the request changes, your JavaScript method is called. The request can be query string, post data or anything else. The response can be in the format of XML, JSON, chunks of HTML or anything.
                                                              </p>
                                                              
                                                              <p>
                                                                We can implement the javascript program by ourselves. But, there&#8217;re some libraries already for us to simplfy the process, e.g. jQuery. jQuery provides functions of DOM manipulation, such as element selection, traversal, and manipulation. It also supports event, AJAX. It has some other utilites and plug-ins too. Here&#8217;s a <a href="https://www.w3schools.com/jquery/">quick start</a> on jQuery.
                                                              </p>
                                                              
                                                              <p>
                                                                HTTP protocol has the following characteristics.
                                                              </p>
                                                              
                                                              <p>
                                                                <img class="alignnone size-medium wp-image-242" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-30-at-9.58.37-AM-300x124.png" alt="" width="300" height="124" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-30-at-9.58.37-AM-300x124.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-30-at-9.58.37-AM.png 497w" sizes="(max-width: 300px) 100vw, 300px" />
                                                              </p>
                                                              
                                                              <p>
                                                                AJAX does have some limitation when the clients need to poll the server very frequently. <a href="https://en.wikipedia.org/wiki/WebSocket">WebSocket</a> another protocol can be very helpful in that case. HTTP&#8217;s headers are usually around the size of 700 bytes. However, WebSocket&#8217;s header&#8217;s only around 3 bytes. This saves a lot of the network cost and provides efficiency. Google Doc and Multiplayer game are good <a href="https://www.infoworld.com/article/2609720/application-development/9-killer-uses-for-websockets.html">examples</a> where WebSocket can be applied.
                                                              </p>
                                                              
                                                              <p>
                                                                This is the characteristics of WebSocket.
                                                              </p>
                                                              
                                                              <p>
                                                                <img class="alignnone size-medium wp-image-243" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-30-at-10.10.10-AM-300x141.png" alt="" width="300" height="141" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-30-at-10.10.10-AM-300x141.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-30-at-10.10.10-AM.png 523w" sizes="(max-width: 300px) 100vw, 300px" />
                                                              </p>
                                                              
                                                              <p>
                                                                It can be easily setup by:
                                                              </p>
                                                              
                                                              <p>
                                                                <img class="alignnone size-medium wp-image-244" src="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-30-at-10.11.37-AM-300x177.png" alt="" width="300" height="177" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-30-at-10.11.37-AM-300x177.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-30-at-10.11.37-AM.png 513w" sizes="(max-width: 300px) 100vw, 300px" />
                                                              </p>
                                                              
                                                              <p>
                                                                Java and tomcat also support the WebSocket. javax.websocket should be the place to look into. It has a sevlet using HandshakeResponse to switch from HTTP to WebSocket.
                                                              </p>
                                                              
                                                              <h2>
                                                                <span id="Security">Security</span>
                                                              </h2>
                                                              
                                                              <p>
                                                                This is one of the most important topics related to web application. Without considering security issues, the web application will be so vulnerable that hackers can easily break in or bring the whole service down.
                                                              </p>
                                                              
                                                              <p>
                                                                Apparently attacking the physical servers is possible, but we won&#8217;t talk too much about that here. Let&#8217;s assume the underlying network is secure first.
                                                              </p>
                                                              
                                                              <p>
                                                                How complex the password do you allow your users to have? If the bad guy can guess the password, they break the application. Two-factor authentication or <a href="https://en.wikipedia.org/wiki/Multi-factor_authentication">multi-factor authentication</a> will help in this case. With some extra information, such as something they know, something they have, or something they are, we can validate the identity of the user.
                                                              </p>
                                                              
                                                              <p>
                                                                SQL injection is another common attack. This kind of attack is basically adding extra SQL query as user input. If the backend implementation is not using prepared statement or taking into this kind of case into account. The SQL injection will be possible. Then anything SQL can do the hacker can do. Here&#8217;s an <a href="https://www.incapsula.com/web-application-security/sql-injection.html">example</a>.
                                                              </p>
                                                              
                                                              <p>
                                                                Cross-site scripting (<a href="https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)">XSS</a>) is embedding scripts into input. This may happen if it&#8217;s possible the input willl be saved to database or passed on to other users. Checking if the user input contains HTML tags can be a solution here. The 2 specific options are either rejecting the input or sanitize the input.
                                                              </p>
                                                              
                                                              <p>
                                                                Cross-site request forgery (CSRF), a web page from a Site A can trick a user into submitting a request to another Site B (The user might already be logged in to Site B).
                                                              </p>
                                                              
                                                              <p>
                                                                <img class="alignnone size-medium wp-image-246" src="http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.19.18-PM-300x130.png" alt="" width="300" height="130" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.19.18-PM-300x130.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.19.18-PM.png 549w" sizes="(max-width: 300px) 100vw, 300px" />
                                                              </p>
                                                              
                                                              <p>
                                                                <img class="alignnone size-medium wp-image-247" src="http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.19.51-PM-300x149.png" alt="" width="300" height="149" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.19.51-PM-300x149.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.19.51-PM.png 618w" sizes="(max-width: 300px) 100vw, 300px" />
                                                              </p>
                                                              
                                                              <p>
                                                                Now, let&#8217;s remove the assumption (secure network). If the network can be attacked, what can the attacks be? There&#8217;re some common attacks, such as man-in-the-middle attack, sniffing and spoofing. They&#8217;re described as follows.
                                                              </p>
                                                              
                                                              <p>
                                                                <img class="alignnone size-medium wp-image-248" src="http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.24.40-PM-300x213.png" alt="" width="300" height="213" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.24.40-PM-300x213.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.24.40-PM.png 634w" sizes="(max-width: 300px) 100vw, 300px" />
                                                              </p>
                                                              
                                                              <p>
                                                                <img class="alignnone size-medium wp-image-249" src="http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.24.58-PM-300x167.png" alt="" width="300" height="167" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.24.58-PM-300x167.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.24.58-PM.png 664w" sizes="(max-width: 300px) 100vw, 300px" />
                                                              </p>
                                                              
                                                              <p>
                                                                <img class="alignnone size-medium wp-image-250" src="http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.25.14-PM-300x202.png" alt="" width="300" height="202" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.25.14-PM-300x202.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.25.14-PM.png 657w" sizes="(max-width: 300px) 100vw, 300px" />
                                                              </p>
                                                              
                                                              <p>
                                                                Before we move on the solutions, let&#8217;s make it clear about the 3 words, authentication, authorization and privacy.
                                                              </p>
                                                              
                                                              <p>
                                                                <img class="alignnone size-medium wp-image-251" src="http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.30.28-PM-300x180.png" alt="" width="300" height="180" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.30.28-PM-300x180.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.30.28-PM.png 754w" sizes="(max-width: 300px) 100vw, 300px" />
                                                              </p>
                                                              
                                                              <p>
                                                                Therefore, the corresponding solutions are:
                                                              </p>
                                                              
                                                              <ul class="ul1">
                                                                <li class="li1">
                                                                  Sniffing: privacy
                                                                </li>
                                                                <li class="li1">
                                                                  Spoofing: authentication
                                                                </li>
                                                                <li class="li1">
                                                                  Man-in-the-middle: authentication and privacy
                                                                </li>
                                                              </ul>
                                                              
                                                              <p>
                                                                In terms of authentication, there&#8217;re 3 common approaches.
                                                              </p>
                                                              
                                                              <p>
                                                                <img class="alignnone size-medium wp-image-252" src="http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.33.35-PM-300x112.png" alt="" width="300" height="112" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.33.35-PM-300x112.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.33.35-PM.png 612w" sizes="(max-width: 300px) 100vw, 300px" />
                                                              </p>
                                                              
                                                              <p>
                                                                But, there&#8217;s another way to provide both authentication and privacy, <strong>SSL (Secure Sockets Layer)</strong>. SSL is a layer on top of TCP and a security model based on strong encryption techniques. Some related crypto topics, such as one-way Hashing, symmetric key encryption, asymmetric key encryption and certificate authority etc. are good to know.
                                                              </p>
                                                              
                                                              <p>
                                                                Those crypto topics are also covered in another course, 95702 distributed systems. It&#8217;s more in-depth there. So, for here, let&#8217;s think about 4 simple scenarios.
                                                              </p>
                                                              
                                                              <ol>
                                                                <li>
                                                                  Use a symmetric secret key, like WWII and <strong>TEA</strong> cases. This is normally faster than asymmetric approach but less reliable and secure.
                                                                </li>
                                                                <li>
                                                                  Use ticket/certificate, like <strong>Kerberos</strong>. This requires a 3rd party to manage the certificates for clients and servers. But, it will be secure and efficient. The con is the 3rd party will be a single point of failure.
                                                                </li>
                                                                <li>
                                                                  Use digital signature(hash digest) plus asymmetric keys. This is secure without a third party but not very efficient.
                                                                </li>
                                                                <li>
                                                                  Add symmetric secret keys to scenario 3 once the connection is established, like <strong>SSL</strong>. Another important thing is that the server&#8217;s public key has to be signed by a trusted 3rd party. In other words, we have to authenticate the servers. This is the most widely used approach. It provides both security and efficiency. Here&#8217;s how SSL hand shake looks like.
                                                                </li>
                                                              </ol>
                                                              
                                                              <p>
                                                                <img class="alignnone size-medium wp-image-253" src="http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.53.30-PM-300x203.png" alt="" width="300" height="203" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.53.30-PM-300x203.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.53.30-PM.png 669w" sizes="(max-width: 300px) 100vw, 300px" />
                                                              </p>
                                                              
                                                              <p>
                                                                <img class="alignnone size-medium wp-image-254" src="http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.54.18-PM-300x210.png" alt="" width="300" height="210" srcset="http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.54.18-PM-300x210.png 300w, http://www.lucas-liu.com/wp-content/uploads/2018/11/Screen-Shot-2018-11-04-at-7.54.18-PM.png 751w" sizes="(max-width: 300px) 100vw, 300px" />
                                                              </p>
                                                              
                                                              <p>
                                                                Now SSL has been upgraded to <a href="https://en.wikipedia.org/wiki/Transport_Layer_Security"><strong>TLS</strong></a>(Transport Layer Security ). The concepts didn&#8217;t change much though. TLS provides server authentication, client authentication(optional) and private communication, too. Here&#8217;s a little summary on SSL.
                                                              </p>
                                                              
                                                              <p class="p1">
                                                                SSL provides:
                                                              </p>
                                                              
                                                              <p class="p1">
                                                                => server authentication (<b>always</b>)
                                                              </p>
                                                              
                                                              <p class="p1">
                                                                => client authentication (<b>sometimes</b>, need client certificate)
                                                              </p>
                                                              
                                                              <p class="p1">
                                                                => <b>never</b> authorization
                                                              </p>
                                                              
                                                              <p class="p1">
                                                                => private communication (<b>always</b>, the communication can be seen but hard to decrypted)
                                                              </p>
                                                              
                                                              <p class="p1">
                                                                => secret communication (<b>never</b>, because the SSL communication will always be seen; VPN provides secret communication)
                                                              </p>
                                                              
                                                              <h2>
                                                                <span id="Cloud">Cloud</span>
                                                              </h2>
                                                              
                                                              <p>
                                                                How can we talk about web application without talking about cloud deployment?! Yeah, the main focus of this course is not about the cloud, unfortunately. Deploying java web application to the cloud is actually very easy. You can use IaaS and make the dependencies on your own with either instance or docker containers. Or you can use PaaS, where you don&#8217;t even need to worry a lot about the dependencies.
                                                              </p>
                                                              
                                                              <p>
                                                                This section will be a short brief history about the cloud. Maybe next year, I will make a post about the cloud only and in details.
                                                              </p>
                                                              
                                                              <p>
                                                                The cloud is a really hot topic recently. But back in the 1960&#8217;s, Standford&#8217;s professor John McCarthy predicted, &#8220;computation &#8230; organized as a public utility&#8221;. That&#8217;s is pretty much the idea of cloud! The 1960&#8217;s is the era of mainframe computers. It&#8217;s not common for ordinary people to own a computer. The 1980&#8217;s, the time of personal computing arrived. More people were able to have a computer but still not a lot. The 2000&#8217;s the when the cloud&#8217;s era began. This is based on the evolution of technology that can manage clusters of machines and the development of web servers. AWS, Azure, and GCP are the 3 main players now in the market. I believe there&#8217;re many other players planning to take a fair share, such as Alibaba, Salesforce, Oracle, Tencent, SAP etc.
                                                              </p>
                                                            </div>
                                                            
                                                            <h1>
                                                              <span id="Practice">Practice</span>
                                                            </h1>
                                                            
                                                            <p>
                                                              &#8220;Talk is cheap&#8221;, some hands-on practice will definitely help us learn more. Check out this <a href="https://github.com/Lucas12138/JavaEE-Web-Application">link</a> to see more. It has contained descriptions, diagrams, and code. Therefore, I won&#8217;t put the unnecessary duplicates here. Finally, what a great course! A big hand for Professor Jeff!
                                                            </p>
                                                          </div>
                                                        </div>
                                                      </div>
                                                    </div>
                                                  </div>
                                                </div>
                                              </div>
                                            </div>
                                          </div>
                                        </div>
                                      </div>
                                    </div>
                                  </div>
                                </div>
                              </div>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>