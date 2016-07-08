---
id: 348
title: Parse JSON body response with cljs-ajax error handler
date: 2014-03-22T15:58:31+00:00
author: admin
layout: post
guid: http://blog.sveri.de/?p=348
permalink: /2014/03/22/parse-json-body-response-with-cljs-ajax-error-handler/
categories:
  - Allgemein
---
Today I had a hard time to find out how I can parse custom return messages from compojure with cljs-ajax error handler for POST/GET request. So this is the code that works:

[codesyntax lang=&#8220;bash&#8220;]

<pre>;server side

(defn method []
  (try
	(something that fails)
    (catch Exception e
      {:status 500 :body {:message "Error message."}}
      ))
  )

;cljs side
(defn error-handler [{:keys [response]}]
  (js/alert (:message response)))

(defn test-connection []
  (POST "/url"
        {:params        (get-form-data)
         :handler       succ-handler
         :error-handler error-handler
         :response-format :json
         :keywords? true}))</pre>

[/codesyntax]

So there are two key points here, first:
  
:response-format :json
  
:keywords? true
  
You need these two keys set to be able to parse a response.

The param list has to look like this:
  
[{:keys [response]}]
  
To get the response map from the server.

I only figured this out thanks to a nice guy from: [http://stackoverflow.com/questions/22569702/parse-luminus-json-response](http://stackoverflow.com/questions/22569702/parse-luminus-json-response "stackoverflow")

&nbsp;