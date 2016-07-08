---
id: 317
title: Using Lift with lift-shiro
date: 2013-09-12T19:18:55+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/?p=317
permalink: /2013/09/12/using-lift-with-lift-shiro/
categories:
  - Computer-Mist
  - programming
tags:
  - lift
  - lift-shiro
  - noclassdeffound
  - shiro
---
I currently try to use lift 2.5 with lift-shiro (https://github.com/timperrett/lift-shiro). It works basically, however as soon as you try to to use sha256 encoding like this:
  
[main]
  
sha256Matcher = org.apache.shiro.authc.credential.HashedCredentialsMatcher
  
sha256Matcher.hashAlgorithmName=SHA-256
  
iniRealm.credentialsMatcher = $sha256Matcher

an error occurs like this:
  
java.lang.NoClassDefFoundError: org/apache/commons/collections/FastHashMap

So obviously there is a dependency missing. Adding these two lines:
  
&#8222;commons-collections&#8220; % &#8222;commons-collections&#8220; % &#8222;3.2.1&#8220;,
  
&#8222;commons-logging&#8220; % &#8222;commons-logging&#8220; % &#8222;1.1.3&#8220;,
  
to the build.sbt resolves the missing dependencies.