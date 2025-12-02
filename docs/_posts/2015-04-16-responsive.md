---
layout: post
title: "Rethinking Responsive Design"
topics: [ Development, Responsive ]
---

We know that these days a lot of our users are trying to access our websites from their phones. They
may need some information, or they may just be bored and stuck somewhere that they don’t have a
larger screen. We also know that a lot of the rest of our users are on tablets, or laptops. We also
know that for some of us, how our designs look on projectors matters (which are limited in contrast
in addition to real estate). We’ve been designing our little hearts out trying to make our websites
“responsive”, and today a lot of the Web looks pretty good at 640 and 1024 pixels wide. It’s been a
lot of work and everyone who has pulled it off deserves to be a little proud of themselves. I say “a
little proud” because we’re completely dropping the ball in other areas of responsiveness. 

What we don’t seem to know at all is that people also have desktop computers with really big 
displays. Really, truly, mind-bogglingly big displays. So here’s a pretty uncomfortable situation: 
my secondary monitor is 1920 pixels wide. The one that isn’t good enough to be in front of my face
anymore. The hand-me-down. Today you can get giant panels that are 4000 pixels or even 5000 pixels
wide. Even if you use scaling that’s a 2000 -2500 pixel wide screen for high end users. I’m slumming
at a mere 2500 pixels myself, with no scaling. I have expensive hobbies and I thought The Nature
Conservancy needed the money more than I needed a bigger monitor. And besides, it wouldn’t fit on my
desk anyway. Sadly, with very few exceptions, the websites I visit don’t seem to make any use at all
of a screen wider than about 1000 pixels. A few appreciate a little elbow room and top out at about
1100 or 1280pixels, but most stop there. Meanwhile, some don’t even get to 1000 pixels. This is the
Daring Fireball website: 

<img src="/assets/images/blog/screen-shot-2015-04-16-at-10-32-50-pm.png"/>

That’s what it looks like maximized on my screen. Let me be clear: I’m not picking on DF. Their 
layout is what inspired me to finally commit some ideas to paper, but this has been bugging me for a
while. The project tool I worked on back in ’12 looked just terrible above 1400 pixels, and we 
couldn’t really come up with anything to do with that space. And that was knowing at the time that
[Nielsen was suggesting you tune your site for 1440 pixels](http://www.nngroup.com/articles/computer-screens-getting-bigger/).
And of course in all fairness, if you look at my blog on my monitor, it looks like this, which I 
confess is only marginally better than DF:

<img src="/assets/images/blog/screen-shot-2015-04-16-at-10-44-47-pm.png"/>

The management and editor views make a little more use of the space, but only a little: 

<img src="/assets/images/blog/screen-shot-2015-04-16-at-11-05-01-pm.png"/>

What happened? We were in a Dark Age of 1000 pixel wide site design when Mobile First and Responsive
Design became common practice, and here we are several years later and the entire web is 1000 pixels
wide – even parts that worked at 1200+ pixels previously. Google has gotten narrower than ever. I
was a little shocked when I actually bothered to check. Are you sitting down? Even though it’s
supposedly 980 pixels wide, the actual content only fills 512 pixels. Google search results are five
hundred and twelve pixels wide, today, in 2015. If these examples are not the very literal
definition of regressing, I don’t know what is.

I can fit two websites side by side on my desktop without losing anything from my web browsing 
experience. In fact there are plugins for Firefox and Chrome that let you show two tabs side by side
in a single window. I can do this thing, but with the exception of some chat windows at work, I 
really shouldn’t have to do this. Certainly we can do better than this, can’t we? At least, I think
we can.
