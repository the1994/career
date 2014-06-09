---
layout: post
title: "Accordion List in Ionic and AngularJS"
description: ""
category: "Programming"
tags: ['AngularJS', 'Ionic', 'Javascript']
---

## Preparation

Before introducing accordion list, here's a quick tuto for Ionic:

	npm install -g cordova ionic
	ionic start myApp tabs

Ionic has three template:

![pic](https://dl.dropboxusercontent.com/u/107773577/Blog%20pics/Screen%20Shot%202014-06-09%20at%203.57.50%20PM.png)

Run your starter-app:

	cd myApp
	ionic platform add ios
	ionic build ios
	ionic emulate ios


## Accordion List

How to implement accordion list with Ionicframework? To be frankly, it can be really simple with the help of 'transition' in CSS.

![pic](https://dl.dropboxusercontent.com/u/107773577/Blog%20pics/Screen%20Shot%202014-06-09%20at%203.43.48%20PM.png)

![pic](https://dl.dropboxusercontent.com/u/107773577/Blog%20pics/Screen%20Shot%202014-06-09%20at%203.44.02%20PM.png)

The basic list html:

	<ion-content class="has-header">
	  <ion-list>
	    <div ng-repeat="group in groups">
	      <ion-item class="item-stable"
	                ng-click="toggleGroup(group)"
	                ng-class="{active: isGroupShown(group)}">
	          <i class="icon" ng-class="isGroupShown(group) ? 'ion-minus' : 'ion-plus'"></i>
	        &nbsp;
	        Group {{group.name}}
	      </ion-item>
	      <ion-item class="item-accordion"
	                ng-repeat="item in group.items"
	                ng-show="isGroupShown(group)">
	        {{item}}
	      </ion-item>
	    </div>
	  </ion-list>
	</ion-content>

The controller:

	.controller('PlaylistsCtrl', function($scope) {
		$scope.groups = [];
	  for (var i=0; i<5; i++) {
	    $scope.groups[i] = {
	      name: i,
	      items: []
	    };
	    for (var j=0; j<3; j++) {
	      $scope.groups[i].items.push(i + '-' + j);
	    }
	  }
	  
	  /*
	   * if given group is the selected group, deselect it
	   * else, select the given group
	   */
	  $scope.toggleGroup = function(group) {
	    if ($scope.isGroupShown(group)) {
	      $scope.shownGroup = null;
	    } else {
	      $scope.shownGroup = group;
	    }
	  };
	  $scope.isGroupShown = function(group) {
	    return $scope.shownGroup === group;
	  };
	})

The CSS file:

	.list .item.item-accordion {
	  line-height: 38px;
	  padding-top: 0;
	  padding-bottom: 0;
	  transition: 0.09s all linear;
	}
	.list .item.item-accordion.ng-hide {
	  line-height: 0px;
	}
	.list .item.item-accordion.ng-hide-add,
	.list .item.item-accordion.ng-hide-remove {
	  display: block !important;
	}


You can find the original code here: [Click me](http://codepen.io/ionic/pen/uJkCz?editors=101)