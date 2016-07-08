---
id: 144
title: Setting up syncevolution with horde
date: 2009-08-01T21:02:00+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/136-guid.html
permalink: /2009/08/01/setting-up-syncevolution-with-horde/
categories:
  - Computer-Mist
---
I was having a hard time to get syncevolution working   
with horde so i want to share my experiences with the rest of the world.  
In the end its really simple. You need to setup the folder:



_mkdir ~/ .config/syncevolutin_



There you creat a folder with the servername for instance:



_mkdir_ _~/ .config/syncevolutin/servername_



Now create a new file named: _config.ini_ with the following contents:



_syncURL = http://horde.url/rpc.php_  
_username = horde_un  
password = horde_pw  
deviceId = sc-api-nat-<id>_



where <id> is a unique identifier.



Next make a folder called _sources_.



Inside them create a folder for each service you want to synchronize.  
In my case i made four:



_mkdir contacts calendar tasks memo_



__Inside them you need again a _config.ini_ with the following appropriate contents:



**_contacts/config.ini_**  
_type = text/vcard  
uri = contacts_



_**calendar/config.ini******  
type = text/calendar  
sync = two-way   
uri = calendar_



_**tasks/config.ini**  
type = text/x-todo  
sync = two-way  
uri = tasks_



_**memo/config.ini  
** type = text/plain  
uri = memo_



Now start the synchronization with:



_syncevolution servername_



__Now everything should work fine. At least it did for me.  
If you want to debug the process you can set the debug level in:



_servername/config.ini_ with  
_loglevel = 0&#8230;3_



__Where 3 is the the level with the most debug information.





Syncevolution saves the local data in the default appropriate  
category of each synchronized entity. So there is no need to  
setup anything in evolution.



_  
_