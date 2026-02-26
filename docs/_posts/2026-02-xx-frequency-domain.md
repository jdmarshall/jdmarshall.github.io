---
layout: post
title: "Errors Should be Reasoned About in the Frequency Domain"
topics: [ Development, Growth ]
published: false
---

## Errors

Errors are one of those areas of software that explain easy but implement hard. And the problem
with putting effort into things that sound like they should be easy and are wicked hard to get
right is that absolutely nobody appreciates how difficult it is to make that 'simple' thing look
simple. So we avoid, or distract, or explain away why they're kind of garbage.

We do the straightforward. It is cheap to model errors as a fraction of the total interactions. 
It's just counting, with very cheap correlation. But it's much more difficult to notice that errors
are clustered. Around restarts, around other errors, around a class of users, or users from one 
town. 

But sometimes those users are influential. They can cost you a contract, or publicly shame you.

But perception and emotional responses to errors can't be modeled by statistics, or by search 
queries. I've seen people complain about problems and have the devs dismiss the complaint because
the patterns seem made up. Those people go away disgruntled. The developer acts as if they have 
'won' that conversation. They haven't won, in fact they might have started a ticking timebomb of
mistrust that comes back as longer meetings and more language lawyering about all new work. Just 
because they don't see it doesn't mean I don't see it. That their manager doesn't see it. That their
manager isn't taking it in the neck in high level meetings.

