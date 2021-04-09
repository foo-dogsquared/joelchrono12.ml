---
layout: default
title: Blog | joelchrono12
header: Blog Archive
description: This archive contains all of my blogs, ordered and divided by date
permalink: /blog/
---

{% assign postsByYear = site.posts | group_by_exp:"post", "post.date | date: '%Y'" %}
{% for year in postsByYear %}
  <h1>{{ year.name }}'s posts</h1>
{% assign postsByMonth = year.items | group_by_exp:"post", "post.date | date: '%B'" %}
{% for month in postsByMonth %}
<h2>{{ month.name }}</h2>
<ul>
  {% for post in month.items %}
   <li>
   <a href="{{ post.url }}">{{ post.title }}</a><br>
	   📅 {{ post.date | date: "%Y-%m-%d" }} 
	 {% for tag in post.tags %}
    <a class="posttag" href="/tags/{{ tag }}">{{ tag }}</a>  
	 {% endfor %}
   </li>
  {% endfor %}
	</ul>
{% endfor %}
{% endfor %}
