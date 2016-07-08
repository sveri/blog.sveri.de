---
id: 135
title: Plone, Arch and Python
date: 2009-02-20T16:08:13+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/126-guid.html
permalink: /2009/02/20/plone-arch-and-python/
categories:
  - Web Development
---
Today i was trying out plone. With the unified installer 
  
it aint a big thing to install plone, but when it comes to 
  
make a new buildout you can get in a slight hassle.
  
At least i did. In the buildout routine you come to a point
  
where you do:
  
python bootstrap.py

I used the python that is installed with arch. But then you get
  
a lot of errors complaining about missing PIL:
  
2009-02-20 16:28:57 ERROR PortalTransforms Problem importing module image\_to\_png : No module named PIL.Image
  
2009-02-20 16:28:57 ERROR PortalTransforms Problem importing module image\_to\_gif : No module named PIL.Image
  
2009-02-20 16:28:57 ERROR PortalTransforms Problem importing module image\_to\_jpeg : No module named PIL.Image
  
2009-02-20 16:28:57 ERROR PortalTransforms Problem importing module image\_to\_pcx : No module named PIL.Image
  
2009-02-20 16:28:57 ERROR PortalTransforms Problem importing module image\_to\_ppm : No module named PIL.Image
  
2009-02-20 16:28:57 ERROR PortalTransforms Problem importing module image\_to\_tiff : No module named PIL.Image
  
2009-02-20 16:28:57 ERROR PortalTransforms Problem importing module image\_to\_bmp : No module named PIL.Image
  
2009-02-20 16:28:58 INFO Archetypes /home/sveri/Plone/zinstance/bin/youriq/parts/plone/Archetypes/Field.py[102]:?
  
Warning: no Python Imaging Libraries (PIL) found.Archetypes based ImageField&#8217;s don&#8217;t scale if neccessary.

So, to get around that you have to use the python
  
that came with the unifiebind installer like:
  
/path/to/plone/Python-2.4/bin/python bootstrap.py

and everything will be good <img src="http://blog.sveri.net/templates/default/img/emoticons/smile.png" alt=":-)" style="display: inline; vertical-align: bottom;" class="emoticon" />