---
id: 169
title: 'Zend Caching &#8211; Which backend to use?'
date: 2011-01-19T22:24:19+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/162-guid.html
permalink: /2011/01/19/zend-caching-which-backend-to-use/
categories:
  - Uncategorized
---
At my current business we are developing a nice web application for a limited user base, based on the Zend engine (only partial), and right around christmas time we met the question of how to cache and what to cache.



What to cache was fast resolved, we decided to cache our models, and the object entities they return. For that we do use the Pet model library, a small, but very effective, caching library: [https://github.com/cyberpet/ZFP](https://github.com/cyberpet/ZFP "https://github.com/cyberpet/ZFP"). 



Then, the next question was how, so, what follows is a short write up of what we came to, and the possibilities we still have:



**<font size="3">Current State</font>**



We right now use the Zend\_Cache\_Backend_Twolevels with APC as its fast backend and sqlite as its slow backend. The sqlite db sits in a ramdisk to execute the writing into the cache fast enough.



**How it came to this decision**



Zend offers several caching backends, namely: 



</p> 

  * Xcache


  * Apc


  * Memcached
</ul> 

All three are basd in the RAM &#8211; 

</p> 

  * File


  * Sqlite
</ul> 



Whereas these both lie on the filesystem.



Because of their backends, there are two great differences, File access, is, especially while writing into the cache, much slower than memory acces, so, you of cause think, uhm, lets cache into the fast backends, like apc or memcache, but wait, theres more to come.   
The fast backends dont support tags, tags are important? You may think? Then, dont take the fast backend.   
There was a lot of discussion going on about using tags in the RAM backends, but basically the zend developers came down to avoid them, cause nobody can guaranty when some pages in the RAM get dropped, or not, and then there may be tag data lossed, maybe resulting in wrong data retrieval.



The pet model, relies on tags, so we have to take the slow backends that support tags.  
But using them is really a showstopper if you have to cache a lot of entries from time to time, its like 20-30 times slower.



**Two Levels for the rescue**   
But wait, there is a solution already there, called _Zend\_Cache\_Backend\_Two\_Levels_, at least it seems like that, _Two levels_ reads and writes from two backends, one slow, and fast the other one. It stores both the tags and the cached data to the slow backend, and then only the cached data to the fast backend.



But, the problem remains, using sqlite as slow backend means, you still have file access for the slow backend, which, especially for many thousand cached objects means, poooooor performance.



And this is where the ram disk comes into the game, mount a ramfs partition and store the sqlite DB there, the db will handle eventual data losses for you and report errors, but you still have a fast slow backend.



**Cache data in slow backend? Not only tags?**   
I also measured if there is a performance gain when only storing the tags in the sqlite DB and not the tags + cached data, on my system i came down to 17%, what didnt seem enough for us, to change a proved caching mechanism from zend to something untested. But maybe later, when 17% seem to be system critical, we even may come and catch the last remaining percent too.



**File backend?   
** Then why not using the file backend in the ram disk? Cause if you have a lot of small files you still have the time consuming fopen, fwrite, fclose for every file, which takes the performance down, compared to sqlite.



**Mysql memory table?**   
I even tried that one as store for the tags, but it also performs very slow, even slower then the file backend in the ram disk.



**Slow/Fast? Read/Write?  
** Everything i said above about the performance was meant for writing into the cache, as that seems to be our greatest problem right now.



Regarding the reads from the backends they all come down to the same as long as you use a Two Level or a slow backend, page generation for our test page takes from 2 to 3.5 seconds, depending on the chosen backend.



Pure fast &#8211; RAM backends are still faster, i came down to like 1 second reading for the test page, so there may be options to get more performance, but right now we dont depend on the last second.



**Testcase  
** Our testcase was an overview page which lists all our suppliers with a lot of information, spread over 10 tables in the database.



**Views? Database anyone?  
** There still are some queries left, which cannot be cached, due to dependency hell under the mappers (the only big disadvantage right now of the pet model <img src="http://blog.sveri.de/templates/default/img/emoticons/sad.png" alt=":-(" style="display: inline; vertical-align: bottom;" class="emoticon" />), they will basically brought down, with their logic, into the database, and then the results will lie there as a view, waiting to deliver its last data, until the and of days.



**Conclusion  
** A mix of Caching, database views, and the use of all the ram our server can give us boils down to a developer friendly (use of application layer logic for development) environment with an acceptable performance at least.  
The last thing that comes to my mind is that Cache is like Security, its not a state, its a process, and who knows where it takes us next <img src="http://blog.sveri.de/templates/default/img/emoticons/smile.png" alt=":-)" style="display: inline; vertical-align: bottom;" class="emoticon" />

<meta http-equiv="content-type" content="text/html; charset=utf-8" />