---
title: Posts About Asynchronous Code
---

<nav>
  {% for post in site.posts %}
    {% if post.topics contains "Async" %}  
      <dl>
        <dt><a href="{{ post.url }}">{{ post.title }}</a></dt>
        <dd>{{post.excerpt}}</dd>
      </dl>
    {% endif %}
  {% endfor %}
</nav>
