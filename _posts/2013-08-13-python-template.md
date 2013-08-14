---
layout: post
title: "Python Note (4) - template"
description: "Notes for python, I'm a beginner. This chapter introduce how to use templates for multiple files"
category: "Programming"
tags: ["Python"]
---

# Template

In order to reuse your code, template can save your repeat codes. You can save your defined functions or variables in template files.

**Note**, template file should be end by `.py`.

## sys template

    #!/usr/bin/python
    # Filename: using_sys.py

	import sys

	print 'The command line arguments are:'
	for i in sys.argv:
		print i

	print '\n\nThe PYTHONPATH is', sys.path, '\n'

The output could be like this,

	[zhipeng@localhost python]$ python using_sys.py 
	The command line arguments are:
	using_sys.py

	The PYTHONPATH is ['/home/zhipeng/projects/python', '/usr/lib64/python27.zip', '/usr/lib64/python2.7', '/usr/lib64/python2.7/plat-linux2', '/usr/lib64/python2.7/lib-tk', '/usr/lib64/python2.7/lib-old', '/usr/lib64/python2.7/lib-dynload', '/usr/lib64/python2.7/site-packages', '/usr/lib64/python2.7/site-packages/gtk-2.0', '/usr/lib/python2.7/site-packages', '/usr/lib/python2.7/site-packages/setuptools-0.6c11-py2.7.egg-info']

As you can see, those parameters after funcion are outputed. It is like argc, argv of C/C++/Java.

**Note**, in this example, `sys.arg[0] = 'we'`, `sys.arg[1] = 'are'`, etc.

In fact, by comparing with loading `.py` template, loading `.pyc` is faster.


