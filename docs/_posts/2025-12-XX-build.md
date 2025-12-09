---
layout: post
title: "Introducing Faceoff"
topics: [ Development, Tools, Performance ]
published: false
---

![Faceoff](https://github.com/cobblers-children/faceoff/blob/050e180aeefafdcb935e2e5a0536fadd3d4562ee/media/logo.svg)

## [Faceoff 1.1.0](https://github.com/cobblers-children/faceoff/)

This is sort of a big milestone for me, because it contains most of the things I initially had in
mind for this application. 

### Background: Why Are You Recreating a Tool?

Last Spring, I was fishing around for projects that were having either functionality or performance
issues that I could dig into. I generally feel that Prometheus is a better model for gathering app
telemetry than OpenTelemetry, but a brief scan of the 
[prom-client](https://github.com/siimon/prom-client) code showed some pretty straightforward issues
with the data storage format that I know how to improve, and conversations with other users
uncovered a bunch more, so I started working on it.

The problem is that `prom-client` is semi-mature code. It's not getting a lot of active maintenance
by the team. So my individual changes started piling up as parallel work. The other is that while
`prom-client` has build tasks that can detect performance changes in the code, it uses a tool called
[benchmark-regression](https://github.com/nowells/benchmark-regression), which hasn't been touched
in seven years, has a lot of challenges with asynchronous benchmarks, and has no way to test 
multiple branches of the same code against each other - it can test a release against your current
branch and that's it. Oh and it's built on top of another library, `benchmark.js` that was declared
End of Life by its author last winter. It also has issues with handling async code. So, not much
hope there.

When you're engaging in a rather enthusiastic campaign of optimizations like I was, I discovered
very quickly that it was getting harder and harder to keep track of how branch A affects performance
versus branch B which has now been merged and my branch is rebased on top of to resolve any 
conflicts. Several times I had to backpedal and update my claimed performance changes. And now that
I've had success getting improvements merged, some other people are trying to one-up me. Which is 
great for `prom-client` but confusing for us because, again, they haven't tagged a release in some 
time so the other people are getting my numbers and their numbers mixed together.

Long story short, I wanted more data.

So I poked around for what other alternatives to `benchmark.js` there were and I stumbled upon 
[bench-node](https://github.com/RafaelGSS/bench-node), which was still under active development
but already supported async tests, had better charts for my purposes, and looked like it could be
bent to fit the model I was using. I have now landed almost as many PRs on that project as I have
on `prom-client`.

## First Customer

I designed [faceoff](https://github.com/cobblers-children/faceoff) to be a mostly drop-in 
replacement for `benchmark-regression` and that has gone pretty well. A PR to use it for 
`prom-client` was merged in the day before Thanksgiving. I have since released 1.0 and have been
working on changes to support worker threads - changes that make me kind of wish I'd waited a little
longer to release 1.0 because I needed to change the lifecycle a little bit. Oh well.

So the main improvement, besides being much faster (2.5 vs 8 minutes according to the prom-client
team), is that it displays data like this, which I hope will be much more actionable:

```text
Summary (vs. baseline):
 ⇒ prom-client@latest            | █████████████████████████ | 14,035,024 ops/sec | 12 samples (baseline)
 ⇒ prom-client@trunk             | ████████████████████───── | 11,428,570 ops/sec | 12 samples (1.23x slower)
 ⇒ prom-client@keys              | ███████████████████████▌─ | 13,316,166 ops/sec | 12 samples (1.05x slower)

constructors ⇒ new Counter()

Summary (vs. baseline):
 ⇒ prom-client@latest            | ████████████████████████▌ | 1,203,153 ops/sec | 11 samples (baseline)
 ⇒ prom-client@trunk             | █████████████████████████ | 1,203,335 ops/sec | 11 samples (1.00x faster)
 ⇒ prom-client@keys              | ████████████████████████▌ | 1,190,763 ops/sec | 13 samples (1.01x slower)

util ⇒ LabelMap.keyFrom()

Summary (vs. baseline):
 ⇒ prom-client@trunk             | ███████████████████────── | 5,486,892 ops/sec | 10 samples (baseline)
 ⇒ prom-client@keys              | █████████████████████████ | 7,192,184 ops/sec | 11 samples (1.31x faster)


Performance Regressions:
------------------------

constructors ⇒ new Registry()
 ⇒ prom-client@latest            | █████████████████████████ | 15,173,658 ops/sec | 12 samples (baseline)
 ⇒ prom-client@trunk             | ███████████████████████── | 14,116,966 ops/sec | 10 samples (1.07x slower)
 ⇒ prom-client@keys              | ███████████████████████── | 14,081,520 ops/sec | 11 samples (1.08x slower)
```

## Next Steps

I'm not actually sure where this goes from here, though I should probably look up any of the old 
library's other dependencies and shop it around to them. See what features are missing. Meanwhile
I'm continuing to work with the `bench-node` folks to improve the data display and hopefully maybe
the accuracy as well. 
