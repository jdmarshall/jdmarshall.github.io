---
title: Posts about Tools
---

<nav>
  {% for post in site.posts %}
    {% if post.topics contains "DX" %}  
      <dl>
        <dt><a href="{{ post.link }}">{{ post.title }}</a></dt>
        <dd>{{post.excerpt}}</dd>
      </dl>
    {% endif %}
  {% endfor %}
</nav>
