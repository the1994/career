---
layout: post
title: "Test for IndexedDB with Polyfill"
description: "Test for IndexedDB with Polyfill on Chrome, Firefox, Opera, Safari"
category: "Programming"
tags: ["Javascript"]
---

Test for a polyfill to enable IndexedDB using WebSql.

IndexedDB is not supported on <a href = "http://caniuse.com/#search=IndexedDB" target="_blank">all browsers</a>.
This IndexedDB polyfill exposes the IndexedDB API in unsupported browsers using WebSQL. This shim is basically an IndexedDB-WebSql adapter.

More details of IndexedDB browsers support can be found in this graph:

![pic](http://media-cache-ec0.pinimg.com/originals/d9/7b/b8/d97bb83436eb838b05e9ee213216be00.jpg)

Using this polyfill, you can use a single offline storage API across browsers (Opera, Safari, Firefox, Chrome and IE10) and even mobile devices (Phonegap on iOS and Android).

## Test results

Chrome

![pic](http://media-cache-ak0.pinimg.com/originals/6e/f5/09/6ef509f05185950bcad58887cb806dad.jpg)

Firefox

![pic](http://media-cache-ec0.pinimg.com/originals/eb/92/83/eb9283ed6789b74385dd674248971cb9.jpg)

Opera

![pic](http://media-cache-ak0.pinimg.com/736x/78/ad/8f/78ad8f1aeaf0d4f67b84f19af5f92934.jpg)

Safari

![pic](http://media-cache-ak0.pinimg.com/736x/85/c7/2a/85c72ae06cfbb64b1444e44da82d9c28.jpg)