---
id: 217
title: adaptd dvorak on windows
date: 2012-03-08T13:47:34+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/?p=217
permalink: /2012/03/08/adaptd-dvorak-on-windows/
categories:
  - Computer-Mist
tags:
  - caps lock
  - dvorak
  - keyboard
  - layout
  - windows
---
After some time has passed i again tried to get a dvorak layout running on windows.
  
Basically it is not that hard, just choose one from the keyboard layout chooser, but thats not my kind of style 😀
  
Of course, as written [here](http://blog.sveri.de/2008/11/28/gvim-dvorak-and-xmodmap/ "gvim, dvorak and xmodmap") in an old post, i want to switch the &#8218;esc&#8216; and &#8218;caps lock&#8216; key, like i did in linux (easily in the end).

Unfortunately, it is not that easy in windows. The only way i found to achieve that is to change some registry entries. There are a few tools out there to do that, but i dont want to go that far.
  
Reason is, you have to reboot to make that work, which is a showstopper for me, as no other user can use my windows then anymore, without having to know about the new special keys.
  
It&#8217;s really a pitty that windows, as old as it is, still so that much non-configurable.

So i just created a new dvorak layout, adapted to my needs, with the [microsoft keyboard layout creator](http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=22339 "microsoft keyboard layout creator 1.4"). It looks like this:

<div id="attachment_218" style="width: 310px" class="wp-caption alignnone">
  <a href="http://blog.sveri.de/wp-content/uploads/2012/03/dvorak_normal.png"><img class="size-medium wp-image-218" title="dvorak_normal" src="http://blog.sveri.de/wp-content/uploads/2012/03/dvorak_normal-300x98.png" alt="" width="300" height="98" /></a>
  
  <p class="wp-caption-text">
    dvorak in normal state
  </p>
</div>

<div id="attachment_219" style="width: 310px" class="wp-caption alignnone">
  <a href="http://blog.sveri.de/wp-content/uploads/2012/03/dvorak_shift.png"><img class="size-medium wp-image-219" title="dvorak_shift" src="http://blog.sveri.de/wp-content/uploads/2012/03/dvorak_shift-300x98.png" alt="" width="300" height="98" /></a>
  
  <p class="wp-caption-text">
    dvorak in shift state
  </p>
</div>

<div id="attachment_220" style="width: 310px" class="wp-caption alignnone">
  <a href="http://blog.sveri.de/wp-content/uploads/2012/03/dvorak_alt_gr.png"><img class="size-medium wp-image-220" title="dvorak_alt_gr" src="http://blog.sveri.de/wp-content/uploads/2012/03/dvorak_alt_gr-300x95.png" alt="" width="300" height="95" /></a>
  
  <p class="wp-caption-text">
    dvorak in alt gr state
  </p>
</div>

There is just one more pitfall i ran into. First i created a complete new layout, which led to the problem that the Ctrl and Alt modifiers behaved somehow different. They corresponding alphabetic keys where on a different place, but neither at the new dvorak, nor in the old german one.
  
So pressing Ctrl+C didnt copy any more, and Ctrl + C on the new layout didnt either.

That was really weird, to solve that one i choose an existing german layout and adapted the keys on that one.
  
Now it&#8217;s like i have to press Ctrl+C on the old keyboard to get something copied, even with the new layout enabled.

The disadvantage is, pressing Ctrl+C on dvorak layout (there, where the new &#8218;C&#8216; is) doesnt copy, but something different.
  
The advantage is, you dont have to remap shortcuts from eclipse/Outlook/whatsoever, as they stay the same.

Here is the installer with the source file included for the microsoft keyboard layout creator:
  
[dvorak_windows](http://blog.sveri.de/wp-content/uploads/2012/03/dvorak_windows2.7z)

**Update**: i forgot the &#8222;&#8220; and added it, dont wanna update the pictures now, but its included in the zip file at the bottom.

**Update 2**: i also forgot the &#8222;%&#8220;, same procedure as before 😉