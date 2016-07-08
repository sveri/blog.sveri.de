---
id: 362
title: The Five + One most underrated Features of Clojure
date: 2014-05-14T18:38:55+00:00
author: admin
layout: post
guid: http://blog.sveri.de/?p=362
permalink: /2014/05/14/the-five-one-most-underrated-features-of-clojure/
categories:
  - clojure
  - Computer-Mist
  - programming
  - Web Development
tags:
  - clojure
  - clojurescript
  - datomic
  - edn
  - features
  - lighttable
  - map
  - syntax
---
1. Syntax

The clojure syntax is so easy that its possible to explain it inbetween a few minutes. Basically it boils down to:
  
Parathese open, function call and some arguments, then close the Parathenses. Like this: (+ 1 2 3 4 5).
  
Every expression returns a value and the function returns the value of the last expression evaluated.
  
Of course there are some special cases like reader macros and things. But to get started this can be enough.
  
The best thing about this is probably it&#8217;s consistency. You can rely on that scheme almost everywhere.

2. Maps

When I first got interested in clojure I was wondering why I never saw any objects, but I just moved it away and thought, hey, all the beginner tutorials just omit them. Then I went ahead and got a book about it, started to read and after almost 1/3 of the pages I started to wonder again, where are my damn objects. Give me some POJOs now, I need to store data (of course, in that time, in my mind). I opened the TOC of the book and see, nothing about POJOs.
  
Well, after thinking about it and looking more deeply, they were already there for a long time, but just not in the form that I got used to them.
  
POJOs are simply mapped by maps. And using maps in the clojure way is just fun and really, after giving it some time I am so relieved I don&#8217;t have to use POJOs anymore. Just put the data in the map and we are done:
  
(def person {:name &#8222;sveri&#8220; :age 30}). Thats it, my person object. Especially the keyword (:name and :age) syntax combined with the pure data makes this so much more readable and reasonable that its just pure joy to work with it.

3. EDN

The Extensible Data Notation (https://github.com/edn-format/edn). Readers not knowing what this is about might imagine it like JSON on Crack. EDN is used buy clojure programs to transfer data. For instance it is possible to have webservices which send and return data in edn format. This is especially cool as you can use that data in your clojure code without having to reformat or parse it again.
  
A map in clojure can be returned as an edn response and be used the same way in clojurescript. The same is valid for datomic (which I will come to in 4.). I can update datomic datoms with data in edn format, just like this.

4. Datomic

Well, I dont want to speak to much about as I have not much experience with it. But as far as I have used it it&#8217;s just awesome. I am writing this from a developers point of view. Using the datomic api is just nice and simple, if you grasp the points that datomic makes about it&#8217;s usage. There is a lot of documentation and screen casts available, and if I had a wish it would be nice if more of this tutorials directly target the clojure usage of datomic. However, again, being able to retrieve data from datomic and pass it to through my backend to my frontend clojurescript and still being able to use them as if it were clojure data structures is just awesome.

5. The clojure stack

Of course one might reason about what this stack is. For me this currently are a few libraries evolving around clojure.
  
Namely I use:
  
Clojure (of course)
  
Clojurescript
  
om
  
core.async
  
Datomic
  
Leiningen
  
And a lot of other small libraries which I cannot mention because they are so easy to forget about as they just work.
  
Using all these libraries seemse like a fresh breeze, especially the easyness of integration into products. The fact that the documentation is almost always to the point and that the code is very readable makes programming just fun again.

Of course this all has to be taken as a very subjective post, however, reading about clojure I seldom find these topics mentioned, but I believe they are part of the great experience that one has working with this stack.

And again, just to repeat myself. As I found out how easy it is to send some web formular data over the wire into datomic with just a few lines of code I could have cried. Never in my life I was done so fast with a task that seems so hard and filled with boilerplate in different languages / frameworks (Just think about GWT and its DTOs and DAOs and factories and wrappers&#8230; Disclaimer, it&#8217;s been some time since I worked with GWT).

5 + 1.

I almost forgot about this one, just like most of the other entry points for clojure do.
  
Lighttable (http://www.lighttable.com/). Lighttable is an insane IDE, not by the editor features, but by the possibility to instantly see changes that you make to your code.
  
You can start a clojure repl inside an editor (your clojure file) and see the output that your functions and function calls generate, instantly.
  
That&#8217;s something I have never seen before and the first time I saw it I knew, ok, I never want to miss such a feature again. Of course, working daily with JAVA I feel the pain again and again, but, maybe thats subject to change some day.
  
If you don&#8217;t know what a repl is just watch some videos about Lighttable and see the aweomeness for yourself.
  
Or, just download it and start using clojure today.