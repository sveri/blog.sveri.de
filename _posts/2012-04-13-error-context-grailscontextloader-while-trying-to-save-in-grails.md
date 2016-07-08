---
id: 275
title: ERROR context.GrailsContextLoader while trying to save in grails
date: 2012-04-13T16:28:57+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/?p=275
permalink: /2012/04/13/error-context-grailscontextloader-while-trying-to-save-in-grails/
categories:
  - Computer-Mist
  - grails 2
  - Web Development
tags:
  - grails 2
  - grailscontextloader
  - save error
---
If you get the error:
  
_ERROR context.GrailsContextLoader  &#8211; Error executing bootstraps: null_
  
_Message: null_
  
while trying to save something in grails 2, go ahead and make use of the nice: _failOnError_ option the save method gives you ([http://grails.org/doc/2.0.x/ref/Domain%20Classes/save.html](http://grails.org/doc/2.0.x/ref/Domain%20Classes/save.html "grails save method")).

It will produce a much better output regarding what is wrong, in my case it showed me that i forgot to set a needed variable in my class before i tried to save it.

A nice guy in the mailing list pinpointed me to this one (<http://grails.1312388.n4.nabble.com/Error-executing-bootstraps-null-with-springsecurity-plugin-td4554560.html>).