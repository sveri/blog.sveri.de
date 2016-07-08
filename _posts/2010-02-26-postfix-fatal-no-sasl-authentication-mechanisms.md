---
id: 161
title: 'Postfix fatal: no SASL authentication mechanisms'
date: 2010-02-26T23:01:55+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/153-guid.html
permalink: /2010/02/26/postfix-fatal-no-sasl-authentication-mechanisms/
categories:
  - Computer-Mist
---
If you set up postfix on your server and cannot receive any message and mail.err shows:   
postfix &#8230; fatal: no SASL authentication mechanisms  
you probably forgot to install: **libsasl2-modules**.