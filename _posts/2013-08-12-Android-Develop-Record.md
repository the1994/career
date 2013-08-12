---
layout: post
title: "Android Develop Record(11) - Http Head Authentication"
description: "Authentication by adding username and password in http header"
category: "Programming"
tags: ["Android"]
---

# Background

Accidentally, for the time being there is no "api-users" for the android application,so we check user account by checking http request header. Like this:

	2011-02-23 15:37:36: (request.c.304) fd: 8 request-len: 308
	POST /test.php HTTP/1.1
	Accept: application/json
	User-Agent: Apache-HttpClient/4.1 (java 1.5)
	Host: myhost.com
	Authorization: Basic YnxpcYRlc3RwMTulHGhlSGs=
	Content-Length: 21
	Content-Type: application/x-www-form-urlencoded; charset=UTF-8
	Content-Encoding: UTF-8
	Connection: Keep-Alive

	HTTP/1.1 200 OK
	Content-type: text/html
	Transfer-Encoding: chunked

# Code

	import java.io.BufferedReader;
	import java.io.IOException;
	import java.io.InputStreamReader;
	import java.net.HttpURLConnection;
	import java.net.MalformedURLException;
	import java.net.URL;

	import org.apache.http.HttpResponse;
	import org.apache.http.auth.UsernamePasswordCredentials;
	import org.apache.http.client.CookieStore;
	import org.apache.http.client.methods.HttpGet;
	import org.apache.http.impl.auth.BasicScheme;
	import org.apache.http.impl.client.AbstractHttpClient;
	import org.apache.http.impl.client.DefaultHttpClient;

	import android.util.Log;

	public class HttpGetMethod {
		
		public String getFoldersStats(String username, String password, String action) {
			String res = "";
			try {
				String url = URL ADDRESS+action;
				HttpGet httpReq = new HttpGet(url);
				
				// add header information
				httpReq.addHeader(BasicScheme.authenticate(
						new UsernamePasswordCredentials(username, password),
						"UTF-8", false));
				DefaultHttpClient httpClient = new DefaultHttpClient();
				HttpResponse httpResponse = httpClient.execute(httpReq);
				
				// handler responds
				StringBuilder builder = new StringBuilder();
				BufferedReader reader = new BufferedReader(new InputStreamReader(
						httpResponse.getEntity().getContent()));
				for (String s = reader.readLine(); s != null; s = reader.readLine()) {
					builder.append(s);
				}
				res = builder.toString();

				// Save to cookie
				CookieStore cookieStore = ((AbstractHttpClient) httpClient).getCookieStore();
			} catch (Exception e) {
				Log.e("", e.toString());
			}
			return res;
		}
	}

