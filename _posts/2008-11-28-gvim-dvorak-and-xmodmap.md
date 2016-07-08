---
id: 131
title: gvim, dvorak and xmodmap
date: 2008-11-28T10:54:39+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/122-guid.html
permalink: /2008/11/28/gvim-dvorak-and-xmodmap/
categories:
  - Linux
---
Thanks to the Arch forum i found that site:  
[DDvorak](http://www.siteuri.ro/dvorak/DDvorak.aspx "DDvorak")

And i was convinced in a very short time.
  
I need to learn the dovrak layout, especially the programmers
  
dvorak layout. Some years ago i switched from the german keyboard
  
layout to the english one cause typing ALT-GR + 8 is a real 
  
pain, and this is what you gotta do to type a &#8222;[&#8220; with a german
  
layout.

But i was not that satisfied, until i found the idea of ddvorak.

After some trial and error i got thrown back. The ddvorak layout
  
is not implemented in Linux yet.

So i tried to remap everything with xmodmap, but no luck.
  
I mean i was successfull until i came to the dead key &#8218;,&#8216; which
  
i couldn&#8217;t get working, no matter what i tried.
  
Whereas the dead key &#8218;,&#8216; is a very important one in the 
  
DDvorak Layout.

Like i said, after some hours i was tired of fiddeling around
  
and i decided to use the Programmers Dvorak Layout which should
  
be part of every Linux installation that is a bit newer.
  
You can load that layout with:

setxkbmap -model pc104 -layout us -variant dvp

But thats only first part.
  
One thing i found out was really useful was the backspace
  
function at the &#8218;b&#8216; key. Believe me, it feels like enlightement
  
if you dont have to break your right hand to delete some
  
characters. So i remapped the standard dvorak programmers
  
layout in the &#8222;us&#8220; file of
  
/usr/share/X11/xkb/symbols

(Other distros may have the file somewhere else)

This is the part that i changed:

partial alphanumeric_keys
  
xkb_symbols &#8222;dvp&#8220; {
  
&#8230;
      
key <lsgt> { [ apostrophe, quotedbl ] };
      
key <ab01> { [ q, Q ] };
      
key <ab02> { [ j, J ] };
      
key <ab03> { [ k, K ] };
      
key <ab04> { [ x, X ] };
      
//key <ab05> { [ Backspace ] };
      
key <ab06> { [ b, B ] };
      
key <ab07> { [ m, M ] };
      
key <ab08> { [ w, W ] };
      
key <ab09> { [ v, V ] };
      
key <ab10> { [ z, Z ] };
  
}

This means i moved all the keys of the down left
  
row one position to left.
  
I didnt find out how to map Backspace functionality
  
to the &#8218;b&#8216; key in that us file. 

After some research i came back to xmodmap.

Here is my current .xmodmap:

keycode 56 = BackSpace 
  
keycode 9 = Caps_Lock
  
keycode 66 = Escape

clear Lock
  
add Lock = Caps_Lock

This means:
  
1. Map the Backspace functionality to keycode 56, which
  
is the &#8218;b&#8216; key on my keyboard.
  
Which is fu\***** handy.

The Rest remaps the Escape and Caps Lock function.
  
I am doing a lot of writing in gvim.
  
(gvim >>>>> All)
  
Everybody who uses gvim a lot knows that getting
  
to command mode breaks up the left Hand.

So i took the idea from the ddvorak man and thought.
  
Hey, i rarely never use that goddamm Caps_Lock key which
  
is in a very close position to the left Hand.

To make a long story short.
  
Line 2 remaps the Caps_Lock function to my &#8218;Esc&#8216; Key.
  
Line 3 remaps the Escape function to my &#8218;Caps Lock&#8216; Key.

Line 4 and 5 are needed for whatever, i know remapping
  
Caps Lock wont work without them.
  
Ask google for more information.