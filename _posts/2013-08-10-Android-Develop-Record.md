---
layout: post
title: "Android Develop Record(10) - Timestamp and String"
description: "Android Develop Record"
category: "Programming"
tags: ["Android", "SQLite", "Java"]
---

**From Timestamp to String**

	SimpleDateFormat df = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
	Timestamp now = new Timestamp(System.currentTimeMillis());
	String str = df.format(now);

**From String to Timestamp**
    
	SimpleDateFormat df = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
    String time = df.format(new Date());
    Timestamp ts = Timestamp.valueOf(time);


**乱了乱了，感觉自己肚子里的设计模式不够用了，全在乱搞，周末一定要恶补设计模式！！！**
