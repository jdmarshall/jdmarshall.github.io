---
title: Posts About Tools
---

I work a lot on tooling, because tooling lets me Work Smarter, Not Harder, and they let me 
exercise my UX skills on a user group that I know a lot about: developers. In the same way doctors
make the worst patients, developers can (but not always) make the worst users. These challenges
can help one hone their craft in both UX and [DX](/dx).

They are a particularly good way to slowly roll out new processes in a team or organization,
because as the tool matures you can increase your expectations of people to use the tools. 

I really should have more posts in this category than I do, given how often I think about it.

<nav>
  {% for post in site.posts %}
    {% if post.topics contains "DX" %}  
      <dl>
        <dt><a href="{{ post.url }}">{{ post.title }}</a></dt>
        <dd>{{post.excerpt}}</dd>
      </dl>
    {% endif %}
  {% endfor %}
</nav>
