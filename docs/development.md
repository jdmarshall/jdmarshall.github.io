---
title: Posts About the Software Development Lifecycle
---

How we build things informs what we can build. Most projects leave a lot of productivity on the
table because they disbelieve that a [sharpened saw](https://www.franklincovey.com/courses/the-7-habits/habit-7/) will pay for itself in a surprisingly
short period.

<nav>
  {% for post in site.posts %}
    {% if post.topics contains "Development" %}  
      <dl>
        <dt><a href="{{ post.url }}">{{ post.title }}</a></dt>
        <dd>{{post.excerpt}}</dd>
      </dl>
    {% endif %}
  {% endfor %}
</nav>
