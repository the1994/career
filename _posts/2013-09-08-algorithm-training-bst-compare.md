---
layout: post
title: "Algorithm (03) - BST comparation"
description: "Algorithm and data struction training serie. This chapter includs two Binary Search Tree Compare Problem."
category: "Programming"
tags: ["Algorithm", "Python"]
---

# Reference

The original question is here:

- [http://coders-stop.blogspot.in/2012/03/compare-bsts.html](http://coders-stop.blogspot.in/2012/03/compare-bsts.html)
- [http://www.careercup.com/question?id=19016700](http://www.careercup.com/question?id=19016700)

# Description

Given two unsorted integer arrays, your task is to compare the BST formed by both the arrays.

e.g [3 2 1 4 5] & [3 4 2 5 1]

when the BST is formed by taking the elements from the left, both BST turn out to be same.

     3
    /  \
  2     4
 /        \
1          5

Expected time complexity O(n).

# Solution

You can do something like quicksort: 

Given Arrays A and B, check if A[0] = B[0], (if not, return false). 

Now construct **A_more**, **A_less** and **B_more**, **B_less** where **A_more** contains elements of A which are > A[0], (and appear in the same order as they appear in A). This is basically the partition step in quicksort. Note that you need the partition to be stable. It is possible to do that in-place, but is very complex. 

Now, recursively compare A_more, B_more and compare A_less and B_less. You can add optimizations to compare lengths of arrays to bail out quicker.

# Code

Please refer to my **[Github](https://github.com/jesusjzp/python_training/blob/master/05_bst_compare.py)**
