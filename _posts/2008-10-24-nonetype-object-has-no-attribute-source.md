---
id: 127
title: '&#8218;NoneType&#8216; object has no attribute &#8217;source&#8216;'
date: 2008-10-24T09:31:22+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/118-guid.html
permalink: /2008/10/24/nonetype-object-has-no-attribute-source/
categories:
  - Django
---
So you Django Developers want to know
  
what that means:

AttributeError at /path/  
&#8218;NoneType&#8216; object has no attribute &#8217;source&#8216;

Request Method: GET
  
Request URL: http://127.0.0.1:8000/community/
  
Exception Type: AttributeError
  
Exception Value: &#8218;NoneType&#8216; object has no attribute &#8217;source&#8216;
  
Exception Location: /usr/lib/python2.5/site-packages/django/template/debug.py in extend_nodelist, line 56
  
Python Executable: /usr/bin/python
  
Python Version: 2.5.2
  
Python Path: [&#8218;/home/sveri/programmierprojekte/django/youriq_mercurial/youriq/trunk/youriq&#8216;, &#8218;/usr/lib/python25.zip&#8216;, &#8218;/usr/lib/python2.5&#8216;, &#8218;/usr/lib/python2.5/plat-linux2&#8216;, &#8218;/usr/lib/python2.5/lib-tk&#8216;, &#8218;/usr/lib/python2.5/lib-dynload&#8216;, &#8218;/usr/lib/python2.5/site-packages&#8216;, &#8218;/usr/lib/python2.5/site-packages/Numeric&#8216;, &#8218;/usr/lib/python2.5/site-packages/PIL&#8216;, &#8218;/usr/lib/python2.5/site-packages/gtk-2.0&#8216;]
  
Server time: Fri, 24 Oct 2008 11:37:15 +0200

in Context to templatetags?

Yea, this is a failure which **may** come 
  
when you write:

def LatestProfileNode(Node):

instead of:

class LatestProfileNode(Node):

Which is very clear if you think about
  
it enough <img src="http://blog.sveri.net/templates/default/img/emoticons/wink.png" alt=";-)" style="display: inline; vertical-align: bottom;" class="emoticon" />

I hope the django developers find a slightly
  
better failure message for that.