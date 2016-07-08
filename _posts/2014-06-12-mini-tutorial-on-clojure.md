---
id: 366
title: Mini tutorial on clojure
date: 2014-06-12T23:01:19+00:00
author: admin
layout: post
guid: http://blog.sveri.de/?p=366
permalink: /2014/06/12/mini-tutorial-on-clojure/
categories:
  - clojure
  - Computer-Mist
tags:
  - clojure
  - raspberry
  - sensors
---
Today a friend of mine had the idea to parse some sensor data on a raspberry pi and generate a html file out of it. So, having had some time I wrote a small clojure application which does just that.
  
I did that in a tutorial form by adding functionality to that project in small steps and explaining what I did in the commits.

What the application does is the following:

  1. Parse a config file for the path to a sensor file
  2. Open that sensor file and convert the data to a clojure map
  3. Take that clojure map and pass it to an enlive template
  4. The template generates a html with a li entry for each key value pair of the map
  5. Parse the config file for a path where we can store the generated html files
  6. Write the html to a randomly generated html file in that path

The sensor file has to look like this:
  
key1: value1
  
key2: value2
  
&#8230;

It completely misses error handling and support for multiple files and a lot of different things one might think of, but I think you can get the point and an entry to step further with clojure.

You can find the code here: https://github.com/sveri/read-sensors

I am surprised that it only took me two hours. I had to ask once in the irc channel for the conversion of file data to maps but the rest of it could be done with my knowledge that I collected in the last 6 months and a bit of googling 🙂