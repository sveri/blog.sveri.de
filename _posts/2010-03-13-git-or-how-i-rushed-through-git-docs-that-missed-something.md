---
id: 164
title: git or how i rushed through git-docs that missed something?
date: 2010-03-13T10:58:27+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/156-guid.html
permalink: /2010/03/13/git-or-how-i-rushed-through-git-docs-that-missed-something/
categories:
  - Computer-Mist
---
Looking to try out git i followed some tutorials in the web, specifically: [http://pthree.org/2008/11/28/setup-a-git-repository/](http://pthree.org/2008/11/28/setup-a-git-repository/ "http://pthree.org/2008/11/28/setup-a-git-repository/") which looks nice and clean and things and worked up to a certain point. Until it comes to the push. Following this tutorial i always got the message:





> No refs in common and none specified; doing nothing.  
> Perhaps you should specify a branch such as &#8218;master&#8216;.  
> fatal: The remote end hung up unexpectedly  
> error: failed to push some refs to &#8217;ssh://



Now, this is some kind of disturbing, cause it didnt come to a satisfactionary end for me, however: [http://vmlinux.org/jocke/blog/programming](http://vmlinux.org/jocke/blog/programming "http://vmlinux.org/jocke/blog/programming") got the answer prepared for me. You have to add the remote repository to be know to the local one, with the following steps:



> <pre>git remote add origin ssh://login@example.com/pub/git/projextX<br />
git push origin master</pre>
> 
> 

Thats it, now you can use git push, like you&#8217;d do with mercurial for instance. I wonder how the guy from the first tutorial got around it, maybe its a version thing or something like that, however, i almost know nothing about git, but maybe i can provide the answer sometime in the future.