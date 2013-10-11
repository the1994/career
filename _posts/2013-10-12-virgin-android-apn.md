---
layout: post
title: "法国Virgin卡如何在android上配置APN"
description: "法国virgin手机卡配置apn，android手机。La configuration d'APN sur Android pour Virgin en France"
category: "Life"
tags: ["Life"]
---

Virgin跟其余地运营商比起来，算是比较划算的，3.99€一个月，2小时通话，无限短信，100M的流量。

不过比较麻烦的是APN的配置。因为Virgin公司的发展壮大，apn也就一直在变，从一开始租用orange域名到现在有独立服务器，网上教程也就千奇百怪，其中大部分已经失效了。

废话不多说，直接上我手机（android）APN的配置：

    Name: virgin
    APN: virgin-mobile.fr
    MCC: 208
    MNC: 23
    APN protocol: IPv4/IPv6

其余的都缺省为默认值。

Les autres options sont par default.

最后附两幅我手机配置的截图：

![pic](http://media-cache-ec0.pinimg.com/736x/6c/6b/2f/6c6b2fd8e5b9ab0afa603b2759eb830b.jpg)

![pic](http://media-cache-ak0.pinimg.com/736x/fc/a5/30/fca53080cd176adc52d6c63112d0eff1.jpg)
