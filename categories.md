---
layout: page
permalink: /categories/
title: Categories
---

<div>
  {% for category in site.categories reversed %}
        
    {% capture category_name %}{{ category | first }}{% endcapture %}
    
    {% if category_name == 'hydejack' %}
        {% continue %}
    {% endif %}
    
    <h3 class="category-head">{{ category_name }}</h3>

    <ul id="blog-posts" class="posts">
        {% for post in site.categories[category_name] %}
        <li><span>{{ post.date | date_to_string }} &raquo;</span><a href="{{ post.url }}">{{ post.title }}</a></li>
        {% endfor %}
    </ul>

  {% endfor %}
</div>