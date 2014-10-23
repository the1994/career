---
layout: post
title: "Something interesting about JavaScript"
description: "Something interesting about JavaScript"
category: "Programming"
tags: ["JavaScript"]
---

I found something interesting about JavaScript, most of them are always favored by interviwers for front-end positions.

* * *

	var foo = 1;
	function(){
    console.log(foo);
    var foo = 2;
    console.log(foo);
	}

**Answer**: undefined; 2;

Actually you can access a variable inside a function, but only its name, not its value.

* * *

	var a;
	alert(typeof a); // undefined
	alert(b);        // error

	var a = null;
	alert(typeof a); //object


**Answer**: a is null, but a is an object.

* * *

	var undefined;
	undefined == null; // true
	1 == true;   // true
	2 == true;   // false
	0 == false;  // true
	0 == '';     // true
	NaN == NaN;  // false
	[] == false; // true
	[] == ![];   // true

**Answer**:

- undefined == null, but undefined !=== null
- true or false can be transfered to 1 or 0

* * *

	var foo = "11"+2-"1";
	console.log(foo);
	console.log(typeof foo);

**Answer**: 111, String

* * *

	var a = new Object();
	a.value = 1;
	b = a;
	b.value = 2;
	alert(a.value);

**Answer**: it's a reference!

* * *

	for(var i=1;i<=3;i++){
	  setTimeout(function(){
	      console.log(i);
	  },0);
	};

**Answer**: 4 4 4

* * *

	var User = {
	  count: 1,

	  getCount: function() {
	    return this.count;
	  }
	};

	console.log(User.getCount());  // what?

	var func = User.getCount;
	console.log(func());  // what?

**Answer**: 1; undefined;