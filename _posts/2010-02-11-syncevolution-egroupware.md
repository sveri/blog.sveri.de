---
id: 159
title: syncevolution egroupware
date: 2010-02-11T21:34:49+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/151-guid.html
permalink: /2010/02/11/syncevolution-egroupware/
categories:
  - Computer-Mist
---
Recently i wrote a post about syncevolution with horde and finally a rant about it [(http://blog.sveri.de/index.php?/archives/136-Setting-up-syncevolution-with-horde.html](http://blog.sveri.de/index.php?/archives/136-Setting-up-syncevolution-with-horde.html) [](http://blog.sveri.de/index.php?/archives/136-Setting-up-syncevolution-with-horde.html%20 "http://blog.sveri.de/index.php?/archives/136-Setting-up-syncevolution-with-horde.html") / [http://blog.sveri.de/index.php?/archives/142-Opensource-yeah,-synchronization-baeh,-a-plea.html](http://blog.sveri.de/index.php?/archives/142-Opensource-yeah,-synchronization-baeh,-a-plea.html "http://blog.sveri.de/index.php?/archives/142-Opensource-yeah,-synchronization-baeh,-a-plea.html")). However, over the time, things have changed. I got accostumed to egroupware and using it, and after i moved to a new Virtual Server i finally managed to setup up everything to my needs. So this is what i got:



</p> 

  * egroupware setup up on apache


  * several clients like kontact, evolution and even outlook


  * and finally sync the data
</ul> 



What works out of the box is the following (after turning xmlrpc on in egroupware settings):



</p> 

  * Egroupware with funambol connector (used by outlook for instance) &#8211; Tasks/Notes/Calendar/Addressbook.


  * Egroupware with sunbird and caldav (integrated in sunbird) &#8211; only Calendar works.


  * Egroupware with kontact &#8211; groupdav for calendar and tasks + xmlrpc for the addressbook
</ul> 



And finally a cool guy patched egroupware 1.6 + minor versions to make it work with **sync ml** (and with that you can sync with syncevolution and things) . You can find his page and a short guide (its really easy to get it running) here: [http://k.noc.de/index.php?option=com_content&view=article&id=6&Itemid=8](http://k.noc.de/index.php?option=com_content&view=article&id=6&Itemid=8 "http://k.noc.de/index.php?option=com_content&view=article&id=6&Itemid=8").



So egroupware now works even with evolution and a lot of other apps, which is a great thing for all the users out there waiting for such a solution, and i know, there are many of them. I have no experiences with phones and things, but i am pretty sure that a lot of things will be done in future to make that work fine too.



Here is my config for syncevolution:  
_server/config.ini:  
_ 



> _syncURL = http://sveri.de/egroupware/rpc.php  
> username = diezahnfee@default  
> password = ichwillhierweg_



_server/sources/calendar/config.ini_



> _type = text/calendar  
> uri = ./calendar_

Settings for addressbook and tasks are similar, i didnt try them specifically, but you find a lot of docs out there, or in my old blog post (link at top of this posting <img src="http://blog.sveri.de/templates/default/img/emoticons/wink.png" alt=";-)" style="display: inline; vertical-align: bottom;" class="emoticon" />).