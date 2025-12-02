---
layout: post
title: "Passive Testing"
topics: [ Development, DX, Testing, Tools ]
excerpt: "Thoughts on multi-device testing"
---

<figure>
  <img class="operator" src="/assets/images/blog/operator.png" width="400px"/>
  <figcaption>You get used to it. I don’t even see the code.</figcaption>
</figure>

I have wanted a deskful of monitors since I first discovered that such a thing was technologically
possible. I gave up on that idea for a while, but I think it will finally happen. I never would have
guessed that this would be the way.

We all know the workstation market is shrinking, and that in the computer industry marginalized
products become expensive products. We as developers are already collectively moving to laptops,
which don’t have the oomph of a workstation, even with the nearly-obligatory SSD. Laptops are
expensive, and can’t have many monitors attached. In a work environment you’ll probably get one,
possibly two. Even if they offered you a third you wouldn’t be able to use it.

Divide and Conquer tactics have already becoming pretty common, in the form of Continuous
Integration. You get one or two wicked fast machines, you divide all your tests up into chunks that
are likely to fail or pass in some pleasing order, and you run them on every commit. With tools like
‘watch’ or the ‘auto-test’ button (Jetbrains), this is beginning to expand back to your desk, but I
think we can do better.

If you do web apps, think about your code-build-test cycle. It’s probably a bit like mine:

1. Think about which page is most affected by the change I’m planning to make.
1. Open it in a bunch of browsers.
1. Make a change to my code.
1. Start the unit tests.
1. Alt-Tab between all the browsers
1. Hit reload
1. Poke at it
1. Did I remember to reload?  Better poke it again to be sure
1. Fix a quirk in IE a browser that’s having problems
1. Rerun the tests
1. Start a commit message
1. Realize/suspect that I forgot a browser
1. Repeat steps 5-10
1. Realize I forgot to check if it works on the other page.
1. Repeat steps 1-13 on other page
1. Fix another IE browser issue
1. Commit
1. Fix a test I broke because I forgot to rerun the tests after step 16

There is only one word for this process: stupid.

If I could blame it on one person I would, but the fact of the matter is that every one of us has
independently or with a little gentle prodding come to this very same development cycle. We are
all (and none) of us to blame. It’s just how things are. Since we understand that it sucks so very
much, we write a bunch of test automation to make step 7 less arbitrary, error-prone and onerous,
but what about all those other steps!?

If you think about it, that’s a awful lot of clicking, and a lot of time wasted on forgetfulness.
It’s an exceedingly interactive form of testing, and this is probably the same observation that
underpins Lighttable. In their tool you have your code running right next to your editor, and you
can just glance over at it whenever you want. In fact it’s kind of hard to avoid looking at it,
which is the point.

It’s a really cool idea, but IDEs require extensive feature sets to reach parity with what we
already use. Namely, what will this piece of code look like in four different browsers? How would
you event display that in Lighttable? Typically it’s taken tool vendors 6-10 years to reach the kind
of feature parity that would make someone dump their existing IDE. I’m impatient, so let’s try
something else. Something more passive, and low-tech.

On top of the steps above, OOCSS actually makes this situation a lot worse, as I mentioned before,
because ‘the most affected pages’ is less likely to be 1-3 and more likely to be 3-6 (I would be
happy to explain this later, if anyone cares to see my notes). But if we go with a more passive
approach, all of this evaporates in a puff of tooling.

So here is my proposed model.

Earlier in the development process:

1. Identify functional areas that are expected to ‘work the same’
1. Generate a fake ‘portfolio’ page filled with page fragments representing all of these areas
1. Populate it with as many corner cases as fit (long text, Unicode, escaped html, etc)
1. Put a <meta> refresh header in the top of the fake page.
1. Optionally add a button to disable the refresh.
1. Tuck it away someplace in the project that will be omitted from the production builds
1. Commit

Now when a new feature or bug fix needs to happen:

1. Tweak the relevant portfolio page to express the behavior change.
1. Open it in a bunch of browsers.
1. Make a change to your code.
1. Start the unit tests.
1. Alt-Tab between all the browsers
1. Poke at it
1. Fix a quirk in IE a browser that’s having problems
1. Rerun the tests
1. Start a commit message
1. Realize you forgot a browser
1. Repeat steps 5-8
1. Have enough energy left (hopefully) to remember to rerun the tests
1. Commit

We’ve moved a big chunk of muscle memory out of the code-build-test loop. This is a good thing. An
excellent thing in fact, because we are human and we make mistakes all the time. However you may be
thinking to yourself, “hey, he promised me The Matrix at the top of this post,” and I haven’t done
anything about that yet. So here goes:

Most of the time you don’t even need step 6 (ie, poke at it). You can just visually verify that
everything still looks good. So all you have to do is arrange your browsers so you can glance at
them all without lifting a finger – passively.

If you plug your tablet in and set it not to go to sleep, then you can test that as well, and now
you have 4+ screens in front of you. If you can find a Windows box or another laptop, or an older
tablet (and who among us doesn’t have those now?) it goes up from there, until you run out of desks,
jacks, or outlets.

If anyone tries this out, or has already come to this same conclusion, I’d love to get some feedback
on your experiences.

PS:

I’m trying to get a pull request into Jasmine to add a refresh button for your JS tests, I’m using
this to short-circuit more of the code-build-test cycle. If you like and use Jasmine, please give my
pull request an upvote, or try it yourself and let me know if it works for you.
