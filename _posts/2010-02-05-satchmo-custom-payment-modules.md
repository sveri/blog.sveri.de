---
id: 158
title: 'Satchmo &#8211; custom payment modules'
date: 2010-02-05T15:09:54+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/150-guid.html
permalink: /2010/02/05/satchmo-custom-payment-modules/
categories:
  - Django
---
For everybody who thinks about using satchmo (the webshop for django: [For everybody who thinks about using satchmo (the webshop for django:](http://www.satchmoproject.com/ "http://www.satchmoproject.com/") ). There are some differences between 0.9 and trunk (which gets closer to 1.0 release). And the differences are not documented yet at all. For instance in the docs it is said that custom payment modules have to get announced in
  
<tt class="docutils literal"><span class="pre">SATCHMO_SETTINGS with the option </span></tt> <tt class="docutils literal"><span class="pre">CUSTOM_PAYMENT_MODULES</span></tt> like:



> 
> 
> <tt class="docutils literal"><span class="pre">SATCHMO_SETTINGS = {<br /> </span></tt><tt class="docutils literal"><span class="pre">CUSTOM_PAYMENT_MODULES : ['custom.module']<br />}</span></tt>
> 
> 



However, in trunk (and later 1.0) they told me on the irc channel you have to add the custom module simply to the insalled apps.