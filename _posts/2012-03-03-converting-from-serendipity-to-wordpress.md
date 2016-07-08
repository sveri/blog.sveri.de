---
id: 177
title: Converting from serendipity to wordpress
date: 2012-03-03T00:46:49+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/?p=177
permalink: /2012/03/03/converting-from-serendipity-to-wordpress/
categories:
  - Computer-Mist
---
Moving to a new vhost on a different hoster with my domain i wanted to try out the well known wordpress blogging software. Well, said, done, looked good so far, at least for my needings.
  
But, one thing bothered me, serendipity only allows to export its entries to rss only, and wordpress has no serendipity import tool so far. And it seems like it will never get one.

Googling around didnt get me further, as there is a serendipity import plugin, but it doesnt work on the new wordpress 3.x, at least it didnt work for me.

I then tried the rss import feature from wordpress, and it didnt look that bad at all. Only thing that didnt work were the html entities, but, nothing easier than that, just open your favorite texteditor and start up the search and replace tool.
  
Go ahead and replace things like < with &#8222;<&#8220; and > with &#8222;>&#8220; and so on. Just do a search on &*; with reg exp and it will find you all html entities.
  
On more thing i had to replace were the double &#8222;<br /><br />&#8220; with only one &#8222;<br />&#8220; so i dont have to much linebreaks in my posts.
  
Maybe check for pictures and things, as they get linked to a certain webspace, and dont get exported with the rss, obviously.

Thats it, it even imported my categories, i dont know about users and other things, cause i never needed these features, thats up to you to find out.