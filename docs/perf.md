---
title: Posts About Performance Analysis and Optimization
---

I made a game with a friend in the same CS classes with me where any time we got our homework done
early, we would see who could make theirs faster or take in larger inputs without crashing. When
my first job after college had embarrassingly slow code, I parlayed that into my first 
specialization.

If I were to co-author a book, the most likely topic would be performance. And my half of the
contribution would be less about mechanical sympathy, and more about the craft and logistics of
performance work. That is its own art and the reason many balk at tackling known complaints about
application performance. They *won't* try because they don't know how to manage these concerns in a
way that will retain the other invariants on the project, like lead time, SLAs, and bug counts.

How do you identify and undertake a series of intricate architectural shifts in order to deliver
substantial gains in performance while retaining or reducing maintenance costs on that same code?
How do you keep a customer and project management engaged during the twelve to twenty-four months it
will take to fully realize these changes? How do you do surgery of this magnitude without
introducing an endless stream of new bugs? These are the reasons most developers say they "can't" do
it, when Sales comes to them with customer complaints.

A lot of performance is a mental more than a technical challenge. And I hope that comes across
in these linked articles:

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
