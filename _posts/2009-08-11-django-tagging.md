---
id: 147
title: django-tagging
date: 2009-08-11T08:53:52+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/139-guid.html
permalink: /2009/08/11/django-tagging/
categories:
  - Django
---
As far as i can tell after a few hours of using it this seems to be a fairly good django app:



 <a href="http://code.google.com/p/django-tagging/" target="_blank" title="http://code.google.com/p/django-tagging/">http://code.google.com/p/django-tagging/</a>



However, setting it up is a bit of trial and error. Here are the steps i took to get it running.



</p> 

  1. Download it via svn like said in the documentation


  2. Install with _sudo python setup.py install_


  3. add it to installed apps in settings.py


  4. go to your model of choice and _import tagging_ and  
    _from tagging.fields import TagField_


  5. register a model with it with: _tagging.register(Entries, tag\_descriptor\_attr=&#8217;etags&#8216;)_  
    here is the first important point, see that _etags_? Remember it.


  6. create a TagField in your model named tags like:  
    _tags = TagField()_  
    The important thing is, the name has to be **tags** and **tag\_descriptor\_attr** has to have a different value than **tags** or any other column name in your model  
    This seems to be a bug, look at: <a href="http://code.google.com/p/django-tagging/issues/detail?id=95" target="_blank" title="http://code.google.com/p/django-tagging/issues/detail?id=95">http://code.google.com/p/django-tagging/issues/detail?id=95</a>


  7. _python manage.py syncdb_


  8. If your model already exists fire up phpmyadmin and add the column _tags_ yourself as varchar(255)


  9. Almost done, now you have to setup a getter and setter method to get around that issue 95 like:  
     _def set_tags(self, tags):          
    Tag.objects.update_tags(self, tags)      
    def get_tags(self, tags):          
    return Tag.objects.get\_for\_object(self)_


 10. Thats it, for more information on retrieving in templates i found i nice post here:  
    <a href="http://tylerlesmann.com/2009/mar/09/adding-tagging-django-10-views-and-templates/" target="_blank" title="http://tylerlesmann.com/2009/mar/09/adding-tagging-django-10-views-and-templates/">http://tylerlesmann.com/2009/mar/09/adding-tagging-django-10-views-and-templates/</a> 
</ol>