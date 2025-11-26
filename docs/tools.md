---
title: Tools
---
<nav>
  <ul>
    {% for post in site.posts %}
      {% if post.topics contains "Tools" %}  
        <li>
          <a href="{{ post.link }}">{{ post.title }}</a>
        </li>
      {% endif %}
    {% endfor %}
  </ul>
</nav>
