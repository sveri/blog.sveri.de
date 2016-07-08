---
id: 157
title: Script to draw a border around an active window with autohotkey
date: 2010-01-27T13:56:59+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/149-guid.html
permalink: /2010/01/27/script-to-draw-a-border-around-an-active-window-with-autohotkey/
categories:
  - Uncategorized
---
Today i wrote a little script that draws borders around certain windows in Windows <img src="http://blog.sveri.de/templates/default/img/emoticons/wink.png" alt=";-)" style="display: inline; vertical-align: bottom;" class="emoticon" />  
This is especially useful if you play poker, or something similar, and need attention on certain windows.  
The script uses the autohotkey framework, which you can find under: [http://www.autohotkey.com/](http://www.autohotkey.com/ "http://www.autohotkey.com/")



Copy the code in a file called foobar.ahk and start it. Inside itself you find two variables:  
_border_thickness_ which sets the thickness of the borders and  
_Table_String_ which looks for the name of the window around which it should draw the border.



The script looks only for active windows, but you can easily add functionality to it, just look at the autohotkey homepage.



So here it comes:



<blockquote style="MARGIN-RIGHT: 0px" dir="ltr">
  <p>
  </p>
  
  <p>
    #Persistent
  </p>
  
  <p>
  </p>
  
  <p>
    SetTimer, DrawRect, 50<br />border_thickness = 5<br />Table_String = Table
  </p>
  
  <p>
  </p>
  
  <p>
    DrawRect:<br />;Loop {<br />; WinGetClass, class, A<br />;if (class = &#8222;#32770&#8220;)<br /> WinGetTitle, title, A<br /> IfInString, title, %Table_String%<br /> {<br /> WinGetPos, x, y, w, h, A<br /> Gui, +Lastfound +AlwaysOnTop +Toolwindow<br /> iw:= w+4<br /> ih:= h + 4<br /> w:=w+ 8<br /> h:=h + 8<br /> x:= x -border_thickness<br /> y:= y -border_thickness<br /> Gui, Color, FF0000<br /> Gui, -Caption<br /> WinSet, Region, 0-0 %w%-0 %w%-%h% 0-%h% 0-0 %border_thickness%-%border_thickness% %iw%-%border_thickness% %iw%-%ih% %border_thickness%-%ih% %border_thickness%-%border_thickness%<br /> Gui, Show, w%w% h%h% x%x% y%y% NoActivate, Table awaiting Action<br /> }<br />;}<br />return
  </p>
</blockquote>