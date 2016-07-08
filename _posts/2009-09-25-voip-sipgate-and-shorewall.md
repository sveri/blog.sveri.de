---
id: 151
title: voip, sipgate and shorewall
date: 2009-09-25T12:05:58+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/143-guid.html
permalink: /2009/09/25/voip-sipgate-and-shorewall/
categories:
  - Computer-Mist
---
The last week i was very busy with setting something up which seems easy in the beginning but turns out to be very difficult in the end. Following situation, we plan to change our phone provider from an &#8222;analog&#8220; one to a digital one to get the advantages of the voip features. So we took a 30 day trial from [http://sipgate.de](sipgate.de "sipgate.de"). So far so good. In our office we have an linux box with iptables firewall and routing function configured by shorewall. Everything works great, we even set up a vpn connection a second office. As an voip adapter we tried out the linksys PAP2T which worked in other cases at home before. So i plugged in the phone into the adapter, connected the adapter to the internet and &#8230; nothing. Hm, sad, to make a long story short, it took me several days to find out that NAT and SIP is broken by design and that everything works in some cases and others dont. See here for a little bit information i got at the shorewall-users ML: [http://sourceforge.net/mailarchive/forum.php?thread\_name=p06240802c6e110340805%40simon.thehobsons.co.uk&forum\_name=shorewall-users](http://sourceforge.net/mailarchive/forum.php?thread_name=p06240802c6e110340805%40simon.thehobsons.co.uk&forum_name=shorewall-users "http://sourceforge.net/mailarchive/forum.php?thread_name=p06240802c6e110340805%40simon.thehobsons.co.uk&forum_name=shorewall-users") &#8222;<rant>Welcome to the world of NAT &#8211; a completely and utterly broken 
   
network by design. I want to throttle anyone who tries to tell me 
   
that it not broken or is a good idea &#8211; it&#8217;s bodge hat breaks lots of 
   
stuff and has significantly contributed to the delays in getting IPv6 
   
going mainstream (because clueless f\***wits think NAT is a fix for 
   
lack of address space in IPv4). It breaks both rules of IP addressing 
   
&#8211; IP address must be globally unique, and IP addresses must be 
   
globally routable.</rant>&#8222;.  
Now to the feature of this post. A short some up of how to get things going systematically and the fastest way i think.



</p> 

  1. Take your adapter to somewhere you know it worked before. I took it to my home lan. Then make it work there with the account you created (for configuration of the adapter have look at this site: [http://spakonfig.de](http://spakonfig.de "http://spakonfig.de") its extremely useful and detailed in configuration matters of the most voip devices). Try to make it work without NAT options in your router, if you have one. It can make things easier.


  2. Now take your adapter (you have to use dhcp) to your office and plug it directly into your cable modem or whatever provides you with the internet. Make it work.


  3. Connect your LAN again and plug in your adapter. 


  4. If your adapter works now, your fine. If not, step 5


  5. Give your adapter a fixed ip and check the lan settings that they are correct (gateway, nameserver, &#8230;)


  6. connect to your linux box and unload the following modules:nf\_nat\_sip, nf\_conntrack\_sip


  7. If that doesnt work start to forward port 5060 and the rtp port (mostly 16834-16482, can be configured in the adapter) range to your adapter.


  8. If thats still not enough yet check your adapters settings and see if you can enter a stun server (most sip providers offer one).


  9. If it still doesnt work enter an external ip and try to make that work.


 10. If its still not working you&#8217;re fu\***** and please have a look at the post in the shorewall ML i linked to above, there are some more ways to get it going.
</ol> 

Thats it, you should be calling now.