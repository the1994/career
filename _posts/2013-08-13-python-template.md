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

## __name__ template

For example,

    #!/usr/bin/python
    # Filename: using_name.py

	if __name__ == '__main__':
		print 'This program is being run by itself'
	else:
		print 'I am being imported from another module'

The output could be,

	$ python using_name.py
	This program is being run by itself

	$ python
	>>> import using_name
	I am being imported from another module
	>>>

Each template has his `__name__`, if it is `__main__`, that means it is called by itself individually.

## Create your template

For example,

    #!/usr/bin/python
    # Filename: mymodule.py

	def sayhi():
		print 'Hi, this is mymodule speaking.'

	version = '0.1'

    # End of mymodule.py

**Note**, this template should be placed in the same directory as other project files, or belongs to `sys.path` lists.

Here is a demo using *sayhi* template,

    #!/usr/bin/python
    # Filename: mymodule_demo.py

	import mymodule

	mymodule.sayhi()
	print 'Version', mymodule.version

The output could be like this,

	$ python mymodule_demo.py
	Hi, this is mymodule speaking.
	Version 0.1

*Well, it is somehow like class.*

# Conclusion

The advantage of template is to enable you to reuse some services and functions in other program.
