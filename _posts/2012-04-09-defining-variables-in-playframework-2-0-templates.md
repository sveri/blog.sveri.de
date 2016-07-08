---
id: 261
title: defining variables in playframework 2.0 templates
date: 2012-04-09T14:59:47+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/?p=261
permalink: /2012/04/09/defining-variables-in-playframework-2-0-templates/
categories:
  - Computer-Mist
  - play framework
  - Web Development
tags:
  - 2.0
  - define
  - java
  - play framework
  - template
  - variable
---
Today i found out how to define variables in play&#8217;s templates. I would say play does not go the common way, instead it uses a functional approach. So to define a new variable you have to do something like:

[codesyntax lang=&#8220;html4strict&#8220;]

<pre>@defining(User.getLoggedinUser()) {user =&gt;
  &lt;h1&gt;hello @user.getName(), @user.getPrename()&lt;/h1&gt;
}</pre>

[/codesyntax]

So basically the variable _user_ references to the result of _User.getLoggedinUser()_, which is an object in this case and can only be used in the defined scope of the _{}_.

&nbsp;