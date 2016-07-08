---
id: 383
title: prismatic schema vs. core.typed
date: 2015-01-19T12:46:26+00:00
author: admin
layout: post
guid: http://blog.sveri.de/?p=383
permalink: /2015/01/19/prismatic-schema-vs-core-typed/
categories:
  - clojure
  - Computer-Mist
  - programming
tags:
  - clojure
  - core.typed
  - prismatic schema
---
The best explanation for this I have got was cflemings one on IRC:
  
<span style="font-size: small;"><span style="color: #af7f00;">(11:42:55) </span></span>cfleming: sveri zilti: One major difference is that core.typed validates your code, schema validates your data. If you&#8217;re dealing with data exclusively created and manipulated by your code, core.typed is a good solution. If you&#8217;re validating data from an external source, you need schema.
  
<span style="font-size: small;"><span style="color: #af7f00;">(11:43:57) </span></span>cfleming: sveri zilti: core.typed can validate that your functions only ever create data of a particular shape, but cannot validate that arbitrary data complies to that shape.

I just write it down here to have a place where I can look again in some months.