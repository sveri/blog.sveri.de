---
id: 328
title: Debug luminus (clojure ring) application
date: 2013-10-26T16:46:41+00:00
author: admin
layout: post
guid: http://blog.sveri.de/?p=328
permalink: /2013/10/26/debug-luminus-clojure-ring-application/
categories:
  - Computer-Mist
  - programming
tags:
  - clojure
  - debug
  - luminus
  - ring
  - windows
---
Today i wondered how hard it might be to debug a luminus webapp. Turns out, as its java, its as easy as always.

Just set the JAVA_OPTS (under windows):
  
set JAVA\_OPTS=-Xdebug -Xrunjdwp:transport=dt\_socket,server=y,suspend=n

And then start as usual with:
  
lein ring server

Afterwards you can connect in eclipse or intellij via the remote debug option. Thats it 🙂