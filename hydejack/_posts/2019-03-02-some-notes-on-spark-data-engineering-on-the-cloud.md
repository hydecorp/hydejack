---
id: 263
title: 'Some Notes on Spark &#8211; Data Engineering on the Cloud'
date: 2019-03-02T21:47:51+00:00
author: Lucas
layout: post
guid: http://www.lucas-liu.com/?p=263
permalink: /2019/03/02/some-notes-on-spark-data-engineering-on-the-cloud/
categories:
  - Cloud
---
The last time when I was using Spark was 1 year ago. I used that for a CMU cloud computing project. Although it has an interesting scenario, I didn&#8217;t get a chance to dive deeper into it. Currently, I picked it up again for a CMU advanced cloud computing project. This time, I would like to note down some interesting things that I spotted.

# 1. The scenario

For the ACC Spark project, it&#8217;s doing ETL on some large English files. The file is in WET format and around **170MB**. We&#8217;re required to clean the data based on some specific rules. The instance we&#8217;re using is AWS EC2 m4.xlarge. The first part focused on correctness. It contains 2 tasks, which let us cleaning 1 file(using 4 slaves) and 50 files(using 8 slaves) respectively. In the second part, we&#8217;re aiming at improving the performance of the ETL. We need to clean **1 file(sanity check, test A)**, **100 files(using 8 slaves, test B)**, **400 files (using 8 slaves, test C)**, **400 files(using 16 slaves, test D)**. The ETL results will be some files on the master node, such as statistics, frequencies etc. and processed corpus files on HDFS.

# 2. Performance tips

  1. Simplify the logic. It&#8217;s simple to implement but hard to identify the bad workflows
  2. Reduce the narrow dependencies and wide dependencies, especially wide dependencies. In other words, decrease the transformation steps. Wide dependencies are more costly. Because it requires information from all partitions
  3. Use the least number of actions, e.g. collect, count. Spark is lazy. The transformation won&#8217;t really happen until there&#8217;s an action. More actions usually require more time to finish the tasks
  4.  Make good use of repartition. Repartition distributes the work to all the nodes. That&#8217;s one of the main reason why Spark can be faster than sequential programs. Usually, using 2-4 partitions per core is a good practice. However, calling repartition many times may introduce some network I/O cost. It&#8217;s good to have reasonable times of repartition. &#8220;spark.default.parallelism&#8221; is an important property for partitioning in Spark.
  5. Persist or cache some RDDs generated in the middle of the processes. Spark is for iterative map-reduce. It&#8217;s highly possible that there will be some generated RDDs can be used for the latter process. It may save 10x time comparing to a solution that not persisting them. Note that the persist term in Spark may not actually persist it on disk. The default persistence level is in memory. But, it&#8217;s tunable. It could be on disk or partially on disk. It&#8217;s important to choose the persist level wisely. Only use memory may kill the slaves. Then it has to recompute some information. It may cost a large amount of time. If the memory is limited, persisting it on disk can be effective too.

# 3. Workflow diagram

<img class="wp-image-268 alignnone" src="{{site.baseurl}}/wp-content/uploads/2019/03/acc-spark-etl-workflow-300x249.png" alt="" width="478" height="397" srcset="{{site.baseurl}}/wp-content/uploads/2019/03/acc-spark-etl-workflow-300x249.png 300w, {{site.baseurl}}/wp-content/uploads/2019/03/acc-spark-etl-workflow-768x638.png 768w, {{site.baseurl}}/wp-content/uploads/2019/03/acc-spark-etl-workflow.png 930w" sizes="(max-width: 478px) 100vw, 478px" /> 

Based on the ETL requirements and the performance tips, the ETL application was split into 4 jobs. They&#8217;re mapping to the **count**, **collectAsMap**, **collect**, **saveAsTextFile** actions respectively.

Before I arrived at this solution, I attempted collecting a very large RDD only once to reduce the number of collections. However, it led to memory issues. Besides, that approach required to do all the logic inside the master node. It&#8217;s not efficient as well. The time spent is not only related to the number of actions but also the size of data collected and how much of the work is handled in parallel.

Persist method was quite handy. We can avoid calculating same RDD multiple times and that would save us a lot of time. Clearly, in the diagram, we have 2 RDDs are used more than once. Therefore, we can persist them to speed up the process.

# 4. Project outcome

The solution mentioned above achieved very good performance. The performance targets for test case B, C, D are **25min, 80min, 45min**. My spark application finished them in **12min, 43min, 24min**. Its performance for test case C ranked #1 among 110 students.