---
layout: post
title: "Document Image Binarization"
description: "Document Image Binarization with four algorithms, with the help from Christian Wolf, who invents the improved contrast maximization algorithem to binarize document images."
category: "Programming"
tags: ["Image", "cpp", "Python"]
---

There are two parts in this repo. The first part is written in python, which enable a simple binarization algorithm.

The second part uses an improved contrast maximization version of Niblack/Sauvola et al's method to binarize document images. It is also able to perform the more classical Niblack as well as Sauvola et al. methods. Details can be found in the [ICPR 2002 paper](http://liris.cnrs.fr/christian.wolf/publications/index.html#icpr2002v).

## Usage:

### Simple Binarization Algorithm

The first algorithem is easy enough, convert the colorful picture into 'L' model, then check the RGB value with an alpha=127. Main code can be found here:

<pre class="prettyprint linenums">
import os, sys
from PIL import Image

inFile = ''
outFile = ''

if len(sys.argv) != 3:
	print 'Input format error!'
else:
	inFile = sys.argv[1]
	outFile = sys.argv[2]

im = Image.open(inFile).convert('L')

for i in range(im.size[0]):
	for j in range(im.size[1]):
		if im.getpixel((i,j)) &gt; 127:
			im.putpixel((i,j), 255)
		else:
			im.putpixel((i,j), 0)

im.show()
im.save(outFile)
</pre>

In order to run this code, run

	python binsimple.py sample.jpg res.jpg

sample.jpg is the source picture, res.jpg is the result after execution.

Here is an example:

![pic](http://media-cache-ec0.pinimg.com/736x/d1/c2/3b/d1c23b9f6216c3c65a03eb29ef899ccc.jpg)

<center>Figure1: Origin picture</center>

![pic](http://media-cache-ec0.pinimg.com/736x/fc/cd/a1/fccda1168a7b5649ca018d6353a8cb15.jpg)

<center>Figure2: Simple algorithm</center>

### Improved Contrast Maximization Algorithms

The source code please refer the repo in Github, [jesusjzp/binarizewolfjolion](https://github.com/jesusjzp/binarizewolfjolion).

In the README.md there are detailed information about how to use and compiler.

Here are three examples:

![pic](http://media-cache-ec0.pinimg.com/736x/d1/c2/3b/d1c23b9f6216c3c65a03eb29ef899ccc.jpg)

<center>Figure3: Origin picture</center>

![pic](http://media-cache-ak0.pinimg.com/736x/09/e1/d9/09e1d9ff41df9fcbeb614e22438b3145.jpg)

<center>Figure4: Algorithm Wolf et al. (2001) needs black text on white background</center>

![pic](http://media-cache-ec0.pinimg.com/736x/ef/d5/5e/efd55e19b3e6a2dcb8f0c2f75f84b651.jpg)

<center>Figure5: Algorithm Sauvola et al. (1997) needs black text on white background</center>

![pic](http://media-cache-ak0.pinimg.com/736x/ee/6a/15/ee6a15230a8c954f49acff6b47a648ee.jpg)

<center>Figure6: Algorithm Niblack (1986) needs white text on black background</center>