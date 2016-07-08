---
id: 243
title: spring roo web gwt setup maven error
date: 2012-04-04T20:13:09+00:00
author: admin
layout: post
guid: http://blog.sveri.de/?p=243
permalink: /2012/04/04/spring-roo-web-gwt-setup-maven-error/
categories:
  - Computer-Mist
  - Web Development
tags:
  - error
  - gwt
  - maven
  - spring roo
---
Today i tried to get a sample project with springsource tool suite, spring roo and gwt running.
  
If you follow the tutorials you finally reach a step where you have to enter:
  
[codesyntax lang=&#8220;bash&#8220;]

<pre>web gwt setup</pre>

[/codesyntax]

After that one you will have an error in your project which you can see under markers:
  
[codesyntax lang=&#8220;bash&#8220;]

<pre>Plugin execution not covered by lifecycle configuration: org.codehaus.mojo:exec-maven-plugin:1.2:exec (execution: default, phase: process-classes)</pre>

[/codesyntax]

I know almost nothing about that maven thing, and the internet in that case does not point to the right solution at first, but finally i found it on the spring forums: <http://forum.springsource.org/showthread.php?116544-Can-t-compile-with-GWT-2.4&p=385963&highlight=#post385963>

It says you have to insert:
  
[codesyntax lang=&#8220;xml&#8220;]

<pre>&lt;pluginManagement&gt;
        &lt;plugins&gt;
            &lt;!--This plugin's configuration is used to store Eclipse 
                m2e settings only. It has no influence on the Maven build itself. --&gt;
            &lt;plugin&gt;
                &lt;groupId&gt;org.eclipse.m2e&lt;/groupId&gt;
                &lt;artifactId&gt;lifecycle-mapping&lt;/artifactId&gt;
                &lt;version&gt;1.0.0&lt;/version&gt;
                &lt;configuration&gt;
                    &lt;lifecycleMappingMetadata&gt;
                        &lt;pluginExecutions&gt;
                            &lt;pluginExecution&gt;
                                &lt;pluginExecutionFilter&gt;
                                    &lt;groupId&gt;org.codehaus.mojo&lt;/groupId&gt;
                                    &lt;artifactId&gt;exec-maven-plugin&lt;/artifactId&gt;
                                    &lt;versionRange&gt;[1.2,)&lt;/versionRange&gt;
                                    &lt;goals&gt;
                                        &lt;goal&gt;exec&lt;/goal&gt;
                                    &lt;/goals&gt;
                                &lt;/pluginExecutionFilter&gt;
                                &lt;action&gt;
                                    &lt;execute /&gt;
                                &lt;/action&gt;
                            &lt;/pluginExecution&gt;
                        &lt;/pluginExecutions&gt;
                    &lt;/lifecycleMappingMetadata&gt;
                &lt;/configuration&gt;
            &lt;/plugin&gt;
        &lt;/plugins&gt;
    &lt;/pluginManagement&gt;</pre>

[/codesyntax]
  
in your pom.xml. Between the <build> tags, but not inside the <plugins> tags.
  
After that you have to right click your project in sts, go to maven -> update project configuration and select your project.

That&#8217;s it, the error is gone. And dont forget to save 😉