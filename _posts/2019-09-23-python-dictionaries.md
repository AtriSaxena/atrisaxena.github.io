---
title: "Python Dictionaries"
categories:
  - Tutorial
tags:
  - machine-learning
  - python
  - programming
  - learning
---

## Python Dictionaries

Python has a data structure called Dict in which you can store value with key: pair combination. e.g., dict= {key1: value1, key2 : value2,…… }. The “empty dict” is just an empty pair of curly braces  {}.

Looking up or setting a value in a dict uses square brackets. eg., dict[‘code’] looks up the value under the key ‘code’. Strings, numbers, and tuples work as keys, and any type can be a value. Looking up a value which is not in the dict throws a KeyError — use “in” to check if the key is in the dict, or use dict.get(key) which returns the value or None if the key is not present (or get(key, not-found) allows you to specify what value to return in the not-found case).


{% highlight python %}
>>> mydict = dict() #initialize dict
>>> mydict['a'] = "apple" #in key 'a' we stored "apple"
>>> mydict['b'] = "ball"
>>> mydict['c'] = "cat"
>>> print(mydict)
{'a': 'apple', 'b': 'ball', 'c': 'cat'}   #output
>>> print(mydict['a'])
apple        #output
>>> mydict[1] = "one" #using mix of key numeric key with string key
>>> print(mydict)
{'a': 'apple', 'b': 'ball', 'c': 'cat', 1: 'one'} #output
>>> "one" in mydict
False  #output
>>> 1 in mydict
True  #output
>>> if 'b' in mydict:
    print(mydict['b'])
ball   #output
>>> print(mydict.get('z'))  #since 'z' is not in key so returned none
None  #output

{% endhighlight %}

We can also run a for loop on dict to iterate through all of the keys. There are two methods dict.key() and dict.values() returns the list of the keys or values respectively. Another function dict.items() returns the list of (key,value) tuple.

{% highlight python %}

>>> for key in mydict.keys():
    print(key,end=",")
a,b,c,1, #output
>>> print(mydict.values())
dict_values(['apple', 'ball', 'cat', 'one']) #output
>>> print(mydict.items())
#output
dict_items([('a', 'apple'), ('b', 'ball'), ('c', 'cat'), (1, 'one')])
>>> for k,v in mydict.items():
    print('(',k,',',v,')' )
#output
( a , apple )
( b , ball )
( c , cat )
( 1 , one )

{% endhighlight %}

### Delete

The “del” operator does deletions. In the simplest case, it can remove the definition of a variable, as if that variable had not been defined. Del can also be used on list elements or slices to delete that part of the list and to delete entries from a dictionary.

{% highlight python %}

>>> python = 1
>>> del python #python variable deleted
>>> mylist = [1,2,3,4]
>>> del mylist[0] #mylist index 0 element deleted
>>> del mylist[-2:] #del last two element
>>> print(mylist)
[2] #output
>>> my_new_dict = {1:'a', 2:'b',3:'c'} #initialize dict
>>> del my_new_dict[3] #del element at key=3
>>> print(my_new_dict)
{1: 'a', 2: 'b'}  #output

{% endhighlight %}

So, that covers the basic of dictionaries in python.

So be connected. Thanks for visiting. Share this with your friends.

Comment your suggestions.
