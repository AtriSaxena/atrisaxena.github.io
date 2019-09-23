---
title: "File Handling in Python"
categories:
  - Tutorial
tags:
  - machine-learning
  - python
  - programming
  - learning
---

Welcome to python 3 another interesting tutorial.

## Python Files

So, for handling the Files there is a open() function which opens the file and returns the handle to do operations like, writing, reading. The code f = open(‘name’, ‘*operation*’) opens the file into the variable f, ready for reading operations, and use f.close() when finished. For operations we use following:


- Read : ‘r’
- write : ‘w’
- append : ‘a’
-The special mode ‘rU’ is the “Universal” option for text files where it’s smart about converting different line-endings so they always come through as a simple ‘\n’. The standard for-loop works for text files, iterating through the lines of the file (this works only for text files, not binary files).\

Let’s take example of each of the operations.

### Write

So, for writing into a file we need to open the file in write mode. After getting the handle of the file we will pass our data into the file.

Here is the code:

{% highlight python %}

>>> text = "Hello, i am python. How are you?"
#Telling python that you are opening the file with write intention
>>> myfile = open('example.txt','w')
#Actually write the information
>>> myfile.write(text)
32
# It is important to remember to actually close the file, otherwise it will
# hang for a while and could cause problems in your script
>>> myfile.close()

{% endhighlight %}

### Read

For reading the file we need to open the file using the ‘r’ read mode.

{% highlight python %}
>>> readfile = open('example.txt','r')
>>> print(readfile.read())
Hello, i am python. How are you?
>>> readfile.close()

{% endhighlight %}

### Append

For appending some data in the file we need to open the file in ‘a’ append mode.

{% highlight python %}

>>> Append_Text= "\n New Append in my file."
>>> Append_file = open('example.txt','a')
>>> Append_file.write(Append_Text)
24
>>> Append_File.close()

{% endhighlight %}

So, that covers the basic of file operations in python.

So be connected. Thanks for visiting. Share this with your friends.

Comment your suggestions.