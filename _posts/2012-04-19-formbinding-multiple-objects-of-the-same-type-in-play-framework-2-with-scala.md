---
id: 278
title: Formbinding multiple objects of the same type in play framework 2 with scala
date: 2012-04-19T09:00:45+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/?p=278
permalink: /2012/04/19/formbinding-multiple-objects-of-the-same-type-in-play-framework-2-with-scala/
categories:
  - Computer-Mist
  - play framework
  - Web Development
tags:
  - 2.0
  - form binding
  - list
  - objects
  - playframework
---
The play docs provide small code snippets on how to use repeated values with form binding, but they make not clear on how to bind to a List of objects. In the end it&#8217;s easy.

Let&#8217;s say we have these two classes:
  
[codesyntax lang=&#8220;scala&#8220;]

<pre>case class Task(name: String, description: String)
case class Tasks(tasks: List[Task])</pre>

[/codesyntax]

Then we can make a Form val like this:
  
[codesyntax lang=&#8220;scala&#8220;]

<pre>val taskForm: Form[Tasks] = Form(
      mapping(
          "tasks" -&gt; list(mapping(
              "name" -&gt; text,
              "description" -&gt; text
          )(Task.apply)(Task.unapply))
      )(Tasks.apply)(Tasks.unapply)
  )</pre>

[/codesyntax]

The html would look like this:
  
[codesyntax lang=&#8220;html4strict&#8220;]

<pre>&lt;tr&gt;
  &lt;td&gt;&lt;input name="tasks[0].name" type="text" &gt;&lt;/td&gt;
  &lt;td&gt;&lt;textarea name="tasks[0].description" &gt;&lt;/textarea&gt;
  &lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
  &lt;td&gt;&lt;input name="tasks[1].name" type="text" &gt;&lt;/td&gt;
  &lt;td&gt;&lt;textarea name="tasks[1].description"&gt;&lt;/textarea&gt;
  &lt;/td&gt;
&lt;/tr&gt;</pre>

[/codesyntax]

And the retrieval as stated in the docs:
  
[codesyntax lang=&#8220;scala&#8220;]

<pre>val tasks = taskForm.bindFromRequest.get</pre>

[/codesyntax]
  
gives back a list of tasks with a task object inside for each table row.

I admit that my table is not a normal form, instead i use jquerys .serializeArray() on the table to submit the data via $.ajax(), but that&#8217;s a different story.

See also this question at stackoverflow from me:
  
[http://stackoverflow.com/questions/10218814/bind-multiple-objects-in-play-framework-2-0-from-a-form/10223431#10223431](http://stackoverflow.com/questions/10218814/bind-multiple-objects-in-play-framework-2-0-from-a-form/10223431#10223431 "stackoverflow form binding play framework")