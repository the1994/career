---
layout: post
title: "Limit string length in Input tag"
description: "Limit string length in Input tag"
category: "Programming"
tags: ['AngularJS', 'CSS']
---

## 1 ng-model instead of value

Let's start from something simple. In `<input>` tag, there are two ways to display defaut value:

```html
<input type="text" id="resetTesting" value="Testing" />
```

```html
<input type="text" id="resetTesting2" placeholder="Testing" />
```

So if you want to modify the value:

```javascript
function resetInput() {
  document.getElementById("resetTesting").value = "I'm reset!";
  document.getElementById("resetTesting2").value = "I'm reset, too!";
}
```

You can find the example code here: [http://jsfiddle.net/J7D55/](http://jsfiddle.net/J7D55/).

**But**, what if we want to do this in **AngularJS**?

Obviously, it dosen't work if a `ng-model` is given:

```html
<input name="widget.title" ng-model="widget.title" value="Original value">
```

On the other hand:

```html
<div ng-app="app" ng-controller="MainCtrl">
  <input name="widget.title" ng-model="widget.title" value="Original value">
  <input name="widget.title" ng-model="widget.title">
  <button ng-click="set('foo')">set to foo</button>
</div>
```

```javascript
angular.module('app', [])
.controller('MainCtrl', function($scope) {
  $scope.widget = {title: 'abc'};

  $scope.set = function(new_title) {
    this.widget.title = new_title;
  }
});
```

You can find full example here: [http://jsfiddle.net/tJsms/](http://jsfiddle.net/tJsms/).

## 2 ng-readonly

If you want to keep the value of `<input>` uneditable, you can use `ng-readonly`. Here's an example:

```html
Check me to make text readonly: <input type="checkbox" ng-model="checked"><br/>
<input type="text" ng-readonly="checked" value="I'm Angular"/>
```

You can try this example here: [http://plnkr.co/edit/xLPEa3314pNeYTvW2gFZ?p=preview](http://plnkr.co/edit/xLPEa3314pNeYTvW2gFZ?p=preview).

## 3 css tricks so as to limit the length of string

Sometimes, in a `<input>`, the string is too long to display, like this:

<img src="http://media-cache-ak0.pinimg.com/736x/65/54/65/655465c1fdac8d8dbc15863ad6a1aab7.jpg" style="width:60%;margin:0 auto 0 auto;padding:5px auto 5px auto;">

So the first idea came to me is to shorten this strng in Javascript. However, it feels like hard-coded because you don't know the width of `<input>`. Well of course you can get the width by `document.getElementBy...`. Why not try this css trick (Thanks for [Florian](https://www.facebook.com/florian.ribon)):

```css
element.style {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}
```

Here we go, this is the result:

<img src="http://media-cache-cd0.pinimg.com/736x/3c/98/17/3c9817ef173af984083f1a5eb4b4fdea.jpg" style="width:60%;margin:0 auto;padding:5px 0px 5px 0;">

No matter you change the width of `<input>`, it changes correspondingly.

<img src="http://media-cache-ec0.pinimg.com/originals/cc/ee/a1/cceea1abe6e40690926a57fd93472959.jpg" style="width:60%;margin:0 auto;padding:5px 0px 5px 0;">
