---
layout: post
title: "Performance is a Budgeting Problem"
topics: [ Development, Performance, Growth ]
excerpt: "Performance is about Budgets, not tent poles, and certainly not fruits."
published: false
---

On the wider topic of label values:

If you guys don't know what your label values are at compile time, you are fundamentally misusing
your telemetry tools, in a manner similar to SQL injection attacks.

First, any vendor who charges based on label cardinality will make an absolute mint off of their fee
schedules that punish open ended label-value pairing. Worse, there are attack vectors there for DOS
attacks by exhausting memory or your monthly Cloud spend. There have been a lot of issues and
comments that make it very clear how misunderstood this behavior of Prometheus and OpenTelemetry
is - any combination of labels and values you record once costs you memory and bandwidth until the
process that recorded them shuts down. Uniqueness is very, very bad. And for that matter, rareness
should be associated with alerts - I am recording this data point because it's more valuable than
the nickel it will cost me to have it hanging around.

You should never, ever, have a situation in production where a label value needs to be sanitized for
any reason other than to escape Prometheus-disallowed punctuation characters, and even in that case,
likely could be avoided as well at PR time.

There are a few exceptions to values that aren't known at compile time but are still bounded, such
as version numbers and deployment numbers. And of course Exemplars may have some fuzzier data like
correlation-ids, but those are not technically labels. And none of those exceptions apply to this
issue.
