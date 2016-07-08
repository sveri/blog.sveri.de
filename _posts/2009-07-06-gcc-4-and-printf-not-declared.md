---
id: 142
title: gcc 4 and printf not declared
date: 2009-07-06T11:33:42+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/134-guid.html
permalink: /2009/07/06/gcc-4-and-printf-not-declared/
categories:
  - Computer-Mist
---
Today i wanted to compile mysql workbench on arch linux
  
which already uses gcc-4.4 at the time being.

After some compiling you get following errors:
  
mysql_resultbind.cpp:104: error: ‘printf’ was not declared in this scope

or 

mysql\_art\_resultset.cpp:57: error: ‘snprintf’ was not declared in this scope

Thanko to IRC the problem was easily and fast solved.
  
Just insert an:

> #include <cstdio>

into the files that throw the error.

UPDATE:
  
Wow, what a mess. Of course that wasnt all that throwed errors.
  
After inserting all the cstdio things a few others will occur.
  
There are patches to be found for older versions of mysql workbench which
  
dont fit for the actual alpha.
  
So i changed everything by hand.
  
Basically you have to look in the files throwing errors for the following:
  
#elif BOOST_PP&#8230;= 1|2
  
and make an
  
#else
  
#if BOOST&#8230;
  
out of it.
  
And insert one or two 
  
#endif
  
at the end of the files.
  
To get a better idea of what i mean look at the bug reports:  
[Mysql-workbench gcc 4.4 bug](http://bugs.mysql.com/bug.php?id=45049 "Mysql-workbench gcc 4.4 bug")