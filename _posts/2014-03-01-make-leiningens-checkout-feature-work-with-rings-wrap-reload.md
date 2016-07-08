---
id: 344
title: Make leiningens checkout feature work with rings wrap-reload
date: 2014-03-01T16:49:04+00:00
author: admin
layout: post
guid: http://blog.sveri.de/?p=344
permalink: /2014/03/01/make-leiningens-checkout-feature-work-with-rings-wrap-reload/
categories:
  - Computer-Mist
  - programming
  - Web Development
tags:
  - checkouts
  - clojure
  - ring
  - wrap-reload
---
Using leiningens checkout feature is pretty cool. You can split your application into some modules and still retain the development workflow.
  
However, when you are running a ring application the hot code reloading wont work out of the box. For this you have to add the extra source paths to the wrap-reload method (generated in core.clj when using luminus).
  
Mine looks like this:

(if (dev? args) (reload/wrap-reload app {:dirs [&#8222;src&#8220; &#8222;checkouts/subproject/src&#8220;]}) app)

In the :dirs value you can add us much paths as you want and the ring middleware will keep watching the changes there.