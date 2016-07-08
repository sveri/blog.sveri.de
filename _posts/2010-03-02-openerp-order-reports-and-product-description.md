---
id: 163
title: openerp, order reports and product description
date: 2010-03-02T11:10:50+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/155-guid.html
permalink: /2010/03/02/openerp-order-reports-and-product-description/
categories:
  - Computer-Mist
---
Today i wondered how to add the description to the order report. What has to be done is find a link from the object which gets looped ([[repeatIn(o.order_line,&#8217;line&#8216;)]]) to the description field. Here comes the general step-by-step approach on how to do that in openerp. I assume you use the gtk client.



</p> 

  1. Our starting point is the [sale.order](http://sale.order.line) report, so we open Administration->Low Level Objects->Actions->Report XML. Where we look for order and see [ir.actions.report.xml](http://ir.actions.report.xml) and sale.order.


  2. Now we check what fields sale.order has, so we open Administration->Customization->Database structure->Objects and look for sale.order, which has a field order\_line with a one2many relation (remember that: [[repeatIn(o.order\_line,&#8217;line&#8216;)]]? this is where the order_line object is being looped).


  3. Now we look at the sale.order.line object and see a reference to product_id which is a many2one field.


  4. Now check the product.product object and look for product\_tmpl\_id (product.template).


  5. And finally on our path we reach product.template and inside it a field called description, thats what we need, so we basically have the path from sale.order to the product description, we just need, to concatenate it.
</ol> 



And this is the result: line.product\_id.product\_tmpl_id.description  
And to get it working in our report template we use it like that:



> [[ line.product\_id.product\_tmpl_id.description or removeParentNode(&#8218;tr&#8216;) ]] or



> [[ line.product\_id.product\_tmpl_id.description or &#8220; ]] or



> [[ line.product\_id.product\_tmpl_id.description or removeParentNode(&#8218;para&#8216;) ]]



Thats it. 



Special thanks go to **alex_joni** from the #openobject irc channel who guided me through the tour and showed me the simplicity of openerp. I hope this helps some people.