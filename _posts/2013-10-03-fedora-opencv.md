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

In Fedora 19, the corresponding packages are **gtk2**, **gtk2-devel**, **pkgconfig**, **cmake** respectively.

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

## Configuration

If you have completed above steps,  some configurations should be made for correct use of OpenCV:

	sudo vim  /etc/ld.so.conf.d/opencv.conf
	add /usr/local/lib into the file
	sudo ldconfig

Furthermore, modify the path variable:

	sudo vim /etc/profile
	add following contents
	export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig
	export LD_LIBRARY_PATH=/usr/local/lib

Save the file and quit, and have modifications come into practice now

	. /etc/profile  (there is a space between the dot and the command)
	# or 
	source /etc/profile

If these methods can not work,  you can logout and enter the system again.

The next part is to test whether openCV can function well.

	cd [your opencv path]/samples/c
	sh build_all.sh
	./facedetect lena.jpg

If an image can pop up,  congratulations!  The library can work well!

Notes:

I have once got a problem when I try to test OpenCV:

OpenCV Error: Unspecified error (The function is not implemented. Rebuild the library with Windows, GTK+ 2.x or Carbon support. If you are on Ubuntu or Debian, install libgtk2.0-dev and pkg-config, then re-run cmake or configure script) in cvNamedWindow

I have the gtk2 installed, but the problem still remains.

I checked in the libray there is a package whose name is **gtk-devel**, I installed it and then I reinstall the OpenCV source code. The problem have disappeared!!

Well, at last, I should say, the compilation really really costs time!!!