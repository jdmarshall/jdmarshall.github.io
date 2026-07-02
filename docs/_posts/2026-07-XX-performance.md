---
layout: post
title: "Performance is a Budgeting Problem"
topics: [ Development, Performance, Growth ]
excerpt: "Performance is about Budgets, not tent poles, and certainly not fruits."
published: false
---

    Everything has been said before; but since nobody listens, we must always start again.

    -- André Gide

If you're a game developer, what I'm about to say here may be things that you already know. But I 
find that it's often worth the effort to learn new ways to say and frame the things you already
know, to reach audiences who resist hearing. And that is often why I write anyway - to practice 
saying things again in a new way. 

# Performance as a Budgetary Concern


# How Did We Get Here?

For decades, people have been misquoting Knuth's "Optimization is the Root of All Evil" in a way
that shut down needed conversations about code quality and operational costs. That issue festered
for a long time but became much more obvious once we started developing in the cloud. And while
there are principal engineers now who may never have deployed anywhere else, much of the traditional 
(non-game-developer) advice on how to manage performance issues still dates to a time when people
self-hosted or ran their code on the user's machines, and we really should be re-examining that.

## In the Before Times

Traditionally, most of us were in a self-hosted environment, or writing applications that ran on
customer hardware.

In the case of customer hardware, the price of upgrades to continue to run your code was considered
an externality. In fact in some cases being an excuse for a customer to have to buy new hardware was
*appreciated*. We were generally so insulated or even enabled in this behavior that the guilt for
having created that situation was easily assuaged.  

When it was 'our hardware', that hardware was already paid for, quarters or sometimes years ago. As
long as your service ran on the hardware that you had available, it cost pretty much the same amount
to run. Any performance problems that did not tip you over into violating your internal SLAs were
effectively tech debt, because they didn't need to be fixed until you added a feature that would 
push you over your limits. Your better senior devs had a long list of Targets of Opportunity to work
on the next time performance was found wanting. Every big change comes with risk, and though
Refactoring de-risks many changes, there's still a single digit percentage chance that even
Refactoring won't save you, and over thousands of changes per year, sooner or later you'll break
something and not have a good scapegoat to throw under the bus. 

Politically, making a potentially breaking change in service of delivering a feature that the
business is *hungry* for is simple. In many cases their investment in The New will paper over any
incidental damaged caused in the pursuit of that new feature, so you wait.

## Autoscaling Means You Pay Now

Today we live in a world where misquoting Knuth literally doesn't pay the bills. Running a service
on 20% (or in one case I can know, 20x - that project failed) more hardware than the problem
strictly requires costs you money this month, not on some hypothetical Some Day. 

When a project is under active development, the cost of developers and project management still 
swamps the operational costs considerably. But once your ecosystem matures, you're going to have a
bunch of services that only get touched once a month, or twice a quarter. The cost for those
services is now dominated by operational expenditure. Even calling a service more often as the
problem requires due to code organization problems means not only more hardware but more log
shipping and telemetry management. All of these costs are in addition to the servers. 
