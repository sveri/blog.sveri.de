---
id: 249
title: twitter bootstrap 2.0.2 broke play 2.0 support
date: 2012-04-05T22:57:29+00:00
author: admin
layout: post
guid: http://blog.sveri.de/?p=249
permalink: /2012/04/05/twitter-bootstrap-2-0-2-broke-play-2-0-support/
categories:
  - Computer-Mist
  - play framework
  - Web Development
tags:
  - bootstrap
  - play
  - twitter
---
I just tried to get the twitter bootstrap lib running with play 2.0, but received an error, irc guys told me that the new twitter bootstrap broke the play support. This is the message:
  
_EcmaError: TypeError: Cannot call method &#8222;charAt&#8220; of undefined (less-1.2.1.js#338)_

I worked around it by using the 2.0.1 of bootstrap, the nice guy at the irc told me that the git version of play has it fixed already.

Btw. there is a nice and short tutorial to get bootstrap running with play:
  
[https://plus.google.com/u/0/108788785914419775677/posts/QgyUF9cXPkv](https://plus.google.com/u/0/108788785914419775677/posts/QgyUF9cXPkv "bootstrap play tutorial")