---
id: 197
title: create running background task within android
date: 2012-03-05T23:51:15+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/?p=197
permalink: /2012/03/05/create-running-background-task-within-android/
categories:
  - Android
  - Computer-Mist
tags:
  - android
  - background
  - service
  - task
---
This is more of a beginners entry about that topic. Background tasks are called Service in Android. Creating and using one is pretty simple. From your activity call the following code:

[codesyntax lang=&#8220;java&#8220; lines=&#8220;normal&#8220;]

<pre>public class TestActivity extends Activity {
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main);

        startService(new Intent(this, TestService.class));
    }
}</pre>

[/codesyntax]

And the service class looks like this for instance:

[codesyntax lang=&#8220;java&#8220; lines=&#8220;normal&#8220;]

<pre>public class TestService extends Service{
	@Override
	public IBinder onBind(Intent intent) {
		return null;
	}

	@Override
	public void onCreate() {
		// TODO Auto-generated method stub
		super.onCreate();
	}

	@Override
	public void onDestroy() {
		// TODO Auto-generated method stub
		super.onDestroy();
	}

	@Override
	public void onStart(Intent intent, int startId) {
		// TODO Auto-generated method stub
		super.onStart(intent, startId);

		new Thread(new Runnable() {

			public void run() {

				while(1 == 1){
				// do something useful and dont waste to much battery
				}

			}
		}).start();
	}
}</pre>

[/codesyntax]

Thats basically it, all you have to do now to make it work, is register that service within the AndroidManifest.xml with a line like that:

[codesyntax lang=&#8220;xml&#8220;]

<pre>&lt;service android:name=".package.TestService" /&gt;</pre>

[/codesyntax]
  
Now you are done and got a background job running on your android device, again, easy, isn&#8217;t it?