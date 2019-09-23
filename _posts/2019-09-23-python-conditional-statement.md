title: "Python Conditional Statement"
categories:
  - Tutorial
tags:
  - machine-learning
  - python
  - programming
  - learning
---

## Conditional Statement

A conditional statement is needed in programming to check on some condition or logical decision. e.g., if you are python than print “hello python”.

So, there are certain type of conditional statement:

- if statement
- if else statement
- if elif else statement

### If Statement

This is the most basic form of logic introduced into the program. Like I exampled in above example. If true then do this.
{% highlight python %}

>>> x=5   #initialize x with 5
>>> y=10  #initialize y with 10
>>> if x<y:  #condition to check if x less than y
    print("y is greater than x")  #if condition true print
 
#output
y is greater than x

{% endhighlight %}

### If else Statement

You can say this is the advance version of if statement. In previous if the condition is false it does nothing. While in this if else statement, if the condition goes wrong then you can write some statement. e.g., if you are python print “Hello python” else print “Who are you?”.

{% highlight python %}
>>> x=5
>>> y=10
>>> if x>y:
    print("x is greater than y")
    else:
    print("y is greater than x")
#output
y is greater than x

{% endhighlight %}

### If elif else Statement

This statement if more advance version. In this, we can tie up many if and else condition. We can say nested if else. e.g., if you are python print “Hello python” elif you are java print “Hello java” else print “Who are you?”.
{% highlight python %}

>>> x = 4
>>> y = 10
>>> z = 20
>>> if x > y:
    print("x is greater than y")
    elif x < z:
    print("x is less than z")
    else:
    print("if and elif never ran.")
 
#output
x is less than z


{% endhighlight %}

You can nest as many elif as you want.

So, that covers the basic of conditional statements in python.

So be connected. Thanks for visiting. Share this with your friends.

Comment your suggestions.