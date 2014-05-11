---
layout: post
title: RGB to Hex and Hex to RGB
description: "RGB to Hex and Hex to RGB"
category: "Programming"
tags: ['Ionic', 'AngularJS', 'Javascript']
---

Wahoo, it has been nearly a month since my last post. LOL.

Recently, I started another [ionic](http://ionicframework.com/) project [ionic-color](https://github.com/jesusjzp/ionic-color). Alright, I have to admit that it's another Android project that I didn't finish last year.

Ok, in today's post, I'm gonna present some color-related tricks. The first one converts color with RGB format to the one in HEX, like `(0, 0, 0)` to `#000000`.

	function rgbToHex(r, g, b) {
		return "#" + ((1 << 24) + (r << 16) + (g << 8) + b).toString(16).slice(1);
	}

Of couse the second one converts HEX to RGB, likt `#000000` or `#000` to `(0, 0, 0)`.

	function hexToRgb(hex) {
		// Expand shorthand form (e.g. "03F") to full form (e.g. "0033FF")
		var shorthandRegex = /^#?([a-f\d])([a-f\d])([a-f\d])$/i;
		hex = hex.replace(shorthandRegex, function(m, r, g, b) {
			return r + r + g + g + b + b;
		});

		var result = /^#?([a-f\d]{2})([a-f\d]{2})([a-f\d]{2})$/i.exec(hex);
		return result ? {
			r: parseInt(result[1], 16),
			g: parseInt(result[2], 16),
			b: parseInt(result[3], 16)
		} : null;
	}

OK, I'm gonna explain this later today.

======

I just saw poppy's new website, nice try! At least she made it, much better than those who talk much but do nothing. Good luck!