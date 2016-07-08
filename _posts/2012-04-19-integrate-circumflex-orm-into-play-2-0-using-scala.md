---
id: 281
title: integrate circumflex-orm into play 2.0 using scala
date: 2012-04-19T21:50:15+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/?p=281
permalink: /2012/04/19/integrate-circumflex-orm-into-play-2-0-using-scala/
categories:
  - Computer-Mist
  - play framework
  - Web Development
tags:
  - 2.0
  - circumflex
  - database
  - orm
  - play framework
---
If you are like me and dont want to use the proposed orm anorm in play 2.0, you may want to use circumflex-orm ([http://circumflex.ru/projects/orm/index.html](http://circumflex.ru/projects/orm/index.html "circumflex-orm")) i give you a quick howto on the integration.

First, create a cx.properties in the conf folder of your project:
  
[codesyntax lang=&#8220;scala&#8220;]

<pre>orm.connection.driver=com.mysql.Driver
orm.connection.url=jdbc:mysql://localhost/database
orm.connection.username=un
orm.connection.password=pw</pre>

[/codesyntax]

Also add the dependency to your Build.scala file:
  
[codesyntax lang=&#8220;scala&#8220;]

<pre>val appDependencies = Seq(
  "ru.circumflex" % "circumflex-orm" % "2.1"
)</pre>

[/codesyntax]

Then create the class and it&#8217;s object:
  
[codesyntax lang=&#8220;scala&#8220;]

<pre>class Task extends Record[Long, Task] with IdentityGenerator[Long, Task] {
  def this(name: String, description: String) = {
    this()
    this.name := name
    this.description := description
  }

  val id = "id".BIGINT.NOT_NULL.AUTO_INCREMENT
  val name = "name".VARCHAR(255).NOT_NULL
  val description = "description".TEXT.NOT_NULL

  def PRIMARY_KEY = id
  def relation = Task
}

object Task extends Task with Table[Long, Task] {
  def apply(name: String, description: String) = new Task(name, description)
  def unapply(t : Task) = Option(t.name(), t.description())
}</pre>

[/codesyntax]

For more info about the fields and the usage of circumflex, look at the docs at their homepage please.

Finally you can retrieve with get for instance, it works without any additions.
  
[codesyntax lang=&#8220;scala&#8220;]

<pre>val task = Task.get(1).get
println("name" + task.name())</pre>

[/codesyntax]

But to save and insert you have to promote a context:
  
[codesyntax lang=&#8220;scala&#8220;]

<pre>val task = new Task("foo","bar")
  Context.executeInNew {ctx =&gt;
    println(task.save())
}</pre>

[/codesyntax]

According to a gentle guy from circumflex this should belong into a filter, which must be put somewhere in the lifecycle usage of your app.
  
Please have a look at the google group discussion for more information about that:
  
<https://groups.google.com/forum/?fromgroups#!topic/circumflex-scala/ma2uCVgPx1Q>
  
But thats a topic for another day.

Easy, isn&#8217;t it? In the end i still could use anorm, or something similar besides it, if i need some complex sql&#8217;s to get done, but, as far as i can tell, circumflex should suffice for most of them.

**Update:
  
** Well, transaction management was no topic for another day. It turned out that without the Context from circumflex cache management did not work.

It is possible to save and retrieve, but, retrieval happens from the cache, and without the transaction-management the cache does not get updatet.

So, what you have to do is write your own action class like this:
  
[codesyntax lang=&#8220;scala&#8220;]

<pre>import play.api.mvc.Action
import play.api.mvc.Request
import play.api.mvc.Result
import ru.circumflex.core.Context

case class ScircumflexOrmActionWrapper[A](action: Action[A]) extends Action[A] {

  def apply(request: Request[A]): Result = {
    Context.executeInNew { ctx =&gt;
      action(request)
    }
  }

  lazy val parser = action.parser
}</pre>

[/codesyntax]

And then call it like that:
  
[codesyntax lang=&#8220;scala&#8220;]

<pre>def index = ScircumflexOrmActionWrapper { Action {

	val taskDbObj = Task AS "taskDb"
	val tasks = SELECT(taskDbObj.*).FROM(taskDbObj).ORDER_BY(taskDbObj.createdAt DESC).list

	Ok(html.task.index(tasks))
  }}</pre>

[/codesyntax]

Now you should have a working solution.