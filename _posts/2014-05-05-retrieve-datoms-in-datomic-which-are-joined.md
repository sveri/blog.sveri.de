---
id: 355
title: Retrieve datoms in Datomic which are joined
date: 2014-05-05T14:30:55+00:00
author: admin
layout: post
guid: http://blog.sveri.de/?p=355
permalink: /2014/05/05/retrieve-datoms-in-datomic-which-are-joined/
categories:
  - clojure
  - Computer-Mist
tags:
  - :db/id
  - clojure
  - datomic
  - ref
  - touch
---
I just wondered how to retrieve a complete datom from datomic which references other attributes. With complete I mean a map which contains the whole dataset instead of rereferences to different datoms. I did not find a convenience method for it, so I wrote my own on.
  
This is the result:
  
[codesyntax]

<pre>(defn get-by-id [dbconn id & [add-key]]
  (let [entity (into {} (d/touch (d/entity dbconn (read-string id))))]
    (if (and add-key (get entity add-key))
      (assoc-in entity [add-key] (map #(d/touch (d/entity (dbc) (:db/id %))) (seq (add-key entity))))
      entity)))</pre>

[/codesyntax]

First we retrieve the original datom, convert this into a clojure map. Then we check if a third param is provided (the additional key that contains references to other datoms). If it exists, we retrieve the datoms for these id&#8217;s and put them in the original map afterwards.

This currently only works for a single ref, where the ref has a &#8222;many&#8220; cardinality. But I guess its easy to generalize it some more to support different cases.