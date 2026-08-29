---
layout: post
title: "Numerical Rules I Live By"
topics: [ Development, Growth ]
excerpt: "Some of the aphorisms that I use at work are rules of thumb based upon numbers. These are some."
published: false
---

    A clever saying proves nothing.

    -- Voltaire

As a professional, you develop a lot of rules of thumb to help you decide how to focus your
attention. In a leadership position, you need even more. Some of those are about numbers. I first
had this idea of writing an article about rules of thumb with numbers in them three jobs ago, but I
am finally writing it down now because I realized I've changed by mind about one or two - it's not
enough to have a rule, you need to understand when it works and when it doesn't. Additionally, as 
I was thinking again about this over the last couple weeks, I discovered that one or two more had
snuck onto the list. I'm hoping to later include links that break out some of these to their own
article. A couple of them tried to get away from me here.

With minor exceptions, these rules are here presented in ascending order by cardinality which is 
perhaps not the best order, but it is **an** order.

### To Finish a Meeting in One Hour, You Must Finish Half the Meeting in a Half Hour

Good artists borrow, great artists steal. I stole this one from a boss early in my career.

I have however later refined this for large meetings, with the help of a peer, to include a 
meta-conversation about the agenda, so that the most people get the most out of the meeting.

For large or nearly staff-level meetings, you also want half the team to be able to tune out or
just leave to go back to working on tasks that are at risk. You need an agenda for these meetings,
and you need to take a straw poll about the agenda to figure out what order to take things. Usually
the thing that affects the most people is pretty straight forward, but number 2 or 3 on the agenda
is the literal elephant in the room. You don't and actually won't want to talk about that first,
because you need to get people settled. But if you leave it for 10 minutes before the end of the
meeting, everyone is tired, they've already blown social capital on other topics, and the solution
ends up being rushed, glib, ham-fisted.

If you save the stuff only three people care about to the end of the meeting, who cares if you run
over, as long as nobody else booked the room after you? They can either keep the room/conference
call, or segue into a private conversation.

### Single Responsibility Principle

First on our list is the one that I've diverged from the most. It is the idea that every function
and class should do one thing and do it well. It is also the Unix Way, although scope creep 
sometimes makes that a bit fuzzier. And also this one is surprisingly difficult to get your 
coworkers who are worried about timelines more than quality to follow. It can be a challenge to 
convince people that our velocity later will be better if we do preventative care now.

There's another discipline that accomplishes a similar outcome to SRP but through a different focus,
and that is Functional Programming. Not only does the function do one thing, but it does not 
mutate global state to do so. Therefore its Responsibility does not get entangled and entrapped with
others.

But even better than this is Imperative Shell, Functional Core. Imperative Shell follows the 
Pareto Principle. There is some portion of your code that should replicate the narrative that is 
recorded in the documentation. Everything below it should be pure, so that the complexity of 
understanding the code is more proportional to the logarithm of the number of lines in the program
rather than the square root, or worse, quadratic, or worst of all, factorial.

### Conceptual Integrity

This comes to us from Fred Brooks, who insists that, "The design must come from one mind", but 
there's another version of this idea that I prefer - the design doesn't have to come from one mind,
but it must *fit* into one, or else we are lost.

A peer of mine took a partial sabbatical to get a Masters Degree from Rensselaer Polytechnic
Institute. It was a sort of Business degree for Information Technology, complete with case studies.
That part in particular made me a little jealous, because I think we could all use formal coursework
in both case studies and code critique (Comparative Literature, but for software). 

One day he shared with me that the class taught that the surest predictor of success or failure on
a software project was whether at least one employee could fit the entire project into their head.

You can achieve this in one of two ways: either hire someone with a massive brain, or keep the 
system complexity under control. As with most professions, it is the balance of skill *and* 
discipline that matters. A genius can fit a fairly large system into their head, yet may still
choose to push back on complexity in order to reason more deeply about what we have and where we 
would like to take things in the future, and to be less of a bottleneck to the rest of the team. 
Discipline means that other members can also fit most of the application into their heads, making
some decisions obvious rather than pre-empting the One Person to negotiate. Anything you feel you
can safely leave until the code review is essentially optimistic locking. 

