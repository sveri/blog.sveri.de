---
id: 320
title: Migrate one imap to another (zimbra to postfix)
date: 2013-10-01T22:04:10+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/?p=320
permalink: /2013/10/01/migrate-one-imap-to-another-zimbra-to-postfix/
categories:
  - Uncategorized
---
I was installing horde on a new server today and had to migrate my imap folders from zimbra to postfix. Both servers run under ubuntu 12.04 LTS. I was trying some different tools, however the only working solution i found was to use imapsync: [https://github.com/patkar/imapsync](https://github.com/patkar/imapsync "https://github.com/patkar/imapsync"). To get it running on ubuntu you have to install the following packages:
  
apt-get install libterm-readkey-perl libmail-imapclient-perl and additionally from cpan:

perl -MCPAN -e shell
  
install Date::Manip

Then you can start with something like:
  
./imapsync &#8211;host1 host.de &#8211;user1 user@user.de &#8211;password1 pw1 &#8211;host2 &#8211;user2 user2@host2.de &#8211;password2 pw2 &#8211;noauthmd5 &#8211;ssl1

You have to use noauthmd5 and ssl1 for zimbra to be able to connect to the imap server, without these options it did not work for me.