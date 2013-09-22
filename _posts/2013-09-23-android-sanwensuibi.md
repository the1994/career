---
layout: post
title: "Android版散文随笔合集"
description: "Android版免费离线散文随笔小说合集，包括散文随笔，优美散文，抒情散文，爱情散文，经典散文，伤感散文。所有文章简短精悍，耐人寻味，或抒发心中万千情愫，或讲述生活曲折坎坷。"
category: "Programming"
tags: ["Android", "Java", "SQLite"]
---

![img](https://scontent-b-ams.xx.fbcdn.net/hphotos-prn1/551297_451156334997168_706945400_n.jpg)

# 前言

Android版《散文随笔》合集apk终于上线了。虽然自从实习结束后回学校就一堆屁事没怎么写代码，github上连续push的记录也停留在9月14号，但这个电子书还是坚持做出来了。上一个Android项目Color半途而废，我不希望自我放弃成为一种习惯。

再一次体会到，做projet跟做成品完全是两码事。

# 功能介绍

说实话，app功能非常简单，数据库方面增删改查，网络访问方面异步加载Jsoup解析。

## 首页

![index](https://scontent-b-ams.xx.fbcdn.net/hphotos-prn2/1240642_451155368330598_1331854663_n.jpg)

精选了若干张意境优雅的照片作为app的欢迎界面，一来可以让用户有一个良好的心情，二来可以给数据库加载提供时间。

## 侧边栏

![navigator](https://scontent-a-ams.xx.fbcdn.net/hphotos-prn1/1238213_451155411663927_194136898_n.jpg)

使用了github上主流的第三方library，方便用户在浏览时快速切换文章分类。

## 文章列表

![list](https://fbcdn-sphotos-g-a.akamaihd.net/hphotos-ak-prn1/44748_451155421663926_312910765_n.jpg)

文章列表，支持actionbar文章搜索以及很炫的jazz效果，一共12种，用过你就知道有多炫！

## 正文

![body](https://scontent-b-ams.xx.fbcdn.net/hphotos-prn2/1157596_451155374997264_870018311_n.jpg)

文章正文，这部分相对简单，本来想作出类似flipboard的效果，但文章的分页问题困扰了我好久，最终放弃。如果后面有时间希望能够解决。

## Icon

![icon](https://scontent-b-ams.xx.fbcdn.net/hphotos-ash3/1240479_451156358330499_1324742762_n.jpg)

不得不说，这次icon的设计让我学到了很多，不仅仅是ps技巧，还有很多关于holo主题的设计思想。图标只是一个方面，app的整体风格，配色，padding和margin等等，都有很多可学习的地方。

# 下载地址

## Google Play

[https://play.google.com/store/apps/details?id=com.jesusjzp.sanwensuibi](https://play.google.com/store/apps/details?id=com.jesusjzp.sanwensuibi)

如果上面的连接无效，请耐心等待，google上线时间各个地区有别。

## 其他

待上传。

# 写在最后

* 给iphone用户道个歉，开发者日子过得太寒酸，用不上mac，虽然一直仰慕Object-C，但能力有限，给来邮件询问的各位朋友说声对不起。

* 本app所有文章均来自[http://www.duanwenxue.com/](http://www.duanwenxue.com/)，我只是收集了文章目录以及链接地址，所有文章内容需要用户访问duanwenxue才能查看，所以不会影响服务器流量（有可能会增加流量）。

* 本应用采用采用了Apache License Version 2.0开源协议，使用了诸多第三方开发library，具体app架构依赖关系及library列表请参见博客：[Android Develop Record(12) - Third-party library](http://jesusjzp.github.io/blog/2013/08/29/Android-Develop-Record/)
