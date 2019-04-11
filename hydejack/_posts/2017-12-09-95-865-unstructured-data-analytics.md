---
id: 97
title: 95-865 Unstructured Data Analytics
date: 2017-12-09T15:45:35+00:00
author: Lucas
layout: post
guid: http://www.lucas-liu.com/?p=97
permalink: /2017/12/09/95-865-unstructured-data-analytics/
categories:
  - Data Analytics
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
      <a href="#Exploratory_Data_Analysis"><span class="toc_number toc_depth_1">2</span> Exploratory Data Analysis</a><ul>
        <li>
          <a href="#Basic_Text_Analysis"><span class="toc_number toc_depth_2">2.1</span> Basic Text Analysis</a>
        </li>
        <li>
          <a href="#Feature_Vector_Co-Occurrence_Analysis_Correlation_Causation"><span class="toc_number toc_depth_2">2.2</span> Feature Vector, Co-Occurrence Analysis, Correlation, Causation</a>
        </li>
        <li>
          <a href="#Visualizing_High-Dimensional_Vectors"><span class="toc_number toc_depth_2">2.3</span> Visualizing High-Dimensional Vectors</a>
        </li>
        <li>
          <a href="#Clustering_with_Generative_Models"><span class="toc_number toc_depth_2">2.4</span> Clustering with Generative Models</a><ul>
            <li>
              <a href="#K-Means"><span class="toc_number toc_depth_3">2.4.1</span> K-Means</a>
            </li>
            <li>
              <a href="#Gaussian_Mixture_Model_GMM"><span class="toc_number toc_depth_3">2.4.2</span> Gaussian Mixture Model (GMM)</a>
            </li>
            <li>
              <a href="#DirichletProcess_Gaussian_Mixture_Model_DP-GMM"><span class="toc_number toc_depth_3">2.4.3</span> Dirichlet Process Gaussian Mixture Model (DP-GMM)</a>
            </li>
            <li>
              <a href="#CH_Index_and_Gap_Statistic"><span class="toc_number toc_depth_3">2.4.4</span> CH Index and Gap Statistic</a>
            </li>
          </ul>
        </li>
        
        <li>
          <a href="#Hierarchical_Clustering"><span class="toc_number toc_depth_2">2.5</span> Hierarchical Clustering</a><ul>
            <li>
              <a href="#Divisive_Clustering"><span class="toc_number toc_depth_3">2.5.1</span> Divisive Clustering</a>
            </li>
            <li>
              <a href="#Agglomerative_Clustering"><span class="toc_number toc_depth_3">2.5.2</span> Agglomerative Clustering</a>
            </li>
          </ul>
        </li>
        
        <li>
          <a href="#Before_You_Choose_a_Clustering_Method"><span class="toc_number toc_depth_2">2.6</span> Before You Choose a Clustering Method</a>
        </li>
        <li>
          <a href="#Topic_Modeling"><span class="toc_number toc_depth_2">2.7</span> Topic Modeling</a>
        </li>
      </ul>
    </li>
    
    <li>
      <a href="#Predictive_Data_Analysis"><span class="toc_number toc_depth_1">3</span> Predictive Data Analysis</a><ul>
        <li>
          <a href="#Classification"><span class="toc_number toc_depth_2">3.1</span> Classification</a><ul>
            <li>
              <a href="#kNN"><span class="toc_number toc_depth_3">3.1.1</span> kNN</a>
            </li>
            <li>
              <a href="#SVM"><span class="toc_number toc_depth_3">3.1.2</span> SVM</a>
            </li>
            <li>
              <a href="#SVM_Kernels"><span class="toc_number toc_depth_3">3.1.3</span> SVM Kernels</a>
            </li>
            <li>
              <a href="#Naive_Bayes"><span class="toc_number toc_depth_3">3.1.4</span> Naive Bayes</a>
            </li>
            <li>
              <a href="#Method_Evaluation"><span class="toc_number toc_depth_3">3.1.5</span> Method Evaluation</a>
            </li>
          </ul>
        </li>
        
        <li>
          <a href="#Regression"><span class="toc_number toc_depth_2">3.2</span> Regression</a><ul>
            <li>
              <a href="#Decision_Trees_for_Classification"><span class="toc_number toc_depth_3">3.2.1</span> Decision Trees for Classification</a>
            </li>
            <li>
              <a href="#Decision_Trees_for_Regression"><span class="toc_number toc_depth_3">3.2.2</span> Decision Trees for Regression</a>
            </li>
            <li>
              <a href="#Random_Forest_and_Extremely_Randomized_Trees"><span class="toc_number toc_depth_3">3.2.3</span> Random Forest and Extremely Randomized Trees</a>
            </li>
            <li>
              <a href="#Boosting"><span class="toc_number toc_depth_3">3.2.4</span> Boosting</a>
            </li>
          </ul>
        </li>
        
        <li>
          <a href="#Deep_Learning"><span class="toc_number toc_depth_2">3.3</span> Deep Learning</a><ul>
            <li>
              <a href="#Handwritten_Digit_Demo"><span class="toc_number toc_depth_3">3.3.1</span> Handwritten Digit Demo</a>
            </li>
            <li>
              <a href="#Convolutional_Neural_Network_CNN"><span class="toc_number toc_depth_3">3.3.2</span> Convolutional Neural Network (CNN)</a>
            </li>
            <li>
              <a href="#Recurrent_Neural_Network_RNN"><span class="toc_number toc_depth_3">3.3.3</span> Recurrent Neural Network (RNN)</a>
            </li>
            <li>
              <a href="#Gradient_Descent"><span class="toc_number toc_depth_3">3.3.4</span> Gradient Descent</a>
            </li>
            <li>
              <a href="#Dealing_with_Small_Datasets"><span class="toc_number toc_depth_3">3.3.5</span> Dealing with Small Datasets</a>
            </li>
          </ul>
        </li>
      </ul>
    </li>
  </ul>
