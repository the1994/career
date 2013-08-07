---
layout: post
title: "Android Develop Record(08) - Http Get Request"
description: "Android Develop Record"
category: "Programming"
tags: ["Android"]
---

### Simple get request

{% highlight java %}
package com.zhipeng.testnet;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.net.HttpURLConnection;
import java.net.MalformedURLException;
import java.net.URI;
import java.net.URL;

import org.apache.http.HttpResponse;
import org.apache.http.client.HttpClient;
import org.apache.http.client.methods.HttpGet;
import org.apache.http.impl.client.DefaultHttpClient;

import android.util.Log;

public class HttpGetMethod {
	public String get() {
		String res = "";
		String httpUrl = "http://jesusjzp.github.io/";
		Log.v("httpUrl:", httpUrl);
		URL url = null;

		try {
			url = new URL(httpUrl);
		} catch (MalformedURLException e) {
			Log.e("GetData.java", "MalformedURLException");
		}

		if(url != null) {
			try {
				HttpURLConnection urlConn = (HttpURLConnection) url.openConnection();
				urlConn.connect();
				BufferedReader reader = new BufferedReader(new InputStreamReader(urlConn.getInputStream(), "8859-1"));
				String inputLine = null;
				while (((inputLine = reader.readLine()) != null)) {
					res += inputLine + "\n";
				}
				reader.close();
				urlConn.disconnect();
			} catch (IOException e)	{
				return "";
			}
		}
		Log.v("res:", res);
		return res;
	}
}
{% endhighlight %}

**Attention** : HttpGet should be place in another thread instead of main thread !!!!!!!!!!! Because in Android 4.0+, this operation is forbidden. 

**PS** This girl reminds me of someone

![Forfun](http://hd.wallpaperswide.com/thumbs/pretty_girl-t2.jpg)
