---
id: 166
title: Already registered at
date: 2010-04-11T20:54:35+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/159-guid.html
permalink: /2010/04/11/already-registered-at/
categories:
  - Django
---
If you&#8217;re fiddling around with django and advanced admin interfaces it can happen that you get an error like:  
Model foobar is already registered at &#8230;   
with an link to &#8230;/contrib/admin.py.



It took me a while to figure out what happened, however, the solution is to import all related models projectlike. So that you have import statements like that:  
from project.app.models import Class.  
The same is valid for the settings.py Apps section.