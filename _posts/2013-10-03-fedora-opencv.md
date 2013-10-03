---
layout: post
title: "Install OpenCV in Fedora 19"
description: "OpenCV install tutorials in Fedora 19"
category: "Programming"
tags: ["OpenCV"]
---

Well, it always has some problem if I want to install new development library. Recently, in my third-year project, I start to do something intresting in image analyze field. Well, first of all, I need to install OpenCV.

Let's begin!

## Preparation

**Important: make sure that the following packages have been installed**

Checking List:

- gtk+2.0
- pkg-config
- cmake

In Fedora 19, the corresponding packages are **gtk2**, **pkgconfig** respectively.

## Download source

The OpenCV source code can be downloaded from [sourceforge](https://sourceforge.net/projects/opencvlibrary/).

And then uncompress the file to your preferred directory:

## Compile and install

cd *your directory which will contain the source file*

	tar -xvf OpenCV-2.4.*.tar.bz2

Next, go into the directory of OpenCV and establish a folder named release and enter it:

	cd ~/OpenCV-2.4.*/
	mkdir release
	cd release

Now we are under the release folder and execute the following commands:

	cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D BUILD_PYTHON_SUPPORT=ON ..

This piece of code will produce makefiles for further processes. Then, we will enter codes in the terminal:

	make
	sudo make install


