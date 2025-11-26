---
title: Development
---

<nav>
  <ul>
    {% for post in site.posts %}
      {% if post.topics contains "Development" %}  
        <li>
          <a href="{{ post.link }}">{{ post.title }}</a>
        </li>
      {% endif %}
    {% endfor %}
  </ul>
</nav>
