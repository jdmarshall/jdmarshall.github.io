---
title: Posts About Tools
---

I work a lot on tooling, because tooling lets me Work Smarter, Not Harder, and as they improve
they also help me help my coworkers Work Smarter as well. Tools let me exercise my UX and DX skills
on a user group that I know intimately: developers. In the same way doctors make the worst patients,
developers can (but not always) make the worst users. These challenges can help one hone their craft
in both UX and [DX](/dx).

They are a particularly good way to slowly roll out new processes in a team or organization,
because as the tool matures you can increase your expectations of people to use the tools. 

I really should have more posts in this category than I do, given how often I think about it.

A few of my tools are open sourced, but sadly most have been specific to particular project.
I am the creator of [faceoff](https://github.com/cobblers-children/faceoff), a maintainer of
[node-config](https://github.com/node-config/node-config), [bench-node](https://github.com/RafaelGSS/bench-node), and a frequent contributor to
[prom-client](https://github.com/siimon/prom-client).

### Posts About Tooling
<nav>
  {% for post in site.posts %}
    {% if post.topics contains "Tools" %}  
      <dl>
        <dt><a href="{{ post.url }}">{{ post.title }}</a></dt>
        <dd>{{post.excerpt}}</dd>
      </dl>
    {% endif %}
  {% endfor %}
</nav>
