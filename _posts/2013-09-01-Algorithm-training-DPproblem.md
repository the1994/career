---
layout: post
title: "Algorithm (01) - Classical DP problem"
description: "Algorithm and data struction training serie. This chapter includs classical DP Problem"
category: "Programming"
tags: ["Algorithm", "Python"]
---

Well, I see, I'm not good at algorithm. But it would not be too late if I start right now.

Bon courage, Zhipeng!

# DP problem

### Problem Description

Author: [Ignatius.L](http://acm.hdu.edu.cn/showproblem.php?pid=1003)

	Given a sequence a[1],a[2],a[3]......a[n], your job is to calculate the max sum of a sub-sequence. For example, given (6,-1,5,4,-7), the max sum in this sequence is 6 + (-1) + 5 + 4 = 14.

### Input

	The first line of the input contains an integer T(1<=T<=20) which means the number of test cases. Then T lines follow, each line starts with a number N(1<=N<=100000), then N integers followed(all the integers are between -1000 and 1000).

### Output

	For each test case, you should output two lines. The first line is "Case #:", # means the number of the test case. The second line contains three integers, the Max Sum in the sequence, the start position of the sub-sequence, the end position of the sub-sequence. If there are more than one result, output the first one. Output a blank line between two cases.

### Sample Input

	5 6 -1 5 4 -7
	7 0 6 -1 1 -6 7 -5

### Sample Output

	Case 1:
	19

	Case 2:
	14

# My solution:

<pre class="prettyprint linenums">

#!/usr/bin/python
# Filename: 01_dp_problem.py
# Author  : Zhipeng JIANG
# Date    : Sep 4, 2013

####################
# function
####################
def MaxAdjVal(values, length):
	Sum = 0
	Max = int(values[0])
	for i in range(0, length):
		# print values[i]
		Sum += int(values[i])
		if Sum &gt; Max:
			Max = Sum
		if Sum &lt; 0:
			Sum = 0
	return Max

####################
# body
####################
strings = '5 6 -1 5 4 -7'
values = strings.split(' ')
print 'values:', values
res = MaxAdjVal(values, len(values))
print 'res is', res

strings = '7 0 6 -1 1 -6 7 -5'
values = strings.split(' ')
print 'values:', values
res = MaxAdjVal(values, len(values))
print 'res is', res

</pre>

**More information can be found in my [Github](https://github.com/jesusjzp/python_training/)**