---
layout: post
title: "Android Develop Record(13) - Adapter"
description: "Android Develop Record"
category: "Programming"
tags: ["Android"]
---

# Adapter

貌似11年暑假的时候就接触到了Adapter这个概念，当时看到学长qq签名就是这个单词，我还在纳闷这到底是多门高深的一个东西。

于是，今天算是见识到了。

Adapter可以看作是数据和界面的桥梁，可以用来初始化，实时更新。由于所有自己定义的adapter都是继承自BaseAdapter，这个类在Android SDK里是封装好的，没法轻易看到里面具体是如何实现的。

在Adapter中，有一个函数getView，非常重要，用来绘制ListView中的每个Item，用position来标志绘制的是哪一个item。我想当然的以为是这样，结果绘制出来的图形用会有偏差，多一个少一个，或者移位了，等。

因为不想翻那几十万行的android源码，我就疯狂地添加log，调试出来才发现这个getView函数在整个界面初始化的时候会被调用两次，也就是说一开始是绘制的两条。往后依次一次一条。等需要显示第i个item的时候，上一次绘制已经把工作做了。实在高不清楚为什么要这样，难不成要做缓冲么。。。

Anyway，不管怎样，这个星期一定要把这个app上线。再往后拖就没时间了。就剩下最后这个类Flipboard的翻页了，加油！
