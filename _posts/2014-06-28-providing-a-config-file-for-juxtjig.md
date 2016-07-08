---
id: 376
title: Providing a config file for juxt/jig
date: 2014-06-28T11:56:25+00:00
author: admin
layout: post
guid: http://blog.sveri.de/?p=376
permalink: /2014/06/28/providing-a-config-file-for-juxtjig/
categories:
  - clojure
  - Computer-Mist
tags:
  - clojure
  - config
  - jig
  - resource
---
Today I was trying out:  <https://github.com/juxt/jig>
  
The configuration of jig says: <https://github.com/juxt/jig#configuration> that you have to put a config.[edn|clj] file into the &#8222;config&#8220; folder. I was trying to create config folders with a configuration everywhere, but did not succeed. However, if you look into the source code of jig you will see that jig loads the configuration from io/resource, so I had to put it into the &#8222;resources&#8220; folder of jig and instantly it worked.

Easy, isn&#8217;t it?