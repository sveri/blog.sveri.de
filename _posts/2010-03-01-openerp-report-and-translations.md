---
id: 162
title: openerp, report and translations
date: 2010-03-01T12:04:39+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/154-guid.html
permalink: /2010/03/01/openerp-report-and-translations/
categories:
  - Computer-Mist
---
I am trialing some Open Source ERP Software right now and got stuck with Openerp right now. It is very modular, flexible and adaptable i think, however, its strength is its weakness too and i had a hard time finding out how to translate some strings that are not translated yet. What i needed was &#8222;Ordered Date&#8220; translated into its German &#8222;Angebotsdatum&#8220; in the report from the sales module.



</p> 

  1. Get into the i18n folder of the sales module and open your language file. Add the following lines:  
    #. module: sale  
    #: rml:sale.order:0  
    msgid &#8222;Quotation Date&#8220;  
    msgstr &#8222;Angebotsdatum&#8220;


  2. Upgrade the sales module and reload the translations from the admin menu, just to be sure the translation is added.


  3. Get into the folder report and edit order.rml. Replace:<para style="terp\_tblheader\_General_Centre">[[ o.state==&#8217;draft&#8216; and &#8218;Quotation Date&#8216; or &#8218;Date Ordered&#8216; ]]</para>With:<para style="terp\_tblheader\_General_Centre">[[ o.state <> &#8218;draft&#8216; or removeParentNode(&#8218;para&#8216;) ]]Quotation Date</para><para style="terp\_tblheader\_General_Centre">[[ o.state <> &#8218;draft&#8216; or removeParentNode(&#8218;para&#8216;) ]]Date Ordered</para>The problem here is that python doesnt translate strings in [[]].


  4. Now it should work.
</ol> 



Now, this was easy, wasnt it?  
But, if you adapted the report with the openoffice and base\_report\_designer plugin, the changes in order.rml dont get recognized.  
So you have to open your .sxw template and change :   


  




> <font face="Helvetica, sans-serif"><font size="1" style="font-size: 8pt;">[[o.state==&#8217;draft&#8216; and &#8218;Quotation Date&#8216; or &#8218;Date Ordered&#8216;]]</font></font>



To:   


  




> <font face="Helvetica, sans-serif"><font size="1" style="font-size: 8pt;">[[o.state <> &#8218;draft&#8216; and removeParentNode(&#8218;para&#8216;) ]] Quotation<br /> Date</font></font><font face="Helvetica, sans-serif"><font size="1" style="font-size: 8pt;"><br />[[o.state==&#8217;draft&#8216; and removeParentNode(&#8218;para&#8216;) ]] Ordered Date</font></font> 

That should get you going basically.