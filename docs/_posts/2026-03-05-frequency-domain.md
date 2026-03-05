---
layout: post
title: "Errors Should be Reasoned About in the Frequency Domain"
topics: [ Development, DX, Growth ]
excerpt: "Users have a very different perception of problems than what we see in our dashboards."
---

    The customers with the slowest requests are often those who have the most data on their 
    accounts, because they have made many purchases. That is: they're the most valuable customers.
    It's important to keep those customers happy, by ensuring the website is fast for them.
    
    -- Designing Data-Intensive Applications

Users have a very different perception of how things are going than we do, and this gap can lead to
priority inversions and disgruntled ex-users.

## The Frequency Domain

I started thinking on this subject after I saw a team get yelled at by a customer representative
about how 'this always happens'. As I was helping someone with the clusterfuck in progress, I was
taking mental notes for the Root Cause Analysis meeting that would surely follow, as I often do.

Several bad things were going on at once. First, and most important, someone was promising features
to be done on the next deployment cycle after we anticipated the work to be done. This is never a
good idea, and of course the person yelling was the person who made this promise in the first place.
But the other was that we had a glitchy build process, and that process was part of our testing and
deployment process. It usually glitched every few weeks but right now it was about to glitch
for the third time in a row.

As my boss was calmly explaining how it was bad luck and actually only happened about once a month,
I realized that they both had a point, and this was exactly the sort of stuff I was brought in to
fix, it was just in the middle of a very large pile I was still working through.

For a User, if they can distinctly recall the last time a problem happened, that's a pretty big
issue. If they can recall the last several times, that's an issue that's getting bigger. And if
a clump of incidents occur, then their perception may flip to the problem happening 'all the time'
and then the next time it happens (incident, or cluster), then they will get very upset about it.

## Statistical Clustering

World of Warcraft (WoW) famously broke their Random Number Generator to answer complaints from
frustrated players. In games like WoW, much of your participation in the game world is a series of 
quests that move you along a story arc. That sort of story writing is expensive work, and too much
story can end up gatekeeping later parts of the game by blocking players from progressing at all,
so filler quests are meant to keep you active and busy between the beats of the main story line(s).

Your next task then, three times out of four, is to collect items from unimportant creatures ('trash
mobs'). And to pad out the plot even further, rather than putting one item on each mob, they use a
random number generator to put between 0 and 2 on each creature so that you hopefully have to kill
12 of them to get the 6 items you have been asked to procure. 

Most of us will think of it the way WoW clearly did: Each event has a 50% chance of something good 
happening. But in reality what happens is that there's a 50% chance of something bad happening, a 
25% chance of it happening twice in a row, a 12.5% chance of it happening 3 times in a row, and so
on. You get to almost 7 times in a row before your odds go below 1%, which is still a huge problem,
when you have over 10 million subscribers, doing half a dozen of these types of quests per day, and 
sometimes in two or three playthroughs at the same time. Soon everyone has a story of needing 40 
minutes to finish a task that was meant to take 6-8 minutes, and a loud minority have five, and are
rage quitting. Or inciting their friends to quit with them.

They solved this problem by cheating - the more consecutive times you failed, the higher the 
probability of success on the next attempt. The correct solution would have been determinism, to 
remove the loot box effect entirely, either by making all kills drop the sought after items, or 
by populating the map with a fixed number of mobs that had the item and a fixed number that did not,
so that the quest was repeatable by everyone. Instead they made the Gambler's Fallacy true - you 
could not in fact roll snake eyes 20 times in a row. 

Nobody outside of games can use this solution though. The best we can do is like Amazon, measuring
internal teams by p999 times, which still allows these statistical clusters to happen, particularly
when fanout occurs. [Goodhart's Law](https://en.wikipedia.org/wiki/Goodhart%27s_law) kicks in and 
we "Make the Numbers Go Up" without actually doing anything about customer satisfaction.

## Birthday Paradox

Even more than just statistical clustering, anecdotes about outlier cases tend to follow the 
Birthday Paradox. The Birthday Paradox says that in a room full of people, the odds of two of them
sharing the same birthday are about 4 times higher than your instincts tell you the number should 
be. If two people you know had the same bad experience with a piece of software, that might put you
off even trying it. Or it might encourage you to quit as well, in solidarity. 

## Scaling

I've always suspected that the Right Way to get people to use a tool more is to first make it less 
error-prone. The situation I described above felt like proof of this feeling, and once I sat with
that realization, it was easy to see a pattern going back as far as I cared to look. 

My first priority then, when tasked with making a process or tool more popular, is to debug it. If
the goal is doubling the usage of a tool or feature, I first attempt to reduce the expected 
error rate by a factor of 4 (2x2). It takes away an excuse to avoid using it, it validates the 
reasons people have been avoiding it in the past, and it provides an enticement to start using it
now. Particularly if the new version is now categorically less error-prone than doing the task by
hand. But from a social contract standpoint, if people start using something more and the error 
rate goes up, then it will make your efforts look bad. See? Things are breaking now because we are
using this thing (more)! We should go back to sticks and rocks! Change Bad!

The 2x rule of thumb means that if I miss on that target, or underestimate the increase in 
popularity of the tool, we may still go from a bad issue once a month to once every six weeks. But
if we hit our numbers the error rate drops by half, which also sets us up to succeed on the next
such initiative. Usage went up and nothing bad happened. What else can we fix?