### You Haven't Proven You Can Do Something Until You've Done it Twice

Stolen from the same boss as the 1/2 rule. Serendipity or dumb luck can let you finish a task once
and convince yourself you know what you're doing. When you do it a second time, that luck tends to
break down and you find out that what you thought was working, didn't.

For operational things I like to take this further. When I work on runbooks, I don't declare it
done until I've had one person get through what I wrote without having to be rescued or prompted by
me to get past the tricky parts. I also don't pick the 'best' person for this job. If I can, I pick
the least qualified person who is likely to get asked. The one people talk to when they discover
everyone else is in a meeting or at lunch. If it doesn't work for them on a calm day, it won't work
for the rest of us when bosses have their hair on fire and are trying to delegate their anxiety.

### Rules Get One Exception

One thing I've learned about human cognition, is that we have very, very good recall of rules that
have exactly one exception. Any more than that and people forget. So much so that sometimes it seems
almost wilful - that they know they have plausible deniability by 'forgetting' the rule. Rules with
one exception are not only easier they also help keep us honest.

I knew about that rule for a number of years before I realized that the Rule of Three is a direct
consequence of this rule.

### The Rule of Three

Whenever we reach two exceptions to a function's happy path implementation, it's time to rethink
the solution to drag the number of options back to two. We often have to do this by resegmenting 
code. We turn two methods into three, or three methods into two. This is IME some of the most 
challenging refactoring work, especially with trunk-based development or pressure to keep PRs 
small and plentiful for large initiatives. 

### Bus Numbers

This rule probably belongs between the previous two, but they go so nice together I couldn't 
split them up. Three people need to understand every part of the code, or you collectively don't 
understand it. Anything with less than two is an active liability. When you have 2 people and an 
understudy, you can begin to relax, and only check on the progress occasionally, but until then
it should be an active agenda item. These should also inform how you write Done criteria for Epics,
because you can't walk away from an initiative until multiple people actually understand it.

#### Promotion Treadmills and Bus Numbers

Being third in line for a bus number is one of the best ways I know to groom Journeyman engineers 
for a promotion. In many companies, you almost have to be doing the next job up to get promoted. And
you can't call yourself a Senior Developer if you're not *responsible* for anything. But having 
*sole* responsibility is its own liability.

Similarly, the Number 2 slot is a good spot for aspiring Staff Engineers. Because as a Lead or 
a Principal, in order to avoid stretching yourself too thin, you need to constantly make yourself 
bus number 2, 3 or sometimes remove yourself entirely from things that you invented, created, or 
sponsored, so that you have the brain space to worry about the Next Big Problem. Your #2 becomes
the primary, and either you or #3 become the secondary, and if and when you do pull back entirely, 
the new primary becomes responsible for training your replacement, while any gaps in  their
knowledge can still be filled from yours before it atrophies from disuse. 

### Conditional Branching Depth

Cognitive Scientists have determined that the average developer can handle conditional branches that
are 3 deep, and above average developers can handle 4. We avoid this by breaking complex decisions
into multiple steps, giving those decisions meaningful names. We have functions that are only called
when certain preconditions are met, so they can be taken as assumed. 

and occasionally rejecting features as
being too complex to maintain.

### Four Questions Equal a Design Flaw

People get angry with you about your code. They're not always right. They don't understand the three
other contexts that are in a different problem domain that you have to handle just as well or better
than theirs. And you eventually discover that they get mad about the wrong parts of the things
they're mad about, which means if you give them what they asked for, they're still mad! So you can't
react to anger by being conciliatory. It doesn't fix the problem and it sometimes makes things much
worse. 

You can't ignore feedback, but complaining isn't *quality* feedback. But if you have to discount
complaining, how do you get good feedback? You get it from questions.

