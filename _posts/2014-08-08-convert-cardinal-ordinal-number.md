Ordinal Number in javascript (1st, 2nd, 3rd, 4th)

---
layout: post
title: "Convert Cardinal Number to Ordinal Number"
description: "Convert Cardianl Number to Ordinal Number, like 1 -> 1st, 2 -> 2nd, 3 -> 3rd, 4 -> 4th."
category: "Programming"
tags: ['JavaScript', 'NodeJS']
---

Found a really useful [function](http://ecommerce.shopify.com/c/ecommerce-design/t/ordinal-number-in-javascript-1st-2nd-3rd-4th-29259), which converts [cardinal number](http://en.wikipedia.org/wiki/Cardinal_number) to [ordinal number](http://en.wikipedia.org/wiki/Ordinal_number), for example:

	1 -> 1st
	2 -> 2nd
	3 -> 3rd
	4 -> 4th

I should say, it's really cute, really beautiful, here we go:

  function getOrdinal(n) {
    var s=["th","st","nd","rd"],
      v=n%100;
    return n+(s[(v-20)%10]||s[v]||s[0]);
  }
