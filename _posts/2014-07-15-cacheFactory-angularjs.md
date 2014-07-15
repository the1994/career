---
layout: post
title: "AngularJS Cache: $cacheFactory"
description: "Propre cache for AngularJS"
category: "Programming"
tags: ['AngularJS']
---

Recently I was blocked by sharing data among multiple controllers in AngularJS. For example, when I'm filling a form, there are several fields, some of which need to open a new page so as to choose an item... So I need data share between two controllers.

This is a common result in StackOverflow, [http://stackoverflow.com/questions/20181323/passing-data-between-controllers-in-angular-js](http://stackoverflow.com/questions/20181323/passing-data-between-controllers-in-angular-js), ShareService is a good model to share data between controllers.

	app.service('productService', function() {
	  var productList = [];
	  var addProduct = function(newObj) {
	      productList.push(newObj);
	  }
	  var getProducts = function(){
	      return productList;
	  }
	  return {
	    addProduct: addProduct,
	    getProducts: getProducts
	  };
	});

However, as you can see, you need to define a new variable and its getter/setter. It could be a disaster if you have tens or hundres or tousands variable to share. Well, of course, you can create a key-value list to save them all, but in the same time you also need to implement add/delete/update/query functions. Lots of work to do.

Voilà, today I found an factory model in AngularJS, **$cacheFactory**, it's really powerfull and it solves the exact problem that I have. Here's office document and example code: 

- [$cacheFactory in AngularJS](https://docs.angularjs.org/api/ng/service/$cacheFactory)
- [$cacheFactory.Cache in AngularJS](https://docs.angularjs.org/api/ng/type/$cacheFactory.Cache)

- [Example code](http://plnkr.co/edit/sYj5td?p=preview)

By default, $cacheFactory has implemented `info()`, `get(cacheID)`, `put(key, value)`, `get(key)`, `remove(key)`, `removeAll()`, etc. I think that's already enough for *normal* usage, right :P ?

Ok, let me replace that long ShareService with $cacheFactory.