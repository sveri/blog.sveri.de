---
id: 145
title: Django Template System and Media_url
date: 2009-08-05T08:19:31+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/137-guid.html
permalink: /2009/08/05/django-template-system-and-media_url/
categories:
  - Django
---
I started making another project with django and again i had a hard time remembering how configure static media serving.  
Here are the important steps to make it work.



</p> 

  1. Get a webserver running and make it serve your static files, lets say under _http://localhost/project_media_


  2. Open s_ettings.py_ of your project and insert the following lines:  
    _TEMPLATE\_CONTEXT\_PROCESSORS = (      
    &#8222;django.core.context_processors.auth&#8220;,      
    &#8222;django.core.context_processors.debug&#8220;,      
    &#8222;django.core.context_processors.i18n&#8220;,      
    &#8222;django.core.context_processors.media&#8220;,      
    )_


  3. Edit the line: _MEDIA_URL_ = and point it to _http://localhost/project_media_


  4. Edit the view where you want to make use of the static files and use the following code:  
    _from django.shortcuts import render\_to\_response  
    from django.template import RequestContext  
    def index(request):      
    return render\_to\_response(&#8218;page.html&#8216;, {},               
    RequestContext(request))_


  5. No open the page.hmtl and access the media url with the template tag: _{{MEDIA_URL}}_
</ol> 



Thats it. Not much to it, but the documentation lacks a place where all that information is tied  
together, or i was just to blind to see it.