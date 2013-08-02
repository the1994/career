---
layout: post
title: "Android Develop Record(05) - View Pager"
description: "Android Develop Record"
category: "Programming"
tags: ["Android"]
---

# Introduction
============

Here is a sample of viewpager, you can fork the sample project by clicking [here](https://github.com/jesusjzp/ViewPager) :

![Sample](http://media-cache-ec0.pinimg.com/736x/1f/d1/8a/1fd18a866baa03a287bd9d3e7ed2525e.jpg)

With [android-support-v4](http://developer.android.com/reference/android/support/v4/app/package-summary.html), we can make more cool effects, such as view pager, action bar, etc.

# Basic structure
----------------------

## Layout

The main layout can be divided into two parts:

1.  Views group. This is where pages group to be presented. For example, if there are three views needed to be presented, you need to design 3 layouts for each of them and combine them togather in the code.
2. Images group. This group is for showing the small points. 

## Action
------------

There are two main actions:

1.  Construct view groups and image groups.
2.  Action adapter and listener.
