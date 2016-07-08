---
id: 311
title: Using scalastyle in the gradle build
date: 2013-07-07T14:30:53+00:00
author: admin
layout: post
guid: http://blog.sveri.de/?p=311
permalink: /2013/07/07/using-scalastyle-in-the-gradle-build/
categories:
  - Computer-Mist
  - programming
tags:
  - build
  - gradle
  - scala
  - scalastyle
---
As there seems to be no documentation available about how to use scalastyle ([http://www.scalastyle.org/](http://www.scalastyle.org/ "scalastyle")) with gradle i figured it out myself, which is not that hard. This is the snippet you have to use:
  
[codesyntax lang=&#8220;groovy&#8220;]

<pre>repositories {
    maven {
        url "https://oss.sonatype.org/content/repositories/snapshots"
    }
}

dependencies {
    compile "org.scala-lang:scala-library:2.10.1"
    compile "org.scalastyle:scalastyle-batch_2.10:0.3.2"
}

task scalastyle &lt;&lt; {
    javaexec {
        main = 'org.scalastyle.Main'
        classpath = sourceSets.main.runtimeClasspath

        ext.configDir = 'src\main\resources\scalastyle_config.xml'
        ext.destDir = 'src'
        ext.xmlOut = 'build\reports\scalastyle_results.xml'
        ext.verbose = false
        ext.warnings = false
        ext.includeTestSourceDirectory = true

        args '--config',configDir, destDir, '--xmlOutput', xmlOut, '--verbose', verbose, '--warnings', warnings</pre>

[/codesyntax]