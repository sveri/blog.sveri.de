---
id: 352
title: 'Clojurescript ending with &#8222;.cljs&#8220; miss source maps'
date: 2014-04-17T10:53:03+00:00
author: admin
layout: post
guid: http://blog.sveri.de/?p=352
permalink: /2014/04/17/clojurescript-ending-with-cljs-miss-source-maps/
categories:
  - clojurescript
  - Computer-Mist
  - programming
tags:
  - bug
  - cljs
  - map
  - missing
  - namespace
  - source
---
I found my first clojurescript bug yesterday. The problem is tricky, but for a experienced programmer it should have been more obvious.

When a clojurescript namespace ends with &#8222;.cljs&#8220; and you have optimizations set to :none the source mappings are not generated correctly resulting in the fact that you wont see them at all in google chrome.

This is the bug: [http://dev.clojure.org/jira/browse/CLJS-799](http://dev.clojure.org/jira/browse/CLJS-799 "CLJS-799")