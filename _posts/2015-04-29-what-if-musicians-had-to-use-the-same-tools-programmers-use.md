---
id: 395
title: What if musicians had to use the same tools programmers use
date: 2015-04-29T15:14:46+00:00
author: admin
layout: post
guid: http://blog.sveri.de/?p=395
permalink: /2015/04/29/what-if-musicians-had-to-use-the-same-tools-programmers-use/
categories:
  - Allgemein
  - clojure
  - programming
tags:
  - clojure
  - musicians
  - programming
  - silver bullet
  - tooling
---
As most people do, I like listening to music and in the age of youtube it happens from time to time that listenting to music also means watching music. So someone suggested me to have a look at Niels Frahm, which I did and liked, especially in his live acts, so I came across a set from October 2014. Some time goes by and he is playing the piano and all of a sudden a guy joins him and they start a duett (If you&#8217;re interested, the piano part starts here: [https://youtu.be/YniiDC0J_7k?t=53m59s](https://youtu.be/YniiDC0J_7k?t=53m59s "https://youtu.be/YniiDC0J_7k?t=53m59s")). After they are done he explains how that came.
  
In short he says he met the guy a day before on some kind of a party, heard him playing a piano and asked him to play one piece in D-Minor together the next evening, without practicing, just playing.

That was the moment I felt some sort of enlightment. I was asking myself, how would it be if two coders met and said, hey, I code tomorrow for some guy here, do you wanna join me for an hour. And he says yes, of course. Ah, we don&#8217;t need to practice, we just enjoy coding some time.
  
So the next day he comes over, takes his computer device next to him and sees him code, ah, yea, that looks good. What is the svn / git uri? Is that java?
  
Yea, it is, JDK5 indeed, we are coding for a legacy system running on some old device no one ever heard about. All you have to do is install that VM here, oh, its a VMware image, you cannot use Virtualbox for that and yea, you need access to the the companies source control. Wait, I just have to change the access rights here, ah, no, you need a login or what so ever.
  
Well, I guess you get the idea. One month later after everything is setup and running both guys code together a nice short algortihm which fixes some performance problems they had under special circumstances in like one hour.

Now, try to think of it the other way around. Imagine the musician would have to use a computer while he is on stage (Yea, I know modern DJs use software to produce sound, but that&#8217;s not the comparison I want to draw here). Imagine he would run a mix of gradle and ant on his &#8222;music device&#8220; running on a windows system within a virtual machine and imagine he wants to start his show and then, whups, sorry, I have to reboot, updates are incoming.
  
One might say this is ridicoulus, this should not happen, this is made up, but wait. In germany there is a basketball team that may have to get into a league below because they &#8222;lost&#8220; a game because the game started 25 minutes to late whereas the maximum delay allowed by the rules are 15 minutes. Guess where the 25 minutes came from? Windows update on a computer that they needed for the game, no joke, here is the link (german newspaper, sry) [http://www.zeit.de/sport/2015-03/basketball-paderborn-windows-update-abstieg.](http://www.zeit.de/sport/2015-03/basketball-paderborn-windows-update-abstieg "http://www.zeit.de/sport/2015-03/basketball-paderborn-windows-update-abstieg")

Now, where were we? Right, the musician entertaining his crowd while he waits for his &#8222;music instrument&#8220; to reboot. Maybe he tells some Microsoft jokes.
  
Then, when it is finally up he can start playing, great, but, in the middle of the set when he wants to &#8222;build&#8220; his improvised tune some weird error occurs causing some missound and complaining about a &#8222;tune not found exception&#8220;. Well, it never occurred before he swears to his crowd, hectically trying to fix that damn exception or just playing a different tune. I guess you are getting the idea here too.

What do I want to say here? I learned a lot about programming languages in the last years, patterns, refactoring, functional programming, event sourcing, haskell type system, akka and the actor pattern and what not more.
  
The common thing about what I learned is that these are all principles related to the implementation work of a programmer.

Now, at work I may code like 2 &#8211; 5% of all my time I am there. This is not because I am lazy, but that I work on a part of a larger suite with probably 200 &#8211; 300 components and several teams working on them.
  
This obv. causes a very large code base with a very **mixed** landscape with dozens of different tools used around the place.
  
So everything basically fails often, servers take time to restart. Build systems have to be upgraded. Reinstalling the whole suit happens maybe once a week, taking 2  to 3 hours.
  
So, when it comes to coding the business logic I am usually done in a short amount of time and then back to the whole ecosystem. Again you may get the idea.

So what am I doing at work. I fight the tools we have. I fight gradle, I fight ant, I fight OSGi, I fight the server our product runs on, I fight the mistakes other teams, we are depending on, make (don&#8217;t get me wrong, mistakes are part of a developers life, I make them too all the time), still, mistakes keep others from &#8222;working&#8220;.

Then I was thinking of the &#8222;Are we there yet?&#8220; talk Rich Hickey gave: [http://www.infoq.com/presentations/Are-We-There-Yet-Rich-Hickey](http://www.infoq.com/presentations/Are-We-There-Yet-Rich-Hickey "http://www.infoq.com/presentations/Are-We-There-Yet-Rich-Hickey"). And again it occured to me, well, everybodys talking about the languages. But, they are not my problem. My problem is the tooling.
  
And asking &#8222;are we there yet?&#8220; regarding tooling I think we are as far away as the sun is from the earth. Sometimes things are so frustratingly complex, take so much time to debug, to make it work at all. Well, you get the idea again.

I don&#8217;t have a solution for this obviously and if I had I would sell it and get rich instead of writing a blog post. However, when reading about the &#8222;go&#8220; language I always heard of it&#8217;s good tooling. Maybe I peek in there and see what it has to offer.

Aside from that I think there needs to be a radical change in how we work from day to day and from the whole universe of different tools we use as long as they are &#8222;broken&#8220; and limited as they are (or maybe they are to complex and should be even more limiting?).
  
There is a need for something completely new, something different from what we have.
  
And if that happens, maybe that will be the &#8222;silver bullet&#8220; everyone is looking for since the [http://en.wikipedia.org/wiki/Software_crisis](http://en.wikipedia.org/wiki/Software_crisis "Software Crisis")

And yes, I am aware that the tools we use are just software too, maybe that&#8217;s part of the problem. Maybe we should build software like hardware. What about a tool that is the complete equivalent to a guitar and how would you make sure that it is exactly that?