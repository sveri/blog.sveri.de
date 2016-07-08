---
id: 287
title: eclipse juno, maven, spring 3 and deployment to tomcat
date: 2012-08-15T07:48:04+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/?p=287
permalink: /2012/08/15/eclipse-juno-maven-spring-3-and-deployment-to-tomcat/
categories:
  - Computer-Mist
  - Web Development
tags:
  - ClassNotFoundException
  - eclipse
  - maven
  - spring
  - tomcat
---
Hi,

i recently tried the above combination for a prototype and all of a sudden the following error appeared:
  
[codesyntax lang=&#8220;java5&#8243;]

<pre>Schwerwiegend: Error configuring application listener of class org.springframework.web.context.ContextLoaderListener
java.lang.ClassNotFoundException: org.springframework.web.context.ContextLoaderListener
	at org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoader.java:1711)
	at org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoader.java:1556)
	at org.apache.catalina.core.DefaultInstanceManager.loadClass(DefaultInstanceManager.java:532)
	at org.apache.catalina.core.DefaultInstanceManager.loadClassMaybePrivileged(DefaultInstanceManager.java:514)
	at org.apache.catalina.core.DefaultInstanceManager.newInstance(DefaultInstanceManager.java:133)
	at org.apache.catalina.core.StandardContext.listenerStart(StandardContext.java:4727)
	at org.apache.catalina.core.StandardContext.startInternal(StandardContext.java:5285)
	at org.apache.catalina.util.LifecycleBase.start(LifecycleBase.java:150)
	at org.apache.catalina.core.ContainerBase$StartChild.call(ContainerBase.java:1559)
	at org.apache.catalina.core.ContainerBase$StartChild.call(ContainerBase.java:1549)
	at java.util.concurrent.FutureTask$Sync.innerRun(Unknown Source)
	at java.util.concurrent.FutureTask.run(Unknown Source)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(Unknown Source)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(Unknown Source)
	at java.lang.Thread.run(Unknown Source)</pre>

[/codesyntax]

It took me some time to figure out what happened, but somehow my project settings changed.
  
To fix this error go to projects properties  -> deployment assembly and add the maven dependencies there to be mapped to WEB-INF/lib.

That&#8217;s it, quick fix for a weired thing like change of the settings -.-