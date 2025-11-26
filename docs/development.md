---
title: Posts about Development
---

<nav>
  {% for post in site.posts %}
    {% if post.topics contains "Development" %}  
      <dl>
        <dt><a href="{{ post.link }}">{{ post.title }}</a></dt>
        <dd>{{post.excerpt}}</dd>
      </dl>
    {% endif %}
  {% endfor %}
</nav>
