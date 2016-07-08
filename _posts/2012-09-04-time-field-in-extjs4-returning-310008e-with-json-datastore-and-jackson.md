---
id: 294
title: time field in extjs4 returning 310008e with json datastore and jackson
date: 2012-09-04T10:12:22+00:00
author: admin
layout: post
guid: http://blog.sveri.de/?p=294
permalink: /2012/09/04/time-field-in-extjs4-returning-310008e-with-json-datastore-and-jackson/
categories:
  - Computer-Mist
  - play framework
  - Web Development
tags:
  - date
  - extjs4
  - grid
  - jackson
  - json
  - model
  - time
---
Currently i am trying to connect extjs datagrid via a extjs datamodel to a rest backend in java.
  
It works great so far, however, i have a java.util.Date column which serializes to javascript millitime format, which can be read by the datastore with the format: &#8218;time&#8216; option.

However, if you try to store an updated value of your row, the datastore will convert your date to &#8222;310008e&#8220;, which cannot be parsed into a date.

There are several options to solve this issue. One would be to write a converter for the extjs model, another one is to write a serializer class which implements JsonSerializer<T> and annotate the datefield with it.

I found this solution here: <http://loianegroner.com/2010/09/how-to-serialize-java-util-date-with-jackson-json-processor-spring-3-0/>
  
There are some other options as well, please have a look in the comments of the linked blog post.