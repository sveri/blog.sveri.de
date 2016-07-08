---
id: 170
title: 'Zend_Db_Table_Abstract &#8211; createRow new dbtable Column vanished?'
date: 2011-01-31T16:02:20+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/163-guid.html
permalink: /2011/01/31/zend_db_table_abstract-createrow-new-dbtable-column-vanished/
categories:
  - Uncategorized
---
For everybody using the function createRow() from Zend\_Db\_Table_Abstract and wondering why new columns in any db &#8211; table dont arise in the returned row. He shall be advised to read the phpdoc of createRow where it says:   
_Fetches a new blank row (not from the database)._  
Yep, thats important, as it reads from the metadatacache, and you have to delete it everytime you add a new column to a certain table.



This took me 30 minutes to figure it out <img src="http://blog.sveri.de/templates/default/img/emoticons/laugh.png" alt=":-D" style="display: inline; vertical-align: bottom;" class="emoticon" />