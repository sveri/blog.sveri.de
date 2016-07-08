---
id: 255
title: two pitfalls with play framework 2 templates i ran into
date: 2012-04-07T10:51:10+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/?p=255
permalink: /2012/04/07/two-pitfalls-with-play-framework-2-templates-i-ran-into/
categories:
  - Computer-Mist
  - play framework
  - Web Development
tags:
  - 2
  - framework
  - include
  - play
  - subpackage
  - template
  - views
---
On my journey through the play framework 2 i ran into two pitfalls in the last days, that are easily solve_d_.

  1. calling a template from a template with a white space (_@navigation_top ()_) between the template name and it&#8217;s paranthesis results in a message like: _BaseScalaTemplate(play.api.templates.HtmlFormat$@3424b1d9) ()_
  
    just showing the plain class output, to circumvent this you have to leave out the white space: _@navigation_top()_
  2. templates from the views package can be referenced without the package name in the template like above: _@navigation_top()_ calls the navigation_top template and includes it.
  
    But if you add a subpackage and a template within you have to call it with the full package name.
  
    So a template navigation_top in views.navigation has to be included with:
  
    _@views.html.navigation.navigation_top()_