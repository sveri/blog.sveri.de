---
id: 146
title: Installing xmonad-contrib
date: 2009-08-09T11:13:31+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/138-guid.html
permalink: /2009/08/09/installing-xmonad-contrib/
categories:
  - Computer-Mist
---
When you try to install xmonad-contrib today in Arch Linux it complains about missing utf8-string:  
xmonad-contrib-0.8.1: dependency utf8-string-0.3.5 doesn&#8217;t exist (use &#8211;force to override)   
but pretends to install despite that problem.



That wont work, you have to manually install the package:  
extra/haskell-utf8-string  
and then reinstall xmonad-contrib to make everything work.