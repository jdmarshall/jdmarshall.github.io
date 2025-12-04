---
published: false
---

This is NOT another post about how unit testing is a waste of time. What I am going to talk about is
the ways that unit testing is counter to your intuition, why that causes you to waste your time on
unit testing, and how you can get so much more out of your tests.

> You simply cannot hide from the ugly truth. - Matthew Sweet

Testing is not code. Testing is documentation. But you're a developer, and tests look exactly like
code, and of course you're going to think of them as code, right? So you'll apply your deep wealth
of coding intuition to it, at least three quarters of which will be wrong. And you'll either have a
bad experience, or notice that your coworkers are grumbling about the tests (your tests) and not
understand why they're bent out of shape about your tests, which you think are pretty decent, if you
do think so yourself.

Your 'gut instincts' will be maladaptive, but just enough of them will be feel right that you'll
convince yourself otherwise. And as a developer, your documentation skills are a little light. So
even if you identify that it's documentation, you'll still come up short. Testing is a discipline.
Like exercise, there are no shortcuts. Shortcuts look good for a long time, until they come back to
bite you in the ass. It's a lifestyle choice, and you have to keep at it, but if you force it,
you'll injure yourself in the process. Take it easy. A little bit is a lot better than none at all.
Baby steps.

What We Know

This is what we know. And when I say 'know', I don't mean truthiness. I mean that these are the
things we believe we have measured empirically, and repeated with different groups of people, in a
handful of programming languages. Irritatingly, some of these things were known back when XP was a
new thing, but too few of us listened. Sorry Kent, we let you down.

Small and Fast

Tiny tests are the only tests that are fast. You need an awful lot of them to say anything, but in
the Grand Scheme of things, this is chump change. The run time of the small tests grows much more
slowly than the equivalent big tests, and individual tests almost never get slower than when they
were written, no matter how much new functionality you've added to the system. Small tests adapt to
big shifts in functionality, because it's clear to everyone what they're trying to assert. When a
small test stops working, the replacement usually honors the concerns of the original. Small tests
do not trigger the Sunk Cost Fallacy in developers - nobody keeps small tests that don't work
anymore. When a small test is no longer relevant, it just gets deleted or replaced, with barely a
thought. When you notice a gap in your testing, it's reasonably straightforward to fill it in.

When a major architecture change causes a lot of small tests to fail, the developers can start
fixing tests right away, and most of the time can estimate how much longer it will take to fix the
tests. X tests were broken, Y tests still aren't passing, so it will hopefully take 2 more hours to
fix the tests.

Big and Slow

Big tests start out slow, but you have so few of them that this doesn't phase you. It doesn't
register that when you multiply the run time by 400 you'll have a problem, because it'll take you a
year to get there. You don't need many of them, and they dovetail perfectly well with code that is
factored only moderately or poorly. Most of the time it's lot easier to get your first Big Test to
pass because you didn't have to change much code to do it. Over the life of the project, however,
the run time for Big Tests will grow many times faster than the small tests, and the hands-on
maintenance cost will be roughly twice as high. Most importantly, that extra time usually comes in
unpredictable and awkwardly inconvenient bursts. Big tests are not happy with big functionality
changes. In some cases they may discourage the team from taking on strategic initiatives, putting
the whole company at risk.

Big tests run slower over time. They are rarely ever as fast as the day they were written. Certain
kinds of new functionality (especially authentication, sanity checks) can add significant overhead
to all of your existing Big Tests, making them more complicated and slower. When the Big Tests
break, things can get painful. Because they cover so much territory, Big Tests can glitch out,
failing randomly or inconsistently, slowly breeding distrust of the testing process in general. The
fact that they run slower, less frequently and touch more code makes debugging them take longer.
Since Big Tests trigger the Sunk Cost Fallacy, people will spend far longer and impact more people
trying to fix a bad test than it would take to simply rewrite it. But if and when they do rewrite
it, some of the scenarios will be missed. The complexity of the tests guarantees they are not
self-documenting, which will obscure the conditions it was meant to assert, and the new tests won't
succeed in making all of the same assertions. One day, you'll have bugs and you'll be absolutely
certain that you used to have a test for that. But you won't be able to find it. And as your tests
pile up, the run time becomes burdensome. People may start noticing regressions in the code before
the test run has a chance to fail. Why are we running all of these tests if the humans find the
problems faster? At the end of a Big Test Experiment, everybody who hates unit testing will feel
that all of their fears have been vindicated. They think they're slow, inaccurate, and distract you
from writing code. They're not wrong.
