---
id: 165
title: 'Adempiere VA &#8211; Virtualbox'
date: 2010-03-15T09:38:25+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/158-guid.html
permalink: /2010/03/15/adempiere-va-virtualbox/
categories:
  - Computer-Mist
---
I setup Adempiere Virtual Appliance for Virtualbox under arch linux today, just out of curiosity: [http://www.adempiere.com/index.php/ADempiere\_Virtual\_Appliance\_Install#Latest\_Version](http://www.adempiere.com/index.php/ADempiere_Virtual_Appliance_Install#Latest_Version "http://www.adempiere.com/index.php/ADempiere_Virtual_Appliance_Install#Latest_Version") 



Despite the very good installation manual, there were three things which bugged me, but could be solved fast:



</p> 

  * Virtualbox wont boot the VA when the module: vboxnetflt is not loaded (at my place i never needed it for windows)


  * Afterwards, the system still wont boot, you have to check the Virtualbox Setting at System -> Motherboard -> &#8222;Enable IO Apic&#8220;, which has to be checked


  * After you installed adempiere in the VA (the manual tells you how to do that), you cannot login into the system, at least i couldnt, cause there was no valid user given in the tutorial. However, after connecting to the host via: http://adempierehost.com:8080 use   
    System/System  
    as user/pw combination.
</ul>