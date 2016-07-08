---
id: 336
title: Start with datomic and clojure
date: 2014-02-05T12:58:35+00:00
author: admin
layout: post
guid: http://blog.sveri.de/?p=336
permalink: /2014/02/05/start-with-datomic-and-clojure/
categories:
  - Computer-Mist
  - programming
tags:
  - clojure
  - datomic
  - partition
  - seed
---
Hi,

I had trouble getting started with datomic and clojure so I will write up what I did to get it running.

Ok, this is the plan:
  
1. Install a partition in datomic
  
2. Install a schema in datomic
  
3. Seed that schema with some data

1. [codesyntax lang=&#8220;bash&#8220;]

<pre>{:db/id #db/id [:db.part/db],
          :db/ident :lweb
          :db.install/_partition :db.part/db
          :db/doc "The partition of the database for releases"}
  {:db/id #db/id [:db.part/db]
          :db/ident :lweb/id
          :db/valueType :db.type/uuid
          :db/cardinality :db.cardinality/one
          :db/unique :db.unique/identity
          :db.install/_attribute :db.part/db
          :db/doc "A unique identifier for any element"}</pre>

[/codesyntax]

2. [codesyntax lang=&#8220;bash&#8220;]

<pre>{
   :db/id #db/id[:db.part/db]
  :db/ident :release/name
  :db/valueType :db.type/string
  :db/cardinality :db.cardinality/one
  :db/fulltext true
  :db/index true
  :db.install/_attribute :db.part/db}
{:db/id #db/id[:db.part/db]
  :db/ident :release/epics
  :db/valueType :db.type/string
  :db/cardinality :db.cardinality/one
  :db/unique :db.unique/identity
  :db.install/_attribute :db.part/db}
;</pre>

[/codesyntax]

3. [codesyntax lang=&#8220;bash&#8220;]

<pre>{:db/id #db/id[:lweb], :release/name "R1", :release/epics "e1" }</pre>

[/codesyntax]
  
This is the part that I had most trouble understanding it. The id will be stored in the :lweb partition that we created first.
  
I was not able to find an example that made this clear so it took me some time to figure it out with the help of Stuart Halloway on the datomic google group 🙂