</div>

# <span id="Introduction">Introduction</span>

This is what I learned in a CMU course, 95-865 Unstructured Data Analytics, from [George Chen](http://www.andrew.cmu.edu/user/georgech/). I learned clustering, topic modeling, classification, regression, deep learning and method evaluation methods. I did assignments about Zipf&#8217;s Law with spaCY, mobile applications analysis with LDA, email spam detection with kNN, Bernoulli Naive Bayes and SVM, tweet sentiment analysis with RNN, image segmentation with CNN. Because some datasets are extremely large, AWS was introduced as well.

I have to say it&#8217;s a very good combination of theory and practice. I did learn a lot from this course.

# <span id="Exploratory_Data_Analysis">Exploratory Data Analysis</span>

## <span id="Basic_Text_Analysis">Basic Text Analysis</span>

The very first step could be extracting words from the document. Then we will have a simple term frequencies table. Normally, the order of the words doesn&#8217;t matter. It&#8217;s like putting the words into a bag, also known as **Bag of Words Model**. We can also apply this technique to many documents and we call the resulting term frequencies **collection term frequency (ctf)**. From the frequencies, we can find some interesting probability distributions which are a key component to the success of many modern AI methods.

In text analysis, we need to think about **stop words**. Usually, we should remove them. But, sometimes we&#8217;d better keep them. For example, _&#8220;To be or not to be&#8221;_. Also, there may be words that have same meaning, like &#8220;The&#8221; and &#8220;the&#8221;, &#8220;walk&#8221; and &#8220;walking&#8221;, &#8220;democracy&#8221; and &#8220;democratization&#8221; etc. Merging them together is called **lemmatization**. On the other hand, one word may have multiple meanings. So, we may want to split it up to multiple words. This problem is called word sense **disambiguation (WSD)**. Some conventional methods to deal with it are knowledge-based methods, semi-supervised methods, supervised methods and unsupervised methods. Besides, we should treat some phrases as a single word, such as &#8220;United States&#8221;.

Some other common NLP tasks include **tokenization**(find atomic words), **part-of-speech tagging**(find nouns, verbs, etc.), **sentence recognition**(figure out when a sentence ends) etc.

So far, if we use only one word as element of our model. It&#8217;s called **unigram** model. This model may have some problems. Because it ignores word order and word agreement. For example, P(w = hello world) = P(w = hello) * P(w = world) = P(w = world hello). Word agreement means it cannot distinguish good sentences and bad sentences, such as P(w = i am &#8230; we are &#8230;) = P(w = i are &#8230; we am &#8230;). For this problem, we can use **bigram** or **n-gram** models. It means we can use 2 or more words as element. We can solve the problems and increase the vocabulary size dramatically at the same time.

For NLP, python has a good open-source library called **spaCy**.

## <span id="Feature_Vector_Co-Occurrence_Analysis_Correlation_Causation">Feature Vector, Co-Occurrence Analysis, Correlation, Causation</span>

Now, we want to process the term frequencies table a little bit. We represent terms as &#8220;features&#8221; and use frequencies as values. Then we can get a **feature vector**, like this [0.1, 0.3, 0.2, 0.4] representing &#8220;sunny&#8221;, &#8220;cloudy&#8221;, &#8220;rainy&#8221;, &#8220;snowy&#8221;.

We may find words in text often seem to have some kind of relationship. For example, &#8220;Tim Cook&#8221; and &#8220;Apple&#8221;, &#8220;Elon Mush&#8221; and &#8220;Tesla&#8221;. We can use **co-occurrences** to figure it out. But, speaking of co-occurrences, there&#8217;re also many approaches. We can count the number of lines in which two entities co-occur. We can count the number of paragraphs, documents etc. as well. We should use the approach which makes the most sense in the specific case.

Here&#8217;s a use case of co-occurrences.

Assume we are looking at a picture of zebra and grass and there&#8217;re only black, white and green pixels. Then we start counting: for each pixel, look at 4 neighboring pixels, compare the values and add the values to a table.

<img class="alignnone wp-image-101" src="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-23-at-1.16.07-PM-300x75.png" alt="" width="348" height="87" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-23-at-1.16.07-PM-300x75.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-23-at-1.16.07-PM-768x192.png 768w, http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-23-at-1.16.07-PM.png 785w" sizes="(max-width: 348px) 100vw, 348px" /> 

Now, think of the bag of words model. We take [green, green], [green, white], [green, black]&#8230; into the bag. There will be 5750 cards in the bag. And we can calculate the probabilities of P(green, white), P(white, black), P(white) etc.

Then we can use **pointwise mutual information (PMI)** to measure surprise. The higher PMI means more surprising. The formula for PMI is as follows.

<img class="alignnone size-medium wp-image-102" src="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-23-at-1.29.21-PM-300x118.png" alt="" width="300" height="118" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-23-at-1.29.21-PM-300x118.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-23-at-1.29.21-PM.png 353w" sizes="(max-width: 300px) 100vw, 300px" /> 

P(A, B) represents A and B co-occurring. P(A) is A occurring. P(B) is B occurring. If A and B are independent, P(A, B) = P(A) P(B) and PMI = 0.

In practice, it&#8217;s helpful to generalize PMI. We can add a positive tune parameter to it.

<img class="alignnone size-medium wp-image-106" src="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-23-at-8.19.13-PM-300x92.png" alt="" width="300" height="92" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-23-at-8.19.13-PM-300x92.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-23-at-8.19.13-PM.png 375w" sizes="(max-width: 300px) 100vw, 300px" /> 

PMI is used to measure one pair of entities. To measure all pairs we can use **Phi-square** and **Chi-square**. Its formula is as follows.

<img class="alignnone size-medium wp-image-105" src="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-23-at-8.07.56-PM-300x83.png" alt="" width="300" height="83" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-23-at-8.07.56-PM-300x83.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-23-at-8.07.56-PM.png 458w" sizes="(max-width: 300px) 100vw, 300px" /> 

Chi-square = N * Phi-square, where N is the total number of occurrences like 5750 cards before.

Then we can use simple **scatter plot** to look if there&#8217;s any pattern in data. It can be negatively correlated, positively correlated or not really correlated. But two variable being correlated doesn&#8217;t mean one can predict another.

**Correlation** is not **causation**. For example, sunspot number and number of Republican senators may be highly correlated. But they are totally not related things. There&#8217;s no causation between them. To find real causality, we should divide users into 2 groups, **treatment group** and **control group**. Then we can use **randomized controlled trial (RCT)**, also called **A/B testing**. Amazon is using this method to figure out webpage layout to maximize revenue. Khan Academy is using this to find out how to present materials to improve learning.

Besides, what is the difference between probability theory and statistics?

Probability theory:

  * Assume we know model of randomness and parameters
  * Reason about what happens in the model, what data X look like

Statistics:

  * Assume we collect data X
  * Reason about what model of randomness make sense, and what the parameters are

## <span id="Visualizing_High-Dimensional_Vectors">Visualizing High-Dimensional Vectors</span>

We live in a 3-dimensional space. It can be very hard for us to imagine high-dimensional data. So, to gain some insights, we need to reduce the dimensionality to 1, 2, or 3.

One common linear approach is **principal component analysis (PCA)**. It basically flattens the data to lower dimensionality. For example, from 2D to 1D, we can squeeze data to one line. In that case, there&#8217;re 360 degrees. It is about finding the line that ensures the most variability. PCA is about finding top k orthogonal directions that explain the most variance in the data. Here is a visualization [example](http://setosa.io/ev/principal-component-analysis/).

But, what if the data is extremely non-linear distributed. Imagine a Swiss Roll. PCA won&#8217;t work well in this case. Then we should use some non-linear dimensionality reduction techniques, like finding low-dimensional &#8220;manifold&#8221; which is called **manifold learning**. 2 specific approaches for manifold learning are **Isomap** and **t-SNE**. Isomap is about calculating the distance between data points and finding nearest neighbors. t-SNE represents t-distributed stochastic neighbor embedding. One significant difference between Isomap and t-SNE is that t-SNE doesn&#8217;t use deterministic definition of which points are neighbors. It uses probabilistic notation instead. Points similarity probability distribution will help here. It improves the low-dimensional distribution representation until it&#8217;s as close as the original one as possible.

Normally, PCA and t-SNE are good candidates for your first try. They cover both linear and non-linear potentiality.

## <span id="Clustering_with_Generative_Models">Clustering with Generative Models</span>

Clustering is a highly useful process, which can divide entities into different groups. One example is recommendation system, where clustering can give different recommendations to different clusters. We can build a user-item matrix and figure out the similarity among users.

In terms of similarity, there&#8217;s usually not a &#8220;best&#8221; way to define it. There&#8217;re 2 popular methods for it, **cosine similarity** and **Euclidean distance**.

  * Cosine similarity:

<img class="alignnone size-medium wp-image-109" src="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-24-at-10.06.22-AM-300x79.png" alt="" width="300" height="79" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-24-at-10.06.22-AM-300x79.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-24-at-10.06.22-AM.png 481w" sizes="(max-width: 300px) 100vw, 300px" /> 

  * Euclidean distance:

<img class="alignnone size-medium wp-image-110" src="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-24-at-10.12.35-AM-300x69.png" alt="" width="300" height="69" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-24-at-10.12.35-AM-300x69.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-24-at-10.12.35-AM.png 512w" sizes="(max-width: 300px) 100vw, 300px" /> 

For comparing similarities of **time series**, we need to align them first. Think of shifting one along x-axis to align with another. Then the distance can be the area between the two.

To **diagnose** the similarity function&#8217;s result, we can pick one data point and compute its similarity with all the other points. Find out the highest one. Look if you can interpret them. If not, the similarity function isn&#8217;t very good.

Let&#8217;s move from similarity to clusters. There&#8217;re two main clustering methods, **generative models** and **hierarchical clustering**.

Generative models mean we first pretend the data generated by specific model with parameters. Learn the parameters(&#8220;fit&#8221; model to data). Then use fitted model to determine cluster assignments.

Hierarchical clustering won&#8217;t assume any model. It starts with all data points in one cluster then decide on how to split or start with all points in its own cluster and then merge them. In short, it can be top-down or bottom-up.

We will talk about generative models first, then hierarchical clustering.

### <span id="K-Means">K-Means</span>

K-means belongs to generative models. We need to decide how many clusters we want first, which is k. Then it will guess where the centers of cluster are. Assign each point to belong to the closest cluster and update cluster means. Repeat this process until convergence.

In other words, it repeat find the closest centroid -> update centroid process until it finds the perfect centroids. Here is a [visualization](http://stanford.edu/class/ee103/visualizations/kmeans/kmeans.html) of it. Obviously, k matters a lot here.

It is suggested to incrementally add centers and add them far from existing centers.

### <span id="Gaussian_Mixture_Model_GMM">Gaussian Mixture Model (GMM)</span>

Gaussian mixture model is also a generative model. It assumes data points sampled independently from different Gaussian distributions. Each Gaussian distribution can be treated as a cluster.

For GMM, learning (&#8220;fitting&#8221;) the parameters is about data points and k as input, mean, covariance of each gaussian distribution as output.

GMM uses **EM(Expectation-Maximization) algorithm**. In simple words, EM is repeating calculating expectation and maximize expectation. Unlike k-means, which hard assigns each point to clusters, EM does a soft assignment probabilistically.

Normally, k-means doesn&#8217;t work as well as GMM if the ellipses are not typical circles.

### <span id="DirichletProcess_Gaussian_Mixture_Model_DP-GMM">Dirichlet Process Gaussian Mixture Model (DP-GMM)</span>

Dirichlet process is one of the stochastic processes. It is a probability distribution of probability distribution.

For DP-GMM, you don&#8217;t have to decide on k manually. Number of clusters is effectively random and can grow with the data amount. But, you will need to choose a different parameter which indicates how likely new points are to form new clusters vs join existing clusters.

We can also apply Dirichlet process to k-means. Then it will be **DP-means**. It also has another parameter, which is the square of the radius around one data point to decide on how to divide the clusters.

### <span id="CH_Index_and_Gap_Statistic">CH Index and Gap Statistic</span>

We can also choose a cost function to compute for different k. The pick the k which achieved the lowest cost.

One approach with flaw is **Residual Sum of Squares (RSS)**. For each cluster, we can calculate a RSS. Finally, we can sum RSS of the k clusters. But, why it is not a very good approach? Think of each data point is a cluster. The RSS will be 0. RSS measures with-in cluster variation.

A better approach is considering both RSS and between-cluster variation.

Let W = RSS,

<img class="alignnone size-medium wp-image-117" src="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-26-at-2.19.27-PM-300x80.png" alt="" width="300" height="80" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-26-at-2.19.27-PM-300x80.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-26-at-2.19.27-PM.png 433w" sizes="(max-width: 300px) 100vw, 300px" /> 

n = total number of points

<img class="alignnone size-full wp-image-116" src="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-26-at-2.20.07-PM.png" alt="" width="195" height="59" /> 

This approach is called **CH index**,** **where CH stands for <span style="font-size: 1rem;">Calinski and Harabasz.</span>

Another good approach is **gap statistic**.

<img class="alignnone size-medium wp-image-118" src="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-26-at-2.30.31-PM-300x59.png" alt="" width="300" height="59" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-26-at-2.30.31-PM-300x59.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-26-at-2.30.31-PM.png 338w" sizes="(max-width: 300px) 100vw, 300px" /> 

It uses **Mean Squared Error (MSE)** and **Maximum Likelihood Estimation (MLE)**. Here&#8217;s a paper about [gap statistic](https://web.stanford.edu/~hastie/Papers/gap.pdf).

## <span id="Hierarchical_Clustering">Hierarchical Clustering</span>

Let&#8217;s move on from generative models to hierarchical clustering.

### <span id="Divisive_Clustering">Divisive Clustering</span>

This method firstly assumes all data points in one cluster. Then use a method to split the cluster(e.g., k-means, k=2). Then decide on the next cluster to split(e.g., pick the cluster with highest RSS). Repeat this process until some termination condition is reached.

### <span id="Agglomerative_Clustering">Agglomerative Clustering</span>

Agglomerative clustering basically is a reverse version of divisive clustering. It first assumes each point is a cluster. Then find the most &#8220;similar&#8221; two clusters(e.g., pick pair of clusters which have closest cluster center). Then merge them.Repeat this process until some termination condition is reached.

There&#8217;re many ways to define &#8220;close&#8221; in agglomerative clustering. They are **single linkage**, **complete linkage**, **centroid linkage**, **average linage**. Basically, they calculate the distance of nearest points, farthest points, centers, each point and average it between clusters, respectively. For the first two, clustering stays the same with monotonic transform. For the last two, clustering may change. They are not perfect. They fit different cases.

Finally, these two can be visualized with a **dendrogram**. Like this.

<img class="alignnone size-medium wp-image-121" src="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-26-at-2.52.19-PM-300x178.png" alt="" width="300" height="178" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-26-at-2.52.19-PM-300x178.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-26-at-2.52.19-PM.png 676w" sizes="(max-width: 300px) 100vw, 300px" /> 

## <span id="Before_You_Choose_a_Clustering_Method">Before You Choose a Clustering Method</span>

  * There&#8217;re some questions to think about.
  * Does Euclidean distance make sense?
  * Do you care about which cluster the new points belong to?
  * After visualization, do the clusters seem interpretable?
  * Compare the cluster centers, do they look reasonable?
  * How would you like to measure the result of clustering?

## <span id="Topic_Modeling">Topic Modeling</span>

In real-world cases, clustering is often not enough. One data point may belong to several clusters. For example, two users may share one Netflix account. Then we prefer assigning data points to multiple topics. This process is called **topic modeling**.

[**Latent Dirichlet Allocation (LDA)**](http://ai.stanford.edu/~ang/papers/jair03-lda.pdf) is a topic modeling approach. The basic idea is that documents are represented as random mixtures over latent topics, where each topic is characterized by a distribution of words.

For LDA, the input is a &#8220;document-word&#8221; matrix and a pre-specified number of topics k. And the output will be what the k topics are, which is also k topics&#8217; distribution of words.

&#8220;document-word&#8221; matrix -> &#8220;topic-document&#8221; matrix -> &#8220;word-topic&#8221; matrix

So, what if we want to automatically select k? The Bayesian nonparametric variant of LDA is **Hierarchical Dirichlet Process(HDP)**. It&#8217;s similar with GMM to DP-GMM.

There&#8217;re also some methods to measure the result. For a specific topic, look at _m_ most probable words(&#8220;top words&#8221;):

<img class="alignnone size-medium wp-image-124" src="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-26-at-8.02.27-PM-300x116.png" alt="" width="300" height="116" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-26-at-8.02.27-PM-300x116.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-26-at-8.02.27-PM-768x297.png 768w, http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-26-at-8.02.27-PM.png 849w" sizes="(max-width: 300px) 100vw, 300px" /> 

Beyond LDA and HDP, there&#8217;re also many other topic modeling methods. For example, correlated topic models, Pachinko allocation, biterm topic models, anchor word topic models, dynamic topic models&#8230;

# <span id="Predictive_Data_Analysis">Predictive Data Analysis</span>

## <span id="Classification">Classification</span>

One main difference between classification and clustering is that, in terms of classification, data have labels. It&#8217;s thereby supervised. And clustering is unsupervised.

Labeled data: {(x1, y1), (x2, y2), (x3, y3)&#8230;}, where y stands for label.

The labels have some types.

  * Binary: yi belongs to {0, 1}
  * Multi-class: yi belongs to {cat, dog, fish&#8230;}
  * Multi-label: yi belongs to {(cat, dog), (car, bike)&#8230;}

Also, there are many kinds of classification models.

  * Linear function
  * Tree-based
  * Nearest-neighbor
  * &#8230;

### <span id="kNN">kNN</span>

NN simply represents Nearest-neighbor. The training data will be like {(x1, y1), (x2, y2)&#8230;}. Then given a test point, say (xi, yi), it will compare its k neighbors. There will be a majority vote first. The test point will be classified to the majority type. But if the number of votes between different classes are equal. The algorithm will break the tie randomly.

According to [Cover and Hart](http://ieeexplore.ieee.org/document/1053964/), if the optimal classifier is with error _e_, 1-NN with k = 1 will have error less than 2_e_.

### <span id="SVM">SVM</span>

SVM is a linear classifier. It assumes the data is linearly separable and the goal is to find the best linear separator. To measure how good is the separator, it calculates the **margin**. The margin is <span style="font-size: 1rem;">perpendicular distance between the separator and the nearest data point. The goal can also be interpreted as finding </span>minimum margin separator.<span style="font-size: 1rem;"> </span>

### <span id="SVM_Kernels">SVM Kernels</span>

What if we want to separate non-linearly separable data points?

Using kernels!

<img class="alignnone size-medium wp-image-126" src="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-27-at-12.55.48-AM-300x141.png" alt="" width="300" height="141" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-27-at-12.55.48-AM-300x141.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-27-at-12.55.48-AM.png 311w" sizes="(max-width: 300px) 100vw, 300px" /> 

The rough idea is basically taking data into higher dimension by kernel methods. Then the data may be linearly separable in higher dimension.

Some example kernels are as follows:

<img class="alignnone size-medium wp-image-127" src="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-27-at-1.00.21-AM-300x90.png" alt="" width="300" height="90" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-27-at-1.00.21-AM-300x90.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/11/Screen-Shot-2017-11-27-at-1.00.21-AM.png 574w" sizes="(max-width: 300px) 100vw, 300px" /> 

### <span id="Naive_Bayes">Naive Bayes</span>

Unlike kNN calculating by distance and SVM calculating by margin, Naive Bayes takes advantage of probability theory, Bayes&#8217; Theorem specifically.

P(h|d) = (P(d|h) * P(h)) / P(d)

  * **P(h|d)** is the probability of hypothesis h given the data d. This is called the posterior probability.
  * **P(d|h)** is the probability of data d given that the hypothesis h was true.
  * **P(h)** is the probability of hypothesis h being true (regardless of the data). This is called the prior probability of h.
  * **P(d)** is the probability of the data (regardless of the hypothesis).

So, how does this theorem help? Let me give you an example.

Assume we are classifying people as male or female. And we have the features like long hair or not, higher than 170cm or not. Then one possible feature vector can be v = [0, 1], which means short hair and higher than 170cm.

Then based on the theorem,

p(male|v) = p(v|male) * p(male) / p(v)

It will be feasible to calculate. Also, if we are using this approach, one important assumption is that it assumes each feature is conditionally independent of others.

Then we can use this model the fit parameters, predict and smooth the results.

### <span id="Method_Evaluation">Method Evaluation</span>

There&#8217;re some steps to evaluate the previous models.

_Data preparation:_

A simple method is splitting data randomly into **train**, **validation** and **test**. And the split can be stratified based on the label.

To avoid wasting valuable training data, we can use another method, which is called k-Fold Cross-Validation. It will split data randomly into **train** and **test**. Then it will split train data randomly into k equal folds. It will train on one fold and validate on the remaining folds for k times. Finally, it will average the k metrics from each fold.

_Hyperparameter Selection:_

The difference between hyperparameter and parameter is that parameters will be learned automatically by machine. However, hyperparameter is set by human based on experience. The common approach is to define a &#8220;well-spaced grid&#8221; of hyperparameter values and select the one with the best performance.

_Performance Metrics:_

So how to measure the performance? Only using accuracy may not be a very good approach. There are better ones, like **precision-recall** and **f1-score**.

**Confusion Matrix:**

<img class="alignnone size-medium wp-image-133" style="font-size: 1rem;" src="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-06-at-12.59.26-AM-300x141.png" alt="" width="300" height="141" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-06-at-12.59.26-AM-300x141.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-06-at-12.59.26-AM.png 573w" sizes="(max-width: 300px) 100vw, 300px" /> 

We can calculate precision-recall and f1-score as follows.

<img class="alignnone size-medium wp-image-132" style="font-size: 1rem;" src="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-06-at-12.59.38-AM-300x149.png" alt="" width="300" height="149" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-06-at-12.59.38-AM-300x149.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-06-at-12.59.38-AM.png 530w" sizes="(max-width: 300px) 100vw, 300px" /> 

<img class="alignnone size-medium wp-image-131" style="font-size: 1rem;" src="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-06-at-12.59.50-AM-300x159.png" alt="" width="300" height="159" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-06-at-12.59.50-AM-300x159.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-06-at-12.59.50-AM.png 543w" sizes="(max-width: 300px) 100vw, 300px" /> 

Normally, the higher the precision, recall and f1-score are means the better performance.

## <span id="Regression">Regression</span>

Before we move on from classification to regression, what is the difference between them? For classification, the output variable takes class labels. For regression, the output variable takes continuous values.

kNN is normally used for classification. But, actually, with a regression kernel, we can change the discrete label to continuous label. For example, it&#8217;s possible to change {spam, ham} to range(1, 10).

### <span id="Decision_Trees_for_Classification">Decision Trees for Classification</span>

The general approach of decision trees looks like the idea of divisive clustering but accounts for labels.

It firstly picks a random feature and finds the threshold that makes the data as separate as possible. For each side, recurse until a termination condition is reached. The data will look like separated in many leaf cells.

The prediction of a test point can be determined by majority vote of training point in the same leaf cell.

### <span id="Decision_Trees_for_Regression">Decision Trees for Regression</span>

It&#8217;s very easy for decision trees to move from classification to regression. Except for, in the prediction part, it will predict by average in the same leaf cell.

To choose what kind of decision trees to use, we can refer to this picture.

<img class="alignnone wp-image-134" src="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-06-at-1.53.45-AM-300x249.png" alt="" width="328" height="272" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-06-at-1.53.45-AM-300x249.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-06-at-1.53.45-AM.png 531w" sizes="(max-width: 328px) 100vw, 328px" /> 

### <span id="Random_Forest_and_Extremely_Randomized_Trees">Random Forest and Extremely Randomized Trees</span>

Typically, a decision tree is learned randomly. Therefore, by re-running the same learning procedure, we can get different decision trees and different predictions.

Then we can aggregate the prediction results from different trees. The performance will be better if we add randomness.

Random Forest:

In addition to randomly choosing features to threshold, it also randomizes training data used for each tree.

Extremely randomized trees:

It further randomizes thresholds rather than trying to pick clever thresholds.

### <span id="Boosting">Boosting</span>

The basic idea of boosting is leaning trees sequentially and learning from previous trees&#8217; mistakes. It will weight trees unequally, so bad trees are down-weighted.

There&#8217;re different boosting methods. Some popular ones are **AdaBoost** and **gradient tree boosting**.

## <span id="Deep_Learning">Deep Learning</span>

Big data, better hardware and better algorithms are the three pillars of deep learning. With the improvement of those technologies, deep learning grows fast. People are talking more and more about deep learning.

But, how deep learning works? Given an image of a cat, it will extract different features like edges, texture, colors. And then it will assemble them to segment and part. Then finally,  it will learn it as a cat.

For different kind of data, we should choose different neural network architectures. Like for **image analysis**, **Convolutional Neural Network(CNN)** works well. And for **time series analysis**, **Recurrent Neural Network(RNN)** has good performence.

### <span id="Handwritten_Digit_Demo">Handwritten Digit Demo</span>

This demo is pretty much used everywhere. It&#8217;s kind of deep learning&#8217;s hello world. In this part, I would like to explain in the code.

<pre class="brush: python; title: ; notranslate" title="">%matplotlib inline
import matplotlib.pyplot as plt
import numpy as np

from keras.datasets import mnist
from keras import models
from keras import layers

# loading data
(train_images, train_labels), (test_images, test_labels) = mnist.load_data()
# train_images.shape -&amp;gt; (60000, 28, 28)
# test_images.shape -&amp;gt; (10000, 28, 28)
# train_labels.shape -&amp;gt; (60000,)
# test_labels.shape -&amp;gt; (10000,)

# flatten 28 * 28 data to 784 * 1 data
# it will be easier for neural network to learn the parameters
# input shape will be (784,) and it's also called 784 input neurons
flattened_train_images = train_images.reshape(len(train_images), -1) # flattens out each training image
flattened_test_images = test_images.reshape(len(test_images), -1) # flattens out each test image
# train_images.shape -&amp;gt; (60000, 784)
# test_images.shape -&amp;gt; (10000, 784)

flattened_train_images = flattened_train_images.astype(np.float32) / 255 # rescale to be between 0 and 1
flattened_test_images = flattened_test_images.astype(np.float32) / 255 # rescale to be between 0 and 1
# to_categorical is basically change the label to higher dimension
# in this case, there're 10 labels(0-9)
# so, this method will change them to 10 dimension and there will be only 0 and 1
from keras.utils import to_categorical
train_labels_categorical = to_categorical(train_labels)
test_labels_categorical = to_categorical(test_labels)
# for example:
# train_labels[6] -&amp;gt; 5
# train_labels_categorical -&amp;gt; array([ 0., 0., 0., 0., 0., 1., 0., 0., 0., 0.])

# two-layer model
two_layer_model = models.Sequential() # this is Keras's way of specifying a model that is a single sequence of layers
# only specify input_shape in the first layer
# following layers will figure it out automatically
# passing data to dense layer is basically compress the data
# each neuron in dense layer has different calculating ways
# this process will parameterized the input data to a weighted matrix(W) and bias(b)
# activation is kind of post-process for the learned parameters
two_layer_model.add(layers.Dense(512, activation='relu', input_shape=(784,)))
# total learned parameters number in first layer will be 784 * 512(W) + 512(b) = 401920
two_layer_model.add(layers.Dense(10, activation='softmax'))
# total learned parameters number in second layer will be 512 * 10(W) + 10(b) = 5130
# then we will need to choose the optimizer, loss function and metrics
two_layer_model.compile(optimizer='rmsprop',
loss='categorical_crossentropy',
metrics=['accuracy'])
two_layer_model.summary() # display the summary of the neural network

# epochs is how many times we train the model or the model learn the parameters
# batch_size is kind of buffer, a batch of data to put into training or learning
two_layer_model.fit(flattened_train_images, train_labels_categorical, epochs=5, batch_size=128)

# evaluation and print out accuracy
test_loss, test_acc = two_layer_model.evaluate(flattened_test_images, test_labels_categorical)
print('Test accuracy:', test_acc)

</pre>

### <span id="Convolutional_Neural_Network_CNN">Convolutional Neural Network (CNN)</span>

The basic idea of CNN is quite straight-forward. It&#8217;s baiscally using a **filter**(or **kernel**) to scan the image, from left to right, top to down. It will calculate the dot product and finally output a smaller image.

<img class="alignnone size-medium wp-image-150" src="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-09-at-6.32.05-PM-300x183.png" alt="" width="300" height="183" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-09-at-6.32.05-PM-300x183.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-09-at-6.32.05-PM.png 514w" sizes="(max-width: 300px) 100vw, 300px" /> 

Different kernels may have different values, which gives them different functions. For example, it can be used for blurring an image or finding horizontal edges. And the kernels are actually unknown and are learned.

<img class="alignnone size-medium wp-image-149" src="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-09-at-6.32.36-PM-300x187.png" alt="" width="300" height="187" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-09-at-6.32.36-PM-300x187.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-09-at-6.32.36-PM.png 527w" sizes="(max-width: 300px) 100vw, 300px" /> 

Input image&#8217;s dimensions include height, width and depth(number of channels, e.g. RGB can be viewed as 3 channels). And after the conv2d layer, which has k kernels of 3x3xd, the output will be a stack of images, also known as feature maps. Output dimensions include height, width and k. And the k will be the next layer&#8217;s channel or depth.

Then, normally, there will be a pooling process to aggregate local information and produce a smaller image. **Max pooling** is one popular pooling method. It&#8217;s simply select the maximum value.

conv2d plus max pooling equals the basic building block of CNN. We can add many this kind of blocks. From the first block to the last block, it extracts from low-level to high-level visual features and aggregate. Finally, there may be a dense, ReLU and a dense, softmax, which are non-vision-specific classification neural net and loss function calculation.

### <span id="Recurrent_Neural_Network_RNN">Recurrent Neural Network (RNN)</span>

RNN&#8217;s basic idea is feeding output at previous time step as input to RNN layer at current time step. Given this idea, it performs well in handling timer series problems.

Two common RNN layers in keras are **SimpleRNN** and **LSTM**. The difference between these two is that LSTM has a longer memory.

_A standard RNN:_

<img class="alignnone size-medium wp-image-152" src="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-10-at-12.25.31-AM-300x107.png" alt="" width="300" height="107" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-10-at-12.25.31-AM-300x107.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-10-at-12.25.31-AM-768x274.png 768w, http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-10-at-12.25.31-AM.png 795w" sizes="(max-width: 300px) 100vw, 300px" /> 

_LSTM:_

<img class="alignnone wp-image-151" src="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-10-at-12.25.42-AM-300x98.png" alt="" width="312" height="102" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-10-at-12.25.42-AM-300x98.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-10-at-12.25.42-AM-768x251.png 768w, http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-10-at-12.25.42-AM.png 861w" sizes="(max-width: 312px) 100vw, 312px" /> 

RNN is likely to play with other neural networks. For example, dealing with video, it will put a CNN before RNN naturally and add a dense layer as classifier at the end. For text sentiment analysis, we should put an **embedding layer** (common approaches for this include word2vec and GloVe) before RNN, which will turn words into vector representations that are semantically meaningful, followed by a dense layer as classifier as well.

By the way, for classification with more than 2 classes, it&#8217;s better to use a dense layer with multiple neurons and softmax activation. For classification of 2 classes, it&#8217;s better to use a dense layer with one neuron and sigmoid activation.

### <span id="Gradient_Descent">Gradient Descent</span>

Gradient descent is about finding the parameters W, which lead to minium loss. In practice, deep nets have more millions of parameters. So, it&#8217;s very high-dimensional gradient descent. Here&#8217;re two simple examples(1D and 2D) to give you an intuition.

_1D:_

<img class="alignnone size-medium wp-image-155" src="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-10-at-1.20.32-AM-300x189.png" alt="" width="300" height="189" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-10-at-1.20.32-AM-300x189.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-10-at-1.20.32-AM.png 589w" sizes="(max-width: 300px) 100vw, 300px" /> 

_2D:_

<img class="alignnone size-medium wp-image-154" src="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-10-at-1.20.44-AM-300x199.png" alt="" width="300" height="199" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-10-at-1.20.44-AM-300x199.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-10-at-1.20.44-AM.png 513w" sizes="(max-width: 300px) 100vw, 300px" /> 

### <span id="Dealing_with_Small_Datasets">Dealing with Small Datasets</span>

  * Data Augmentation

This idea is similar to cross validation but not exactly the same. It maximums the use of datasets. For example, it can be using mirrored versions of images, rotated versions etc. to get larger datasets.

  * Fine Tune

This one basically means using existing pre-trained neural net. When it&#8217;s very hard to train the data, using the existing ones will be a good idea.

In the end, it&#8217;s been a very great course! It covered from the very basic concepts to some higher level approaches, combining theory as well as practice. I would like to use this picture to sum up.

<img class="alignnone size-medium wp-image-156" src="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-10-at-1.46.24-AM-300x195.png" alt="" width="300" height="195" srcset="http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-10-at-1.46.24-AM-300x195.png 300w, http://www.lucas-liu.com/wp-content/uploads/2017/12/Screen-Shot-2017-12-10-at-1.46.24-AM.png 560w" sizes="(max-width: 300px) 100vw, 300px" /> 

Thanks, George! Ciao!