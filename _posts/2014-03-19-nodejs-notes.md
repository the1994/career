---
layout: post
title: "NodeJS学习笔记"
description: ""
category: "Programming"
tags: ["Javascript", "NodeJS"]
---

> Node.js is a software platform for scalable server-side and networking applications. Node.js applications are written in JavaScript, and can be run within the Node.js runtime on Windows, Mac OS X and Linux with no changes. Node.js applications are designed to maximize throughput and efficiency, using non-blocking I/O and asynchronous events. Node.js applications run single-threaded, although Node uses multiple threads for file and network events.

NodeJS似乎精髓就在于异步IO，原本打算把数据读写这个时间消耗的操作放到异步里去操作，代码写出来发现没我想的那么简单。看来我还是先用别的script把这次任务做掉，等数据量大了之后再试试NodeJS。

除此之外，[caolan/async](https://github.com/caolan/async)可以提供线性执行，不过用非阻塞的语言去执行阻塞任务，总感觉很奇怪 - -，虽然老板很多时候都这么用。

Bon courage les enfants!