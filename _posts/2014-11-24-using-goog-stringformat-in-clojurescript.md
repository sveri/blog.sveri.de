---
id: 380
title: Using goog.string/format in clojurescript
date: 2014-11-24T19:14:33+00:00
author: admin
layout: post
guid: http://blog.sveri.de/?p=380
permalink: /2014/11/24/using-goog-stringformat-in-clojurescript/
categories:
  - Computer-Mist
  - programming
tags:
  - clojurescript
  - format
  - goog.string.format
  - number
---
When I tried to format a string with googles closure library there was a surprising result. This code:
  
[codesyntax lang=&#8220;java&#8220;]

<pre>(ns foo
  (:require [goog.string :as gstring])))
  
(gstring/format "%.2f MB" 1000000)  
</pre>

[/codesyntax]
  
produces this error:
  
Uncaught TypeError: Cannot read property &#8218;call&#8216; of undefined

To resolve this issue just add this line to your require statement: [goog.string.format]. Whyever that is&#8230;