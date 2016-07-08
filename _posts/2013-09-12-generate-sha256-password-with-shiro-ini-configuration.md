---
id: 315
title: Generate sha256 password with shiro ini configuration
date: 2013-09-12T19:11:56+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/?p=315
permalink: /2013/09/12/generate-sha256-password-with-shiro-ini-configuration/
categories:
  - Computer-Mist
  - programming
  - Web Development
tags:
  - sha256
  - shiro
---
Well, it seems like most documentation about shiro suggests to use the  shiro-tools-hasher-1.2.1-cli.jar to generate SHA256 hashed password for your application. I did not get this working at all, so i used another approach.
  
Just call:
  
println(new Sha256Hash(&#8222;your_password&#8220;))
  
> SHAENCODEDSTRING
  
and add this to your shiro.ini:

[main]
  
sha256Matcher = org.apache.shiro.authc.credential.HashedCredentialsMatcher
  
sha256Matcher.hashAlgorithmName=SHA-256
  
iniRealm.credentialsMatcher = $sha256Matcher

[users]
  
user = SHAENCODEDSTRING