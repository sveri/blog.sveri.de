---
id: 271
title: play 2.0 formbind validation exception
date: 2012-04-11T20:19:19+00:00
author: admin
layout: post
guid: http://blog.sveri.de/?p=271
permalink: /2012/04/11/play-2-0-formbind-validation-exception/
categories:
  - Computer-Mist
  - play framework
  - Web Development
tags:
  - 2.0
  - formbind
  - getter
  - play framework
  - setter
  - validationerror
---
If you get the following error: _[ValidationException: Call to TraversableResolver.isReachable() threw an exception]_ when you try to do a formbind with play 2.0 framework:
  
_Form<Task> tasks = taskForm.bindFromRequest();
  
_ Then you should check if your class _Task_ has getters and setters for the variables you need, the springbind library play relies on needs them to work._
  
_