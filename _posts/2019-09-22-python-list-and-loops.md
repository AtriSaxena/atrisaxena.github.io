---
title: "Python List & Loops"
categories:
  - Tutorial
classes: wide
tags:
  - machine-learning
  - python
  - programming
  - learning
---

## Python Lists

Python has a great Data structure to store a bunch of value in a single variable is “List”. Like you might have studied in other programming languages there is an “Array”, similarly, there is list in python.

List literals are written within square brackets [ ].

{% highlight python %}

>>>my_list = list() #define a list
>>>my_list = [1,2,3,4,5] #initialize variables
>>>print(my_list)
[1, 2, 3, 4, 5]
>>>print(my_list[0])
1
>>>print(my_list[:3]) #slicing
[1, 2, 3]
>>>print(len(my_list))

{% endhighlight %}

Now, if you want to add more number into “my_list” than we can use “append()” function.

{% highlight python %}

>>>my_list.append(5)  #we can pass only one argument
>>>my_list.append([6,7,8]) #we can another list to append in my_list
>>>print(my_list)
[1, 2, 3, 4, 5, 5, [6, 7, 8]]

{% endhighlight %}


There are many useful functions in list, some of them are:
{% highlight python %}

>>>new_list = list()
>>>new_list =[1,2,3,1,9,5,4]
>>>new_list.count(1) #to count how many times '1' appeared
2
>>>new_list.sort() #to sort list
>>>print(new_list)
[1, 1, 2, 3, 4, 5, 9]

{% endhighlight %}

### Wow, python:

Assignment with an = on lists does not make a copy. Instead, assignment makes the two variables point to the one list in memory.
{% highlight python %}

copy_list = my_list ## Does not copy the list

{% endhighlight %}



<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- horizontal -->
<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-2975147576456254"
     data-ad-slot="4059282902"
     data-ad-format="auto"
     data-full-width-responsive="true"></ins>
<script>
     (adsbygoogle = window.adsbygoogle || []).push({});
</script>

## FOR and IN loops:

"For” and “IN” is extremely useful in python. The *for* construct — for var in list — is an easy way to look at each element in a list (or other collection). Do not add or remove from the list during iteration.
{% highlight python %}

>>>numbers = [4,7,2,1]
>>>sum_num = 0
>>>for num in numbers:
    sum_num+= num
>>>print(sum_num)
14

{% endhighlight %}

## Range

The range(n) yields the number from 0,1,2. . . . ,n-1 and range(1,n) returns 1,2,3. . . . ,n-1 but not including the last number.
{% highlight python %}

>>> for i in range(5):
    print(i)
0
1
2
3
4

{% endhighlight %}

## While Loop

Python also has the standard while-loop, and the *break* and *continue* statements work as in C++ and Java, altering the course of the innermost loop. The above for/in loops solves the common case of iterating over every element in a list, but the while loop gives you total control over the index numbers. There is the code to print even number between 0 to 10:


{% highlight python %}
>>> while i &lt; 10:
    print(i)
    i+=2
#output
0
2
4
6
8

{% endhighlight %}

## List Methods

Here are some common methods you can play with:

- list.append(elem) : adds a single element to the end of the list. Common error: does not return the new list, just modifies the original.
- list.insert(index, elem) : inserts the element at the given index, shifting elements to the right.
- list.extend(list2) : adds the elements in list2 to the end of the list. Using + or += on a list is similar to using extend().
- list.index(elem) : searches for the given element from the start of the list and returns its index. Throws a ValueError if the element does not appear (use “in” to check without a ValueError).
- list.remove(elem) : searches for the first instance of the given element and removes it (throws ValueError if not present)
- list.sort() — sorts the list in place (does not return it). (The sorted() function is preferred.)
- list.reverse() — reverses the list in place (does not return it)
- list.pop(index) — removes and returns the element at the given index. Returns the rightmost element if index is omitted (roughly the opposite of append()).

So, that covers the basic of lists and loop.

So be connected. Thanks for visiting. Share this with your friends.

Comment your suggestions.


<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- horizontal -->
<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-2975147576456254"
     data-ad-slot="4059282902"
     data-ad-format="auto"
     data-full-width-responsive="true"></ins>
<script>
     (adsbygoogle = window.adsbygoogle || []).push({});
</script>