If four people ask you how to do something with your code, there's a knowledge transfer gap that 
only you can fix. It's sometimes something in the documentation, but more often than not, a footgun
you left. Or a disconnect where it's not obvious that two functions compose to create a feature, and
that was intentional, not just a Hyrim's Law situation.

They know something is wrong, they just don't know what or how to fix it. But if you can be honest
with yourself, you know exactly what is wrong. Some of my most popular API improvements have come
from trying to make sure I didn't get asked the same question a sixth time. 

### Five Tests To Move One Test Down the Testing Pyramid

I don't want to talk about whether Unit and Functional or Unit and Integration tests touch in the
Pyramid. That is a perspective difference between people who write libraries and people who write
services and we will never sort that out now. 

So I will simply say that if you want to move a test from tier 3 to tier 2, you are likely to
find that it takes around 5 tests to achieve the same code coverage. If you want to move down 2 
tiers, you're usually between 22 and 28 (things get a little more fuzzy the more tiers you jump in
one go), but 25 on average.

My favorite analogy about the testing Pyramid is to plumbing. The last thing a plumber does when
they do a repair or add a new fixture is, they turn on the water and make sure it comes out of one
pipe and makes it safely to the other. That's not a lot of End to End testing. The unit tests
started with Quality Control at the factory on the pipes, joints, and valves. They spot check their
work looking for leaks as they go. They don't spend all day farting around with making sure the
water comes out of the tap. If they don't ask for your signature immediately after that one E2E 
test, then it's because something went horribly wrong. So I check my materials. I check the
connections, then I check the End to End as a sanity check on everything else I've touched.

### Each Testing Tier is Eight Times Faster Than the One Above

Why would you make more tests for yourself if one would do? Well the answer is that in most 
well-designed or at least well-intentioned test frameworks, any test at one tier runs around 8
times faster than on the next tier. Back in the JUnit days, this number was closer to 10, but
across several other languages and many years, I've found 8 to be more accurate.

So if you're trying to speed up your test framework, you can get a set of tests 3/8ths faster 
by moving them down one tier. And if you jump a tier, you're looking at around a 60% reduction in 
run time. So if you start with your worst tests first, which also often exceed the Rule of 8, and
you also put a moratorium on writing more tests of the same sort, you can flatten the slope of CI 
run time increasing year over year substantially. When we are managing technical debt, we often 
ignore problems until they cross a threshold. Anything you do to reduce the slope of that line 
permanently, buys you more time in the future to think about either other technical debt or work
that will increase your Monthly Reccuring Revenue. You make the project better instead of just more
tolerable.


### If More Than 10% of the Code is 'Mine', That's Not Leadership, That's Control

This could have just as easily been at the top of the list as a 1/10th rule, but I feel this is 
a better parting thought than an opening one, so here it is at the end. 

There are parts of the code that have to work right the first time. There are parts of the code that
have to work right *every* time. That is where the critical parts of your architecture live, the
10% of the code where 90% of the worst problems are likely to happen. Your technical leadership 
should be concerning themselves with those parts **and only those parts**. If you're having to
swoop in all over the code base, you have poor separation of concerns, or you have control issues
that you need to talk to a therapist about.

The team cannot grow while you're carrying them your shoulders. They need to fly off to do their 
own things. You may not actually be saying 'no touchy!' out loud but any file where all the most
recent edits are yours will communicate that all on its own. The same way if you put dishes next
to your neurotic friend's sink and they feel the urge to immediately rearrange them, you know that
they think you 'did it wrong' and they're always going to correct you. Ain't nobody got time for
that.

I know a piece of code is done with me when other developers feel empowered to add features to it,
and they implement the feature in the same spot I would have. I have made this code sufficiently
self-explanatory than I can unclench and either let other people own it now, or declare that module
'done' and back-burner it. 

That letting go is necessary for a project to grow. Usually by the time I experience this, I've
already been fretting about where we are going to find the time and energy to deal with three other
problem areas we need to tackle next and I need the capacity freed up by letting it go. It's like
living in a small apartment. Every time I want to bring something in, I need to let something go,
or live in clutter all my days, constantly tripping over things I probably shouldn't still own.
