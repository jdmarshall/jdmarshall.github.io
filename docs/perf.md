---
title: Posts About Performance Analysis and Optimization
---

I made a game with a friend in the same CS classes with me where any time we got our homework done
early, we would see who could make theirs faster or take in larger inputs without crashing. When
my first job after college had embarrassingly slow code, I parlayed that into my first 
specialization.

A lot of performance is a mental more than a technical challenge. And I hope that comes across
in the linked articles.

<nav>
  {% for post in site.posts %}
    {% if post.topics contains "Performance" %}  
      <dl>
        <dt><a href="{{ post.url }}">{{ post.title }}</a></dt>
        <dd>{{post.excerpt}}</dd>
      </dl>
    {% endif %}
  {% endfor %}
</nav>
