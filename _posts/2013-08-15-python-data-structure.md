---
layout: post
title: "Python Note (5) - data structure"
description: "Notes for python, I'm a beginner. This chapter introduce how to use data structure"
category: "Programming"
tags: ["Python"]
---

There are three types of data structures in python, list, tuple and dictionary. In order to fasten this notes, only python features will be noted here.

## List

Here is a example,

    #!/usr/bin/python
    # Filename: using_list.py

You can initialize a list like this,

    # This is my shopping list
	shoplist = ['apple', 'mango', 'carrot', 'banana']

In order to get the length of the list,

	print 'I have', len(shoplist),'items to purchase.'

You can use for loop to get all the element inside this list

	print 'These items are:', # Notice the comma at end of the line
	for item in shoplist:
		print item,

You can also add an element to the end of list and print out the whole list like this,

	print '\nI also have to buy rice.'
	shoplist.append('rice')
	print 'My shopping list is now', shoplist

In python, it is really easy to sort a list, well, I am not sure the efficiency,

	print 'I will sort my list now'
	shoplist.sort()
	print 'Sorted shopping list is', shoplist

Delete an element is also quite easy for you, check it out,

	print 'The first item I will buy is', shoplist[0]
	olditem = shoplist[0]
	del shoplist[0]
	print 'I bought the', olditem
	print 'My shopping list is now', shoplist

# Tuple

In fact, there is no big difference between tuple and list, but you should remember that tuple is ineditable!!!

Well, the initialization is easy, for example, 

    #!/usr/bin/python
    # Filename: using_tuple.py

	zoo = ('wolf', 'elephant', 'penguin')
	print 'Number of animals in the zoo is', len(zoo)

	new_zoo = ('monkey', 'dolphin', zoo)
	print 'Number of animals in the new zoo is', len(new_zoo)
	print 'All animals in new zoo are', new_zoo
	print 'Animals brought from old zoo are', new_zoo[2]
	print 'Last animal brought from old zoo is', new_zoo[2][2]

Next let us see how to ouput as a tuple, it is somehow like C,

# Dict

    #!/usr/bin/python
    # Filename: using_dict.py

    # 'ab' is short for 'a'ddress'b'ook

Initialization of a type dict

	ab = {       'Swaroop'   : 'swaroopch@byteofpython.info',
				 'Larry'     : 'larry@wall.org',
				 'Matsumoto' : 'matz@ruby-lang.org',
				 'Spammer'   : 'spammer@hotmail.com'
		 }

Ouput value according the key

	print "Swaroop's address is %s" % ab['Swaroop']

Add new pair

    # Adding a key/value pair
	ab['Guido'] = 'guido@python.org'

Delete pair by deleting the key

    # Deleting a key/value pair
	del ab['Spammer']

Output the length and get each pair

	print '\nThere are %d contacts in the address-book\n' % len(ab)
	for name, address in ab.items():
		print 'Contact %s at %s' % (name, address)

Check existence

	if 'Guido' in ab: # OR ab.has_key('Guido')
		print "\nGuido's address is %s" % ab['Guido']

# Sequence

In fact, list, tuple and dict all are sequence. The two main features of seq are indexing and slicing.

    #!/usr/bin/python
    # Filename: seq.py

	shoplist = ['apple', 'mango', 'carrot', 'banana']

Ok, the indexs -1, -2 are before 0. Assum it is a loop. 

    # Indexing or 'Subscription' operation
	print 'Item 0 is', shoplist[0]
	print 'Item 1 is', shoplist[1]
	print 'Item 2 is', shoplist[2]
	print 'Item 3 is', shoplist[3]
	print 'Item -1 is', shoplist[-1]
	print 'Item -2 is', shoplist[-2]

This part is little bit like matlab

    # Slicing on a list
	print 'Item 1 to 3 is', shoplist[1:3]
	print 'Item 2 to end is', shoplist[2:]
	print 'Item 1 to -1 is', shoplist[1:-1]
	print 'Item start to end is', shoplist[:]

You can slice a String

    # Slicing on a string
	name = 'swaroop'
	print 'characters 1 to 3 is', name[1:3]
	print 'characters 2 to end is', name[2:]
	print 'characters 1 to -1 is', name[1:-1]
	print 'characters start to end is', name[:]

## Reference

    #!/usr/bin/python
	# Filename: reference.py

New a reference to shoplist

	print 'Simple Assignment'
	shoplist = ['apple', 'mango', 'carrot', 'banana']
	mylist = shoplist # mylist is just another name pointing to the same object!

	del shoplist[0]

Notice that both shoplist and mylist both print the same list without the 'apple' confirming that they point to the same object

	print 'shoplist is', shoplist
	print 'mylist is', mylist

Notice that now the two lists are different

	print 'Copy by making a full slice'
	mylist = shoplist[:] # make a copy by doing a full slice
	del mylist[0] # remove first item

	print 'shoplist is', shoplist
	print 'mylist is', mylist

The output is

	$ python reference.py
	Simple Assignment
	shoplist is ['mango', 'carrot', 'banana']
	mylist is ['mango', 'carrot', 'banana']
	Copy by making a full slice
	shoplist is ['mango', 'carrot', 'banana']
	mylist is ['carrot', 'banana']

# String

	#!/usr/bin/python
	# Filename: str_methods.py

	name = 'Swaroop' # This is a string object 

	if name.startswith('Swa'):
		print 'Yes, the string starts with "Swa"'

	if 'a' in name:
		print 'Yes, it contains the string "a"'

	if name.find('war') != -1:
		print 'Yes, it contains the string "war"'

	delimiter = '_*_'
	mylist = ['Brazil', 'Russia', 'India', 'China']
	print delimiter.join(mylist)
