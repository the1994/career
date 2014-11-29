---
layout: post
title: "Using jQuery.when for dynamic number of requests"
description: ""
category: "Programming"
tags: ["JavaScript"]
---

The `jQuery.when` method accepts a dynamic number of arguments, however, id dose not accept an array of arguments. For example:

	var d1 = new $.Deferred();
	var d2 = new $.Deferred();

	$.when( d1, d2 ).done(function ( v1, v2 ) {
	    console.log( v1 ); // "Fish"
	    console.log( v2 ); // "Pizza"
	});

	d1.resolve( "Fish" );
	d2.resolve( "Pizza" );

What if I want to pass an array instead of requests themselves? For example, an array [d1, d2] instead of `d1` and `d2`.

Ok, here we go, actually we can use `$.when.apply`:

	var d1 = new $.Deferred();
	var d2 = new $.Deferred();

	var deferredArr = [];
	deferredArr.push(d1);
	deferredArr.push(d2);

	$.when.apply(this, deferredArr).then(function() {
    alert("All Done Loading!");
	});