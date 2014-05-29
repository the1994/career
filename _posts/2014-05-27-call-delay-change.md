---
layout: post
title: "Call Function with Delay after Changes in AngularJS"
description: "Call Function with Delay after Changes in AngularJS"
category: "Programming"
tags: ['AngularJS', 'Javascript']
---

There are three ways to call a function with certain seconds of delay in AngularJS.

#### $scope.$watch

	var timer=false;
	$scope.modelName='toto';
	$scope.$watch('modelName', function(){
		if(timer){
			// Ignore this change
			$timeout.cancel(timer)
		}  
		timer= $timeout(function(){
			// Run code
		}, delay)
	});

The unit of `delay` is millisecond.

With $scope.$watch you no longer need `ng-change` to trigger function.

#### $timeout

	(function (timer, delay) {
		$scope.callDelayed= function () {
			if(timer){
				$timeout.cancel(timer)
			}
			timer = $timeout(function(){
				// run code
			}, delay)
		};
	})(false, 500);

The unit of `delay` is millisecond. `callDelayed` is the name of function that is called after `ng-click`.

#### Lodash or Underscore.js

`debounce()` will delay the execution of `func` until after wait milliseconds have elapsed since the last time it was invoked.

	// avoid costly calculations while the window size is in flux
	var lazyLayout = _.debounce(calculateLayout, 150);
	jQuery(window).on('resize', lazyLayout);
	
	// execute `sendMail` when the click event is fired, debouncing subsequent calls
	jQuery('#postbox').on('click', _.debounce(sendMail, 300, {
		'leading': true,
		'trailing': false
	});
	
	// ensure `batchLog` is executed once after 1 second of debounced calls
	var source = new EventSource('/stream');
	source.addEventListener('message', _.debounce(batchLog, 250, {
		'maxWait': 1000
	}, false);

More documentation could be found here: [http://lodash.com/docs#debounce](http://lodash.com/docs#debounce).

#### Reference

- [Call Function with Delay When Textbox Changes in AngularJS](http://stackoverflow.com/questions/15723381/call-function-with-delay-when-textbox-changes-in-angularjs)
- [Implement a delay on $scope.$watch](http://stackoverflow.com/questions/20397253/implement-a-delay-on-scope-watch)