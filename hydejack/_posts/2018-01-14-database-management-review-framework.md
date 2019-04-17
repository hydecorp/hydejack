---
id: 177
title: 'Database Management: Review Framework'
date: 2018-01-14T07:04:25+00:00
author: Lucas
layout: post
guid: http://www.lucas-liu.com/?p=177
permalink: /2018/01/14/database-management-review-framework/
categories:
  - Database
---
The main reason for doing this framework is that knowledge points are consistently forgotten if we don&#8217;t use them. So, I want to wrap it up in a concise way.

<div id="toc_container" class="no_bullets">
  <p class="toc_title">
    Contents
  </p>
  
  <ul class="toc_list">
    <li>
      <a href="#Relational_Model"><span class="toc_number toc_depth_1">1</span> Relational Model</a>
    </li>
    <li>
      <a href="#Entity-Relationship_Modeling"><span class="toc_number toc_depth_1">2</span> Entity-Relationship Modeling</a>
    </li>
    <li>
      <a href="#Normalization"><span class="toc_number toc_depth_1">3</span> Normalization</a>
    </li>
    <li>
      <a href="#Relational_Algebra"><span class="toc_number toc_depth_1">4</span> Relational Algebra</a>
    </li>
    <li>
      <a href="#SQL"><span class="toc_number toc_depth_1">5</span> SQL</a>
    </li>
  </ul>
</div>

# <span id="Relational_Model">Relational Model</span>

First of all, some critical terminologies are as follows.

**Relational Database**: a collection of relations

**Relation**: a set of tuples

**Tuple**: a collection of attributes&#8217; values

**Attribute**: a characteristic of a tuple in a relation

**Domain**: a set of acceptable values of an attribute

**Degree**: number of attributes in a relation

**Cardinality**: number of tuples in a relation

In terms of data integrity, relational keys are introduced.

Those are **Superkey**, **Candidate Key**, **Primary** **Key**, **Foreign** **Key**.

In short,  superkey is an attribute or a set of attributes that can identify each tuple uniquely. Candidate key can be viewed as a subset of superkey, which has no subset that can identify each tuple uniquely. Primary key is a candidate key that is selected to identify the tuples. Foreign key matches candidate key of another relation.

# <span id="Entity-Relationship_Modeling">Entity-Relationship Modeling</span>

While developing a database model, we need to translate the business rules into **conceptual** model first. Then, we can design **logical** model based on the conceptual model. Finally, we will develop the **physical** model. The differences between those three are shown in the table below.

<img class="alignnone size-medium wp-image-178" src="{{site.baseurl}}/wp-content/uploads/2018/01/Screen-Shot-2018-01-14-at-4.31.26-PM-300x204.png" alt="" width="300" height="204" srcset="{{site.baseurl}}/wp-content/uploads/2018/01/Screen-Shot-2018-01-14-at-4.31.26-PM-300x204.png 300w, {{site.baseurl}}/wp-content/uploads/2018/01/Screen-Shot-2018-01-14-at-4.31.26-PM.png 397w" sizes="(max-width: 300px) 100vw, 300px" /> 

Here are some tips related to **ER diagram**:

  * While developing the logical model, FK and attributes on the relationship should be included in the M side entity if the relationship is 1: M (one-to-many).
  * Relationship **participation** includes **optional** and **mandatory**.
  * Many-to-many relationships should be converted to **composite entities**.
  * Relationships can be **binary**, **N-ary** or even **recursive**.
  * Solution for multivalued attributes: creating new attributes or a new entity

In extended ER model, **specialization**, **generalization**, **categorization** and **aggregation** are covered.

**Data Dictionary:** data that describes the data. It is a table that includes table name, attribute name, description, data type, constraint, PK/FK, FK referenced table as columns.

**User-to-Entity matrix** basically shows what a specific user can do with different entities.

# <span id="Normalization">Normalization</span>

**Functional Dependency** is a constraint between two sets of attributes in a relation.

**UNF** has repeating groups.

**1NF** has no repeating groups.

**2NF** has no partial dependencies.

**3NF** has no transitive dependencies on PK.

**BCNF** has no non-CK dependencies.

**4NF** has no multivalued dependencies.

Notice: higher level normal forms satisfied the conditions of lower level normal forms.

**Dependency diagram** and **decomposition diagram** are included in this area.

**Lossless-join decomposition** is normally expected. If R is decomposed into  R1 and R2, and R1 intersect R2 is a superkey of R1 or R2, we can say that this is a lossless-join decomposition.

# <span id="Relational_Algebra">Relational Algebra</span>

<div class="page" title="Page 2">
  <div class="section">
    <div class="layoutArea">
      <div class="column">
        <p>
          Some important ones are as follows:
        </p>
        
        <ul>
          <li>
            Selection
          </li>
          <li>
            Projection
          </li>
          <li>
            Union
          </li>
          <li>
            Intersection
          </li>
          <li>
            Set difference
          </li>
          <li>
            Cartesian product
          </li>
          <li>
            Renaming relations
          </li>
          <li>
            Theta-join
          </li>
          <li>
            Natural join
          </li>
          <li>
            Outer join
          </li>
          <li>
            Semi-join
          </li>
          <li>
            Division
          </li>
        </ul>
        
        <p>
          <img class="alignnone size-medium wp-image-180" style="font-size: 1rem;" src="{{site.baseurl}}/wp-content/uploads/2018/01/Screen-Shot-2018-01-14-at-5.20.21-PM-300x182.png" alt="" width="300" height="182" srcset="{{site.baseurl}}/wp-content/uploads/2018/01/Screen-Shot-2018-01-14-at-5.20.21-PM-300x182.png 300w, {{site.baseurl}}/wp-content/uploads/2018/01/Screen-Shot-2018-01-14-at-5.20.21-PM.png 449w" sizes="(max-width: 300px) 100vw, 300px" /><img class="alignnone size-medium wp-image-179" src="{{site.baseurl}}/wp-content/uploads/2018/01/Screen-Shot-2018-01-14-at-5.20.32-PM-300x167.png" alt="" width="300" height="167" srcset="{{site.baseurl}}/wp-content/uploads/2018/01/Screen-Shot-2018-01-14-at-5.20.32-PM-300x167.png 300w, {{site.baseurl}}/wp-content/uploads/2018/01/Screen-Shot-2018-01-14-at-5.20.32-PM.png 467w" sizes="(max-width: 300px) 100vw, 300px" />
        </p>
        
        <h1>
          <span id="SQL">SQL</span>
        </h1>
        
        <p>
          SQL can actually be divided into some categories.
        </p>
        
        <ul>
          <li>
            Data Definition Language (DDL): <em style="font-size: 1rem;">CREATE, ALTER, DROP, RENAME</em>
          </li>
          <li>
            Data Manipulation Language (DML): <em>INSERT, UPDATE, DELETE, TRUNCATE, MERGE</em>
          </li>
          <li>
            Transection Control (TC): <em>COMMIT, ROLLBACK, SAVEPOINT</em>
          </li>
          <li>
            Data Retrieval: <em>SELECT</em>
          </li>
          <li>
            Data Control Language (DCL): <em>GRANT, REVOKE</em>
          </li>
        </ul>
        
        <p>
          Besides, a very common simple SQL SELECT template is shown below.
        </p>
        
        <pre class="brush: sql; title: ; notranslate" title="">

SELECT column(s), group_function(col.)

FROM table(s)

WHERE row_condition

GROUP BY column(s)

HAVING group_condition

ORDER BY column(s);

</pre>
      </div>
    </div>
  </div>
</div>