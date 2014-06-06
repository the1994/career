---
layout: post
title: "Ng-select example"
description: "Call Function with Delay after Changes in AngularJS"
category: "Programming"
tags: ['AngularJS', 'Javascript', 'ionic']
---

In mobile UI, it's not a good idea to use drop-down to choose item. For example, in the picture below, I can't deny that it's beautifully designed, however, in the same time, it could be difficult for users to pull back drop-down list. Click other parts of the small screen? No way, that will result in mistakes of clicking. By the way, if the drop-down list is too long, it's almost impossible for user to scroll this small list.

![pic](http://media-cache-ec0.pinimg.com/originals/d6/72/ad/d672ad7cf5b30fd7d8563ccc9374f163.jpg)

In the latest Ionicframework, `select` element is supported.

>Ionic's select is styled so its appearance is prettied up relative to the browser's default style. However, when the select elements is opened, the default behavior on how to select one of the options is still managed by the browser.
>
>Each platform's user-interface will be different as the user is selecting an option. For example, on a desktop browser you'll see the traditional drop down interface, whereas Android often has a radio-button list popup, and iOS has a custom scroller covering the bottom half of the window.

For example, in ios emulator, selector functions like this:

![pic](http://media-cache-ec0.pinimg.com/originals/3a/db/8b/3adb8b41a100668d955e1f7857c19193.jpg)

Thay have also provide a piece of example CSS:

	<div class="list">

	  <label class="item item-input item-select">
	    <div class="input-label">
	      Lightsaber
	    </div>
	    <select>
	      <option>Blue</option>
	      <option selected>Green</option>
	      <option>Red</option>
	    </select>
	  </label>

	</div>

So... how to add listener to `select`??? The answer should be `ng-select`. I'm gonna explain how to use `ng-select` with a simple example.

We have a collection of color:

	$scope.colors = [
	  {name:'black', shade:'dark'},
	  {name:'white', shade:'light'},
	  {name:'red', shade:'dark'},
	  {name:'blue', shade:'dark'},
	  {name:'yellow', shade:'light'}
	];

The HTML code:

	<div ng-controller="MyCntrl">
	  Color (null not allowed):
	  <select ng-model="myColor" ng-options="color.name for color in colors">
	  </select>
	  
	  <br>

	  Color (null allowed):
	  
	  <select ng-model="myColor" ng-options="color.name for color in colors" ng-change="dosth()">
	    <option value="">-- choose color --</option>
	  </select>
	  
	  
	  <hr/>

	  Color chosen:
	  <div style="border:solid 1px black; width:50px; height:50px"
	       ng-style="{'background-color':myColor.name}">
	  </div>
	</div>

In this code, there are two selectors, within one null is not allowed, another yes. Each time the value of select changed, it will call `dosth()` in MyCntrl.

	$scope.dosth = function() {
	  console.log('sth');
	};

So that's it. Kid's stuff. Here's the source code: [Edit](http://plnkr.co/edit/fCT4M1lPCjF7fPTmzGE3?p=preview). Have fun!