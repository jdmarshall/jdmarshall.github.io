---
title: Posts about Developer Experience
---
<nav>
  <ul>
    {% for post in site.posts %}
      {% if post.topics contains "DX" %}  
        <li>
          <a href="{{ post.link }}">{{ post.title }}</a>
        </li>
      {% endif %}
    {% endfor %}
  </ul>
</nav>
