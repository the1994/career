---
layout: post
title: "Algorithm (02) - DP problem"
description: "Algorithm and data struction training serie. This chapter includs a DP Problem, Pots of gold game."
category: "Programming"
tags: ["Algorithm", "Python"]
---
# DP problem

### Problem Description

Resource: [Pots of gold game](http://www.careercup.com/question?id=15422849)

	Pots of gold game: Two players A & B. There are pots of gold arranged in a line, each containing some gold coins (the players can see how many coins are there in each gold pot - perfect information). They get alternating turns in which the player can pick a pot from one of the ends of the line. The winner is the player which has a higher number of coins at the end. The objective is to "maximize" the number of coins collected by A, assuming B also plays optimally. A starts the game. 

	The idea is to find an optimal strategy that makes A win knowing that B is playing optimally as well. How would you do that? 

### Sample Input

	3, 4, 7, 5

### Sample Output

	10

# My solution:

<pre class="prettyprint linenums">

#!/usr/bin/python
# Filename: 02_pots_game.py
# Author  : Zhipeng JIANG
# Date    : Sep 4, 2013
# Question: http://jesusjzp.github.io/blog/2013/09/04/algorithm-training-pots-game/

def max_coin(pots, start, end):
	if start &gt; end:
		return 0

	a = pots[start] + min(max_coin(pots, start+2, end), max_coin(pots, start+1, end-1))
	b = pots[end] + min(max_coin(pots, start+1, end-1), max_coin(pots, start, end-2))

	return max(a, b)



pots = [3, 4, 7, 5]
print "Pots are", pots
print "The max coins are", max_coin(pots, 0, 3)

</pre>

**More information can be found in my [Github](https://github.com/jesusjzp/python_training)**