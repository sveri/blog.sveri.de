---
id: 342
title: Making postal/mailer work with sendmail on windows
date: 2014-02-28T15:25:55+00:00
author: admin
layout: post
guid: http://blog.sveri.de/?p=342
permalink: /2014/02/28/making-postalmailer-work-with-sendmail-on-windows/
categories:
  - Computer-Mist
  - programming
tags:
  - clojure
  - postal
  - sendmail
---
While developing an application that sends mail using sendmail I had the problem that there is no sendmail available on windows.
  
To solve this just download: http://www.glob.com.au/sendmail/sendmail.zip edit the sendmail.ini and set the smtp_server to use localhost. Now add an environment variable to your windows: SENDMAIL=&#8220;/the/path/you/extracted/sendmail/to&#8220;

Then go and get: http://nilhcem.github.io/FakeSMTP/
  
You can use this to check the mails that were sent with sendmail.

Finally add: [clojurewerkz/mailer &#8222;1.0.0&#8220;] to your project.clj.

Now you can call the code to emit some mails:
  
[codesyntax lang=&#8220;php&#8220;]

<pre>(deliver-email {:from mail-from, :to [email] :subject "Subject."}
                 "templates/email/activation.mustache" {:activationlink (generate-activation-link activationid)})</pre>

[/codesyntax]

Thats it 🙂