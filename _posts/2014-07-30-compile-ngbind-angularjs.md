---
layout: post
title: "AngularJS recompile after ng-bind-html"
description: "AngularJS recompile after ng-bind-html"
category: "Programming"
tags: ['AngularJS']
---

Just as indicated here in StackOverflow, [angular ng-bind-html-unsafe and directive within it](http://stackoverflow.com/questions/17417607/angular-ng-bind-html-unsafe-and-directive-within-it):

	I have a element which I would like to bind html to it.

	<div ng-bind-html-unsafe="details" upper></div>

	That works. Now, along with it I also have a directive which is bound to the bound html:

	$scope.details = 'Success! <a href="#/details/12" upper>details</a>'

	But the directive upper with the div and anchor do not evaluate. How do I make it work?

Someone responds responds below with a runable example:

	I was also facing this problem and after hours searching the internet I read @Chandermani's comment, which proved to be the solution. You need to call a 'compile' directive with this pattern:

	HTML:

	<div compile="details"></div>

	JS:

	angular.module('yourAppName')
	  .directive('compile', ['$compile', function ($compile) {
	  return function(scope, element, attrs) {
	      scope.$watch(
	        function(scope) {
	           // watch the 'compile' expression for changes
	          return scope.$eval(attrs.compile);
	        },
	        function(value) {
	          // when the 'compile' expression changes
	          // assign it into the current DOM
	          element.html(value);

	          // compile the new DOM and link it to the current
	          // scope.
	          // NOTE: we only compile .childNodes so that
	          // we don't get into infinite loop compiling ourselves
	          $compile(element.contents())(scope);
	        }
	    );
	};
	}]);

	You can see a [working fiddle of it here](http://jsfiddle.net/NWZZE/6/)

Ok, well, this piece of code dose work, this example is simple enough to understand how to recompile binding templates. Actually, if the hierarchy is far more complex, this `scope` might results in error. Please note that in the example above, there's only one scope.

So thanks for Florian, he gives me a solution, that is to pass the root scope as attributes of directive, so this code may look like this:

	HTML:

	<div ng-bind-html="details" do-compile="scope"></div>

	JS:

	angular.module('yourAppName')
	  .directive('doCompile', ['$compile', function ($compile) {
	  return function(scope, element, attrs) {
      var selectedScope = attrs.doCompile && scope.$eval(attrs.doCompile);
      if (!element.hasClass('compiled')) {
        element.addClass('compiled');
        compile(element.contents())(selectedScope || scope);
      }
		};
	}]);