title: "Python Print functions & Strings"
categories:
  - Tutorial
tags:
  - machine-learning
  - python
  - programming
  - learning
---


## Print Function:

The “print()” function in python is used to print on the console window.

## Strings: 

Python has a built-in string class named ”str”. A string can be enclosed in either single quotes or double quotes.

{% highlight python %}

print('Single Quotes')
print("Double Quotes")

{% endhighlight %}

One thing you need to remember that you need to use similar quotes together. And we can also fuss quotes like, double quotes can fuss single quotes and vice verse.

{% highlight python %}

>>>print("Hey.Let's go out.")
Hey.Let's go out.
>>> print('Hey, i am "python"')
Hey, i am "python"

{% endhighlight %}

Python strings are “immutable” which means they cannot be changed after they are created (Java strings also use this immutable style). Since strings can’t be changed, we construct *new* strings as we go to represent computed values. So, for example, the expression (‘hello’ + ‘there’) takes in the 2 strings ‘hello’ and ‘there’ and builds a new string ‘hellothere’.

Characters in a string can be accessed using the standard [ ] syntax, and like Java and C++, Python uses zero-based indexing, so if str is ‘hello’ str[1] is ‘e’. If the index is out of bounds for the string, Python raises an error.

The len(string) function returns the length of the string. The ‘+’ operator can concatenate two strings.

{% highlight python %}

>>> s = "Hello"
>>> print(s[1])
e
>>> print(len(s))
5
>>> print(s + "there")
Hellothere

{% endhighlight %}

A “raw” string literal is prefixed by an ‘r’ and passes all the chars through without special treatment of backslashes, so r’x\nx’ evaluates to the length-4 string ‘x\nx’.

{% highlight python %}

>>> raw = r"Hello \t\n Python"
>>> print(raw)
Hello \t\n Python

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

## String Methods:

Here are the most common string methods:

- s.lower(), s.upper() — returns the lowercase or uppercase version of the string
- s.strip() — returns a string with whitespace removed from the start and end
- s.isalpha()/s.isdigit()/s.isspace()… — tests if all the string chars are in the various character classes
- s.startswith(‘other’), s.endswith(‘other’) — tests if the string starts or ends with the given other string
- s.find(‘other’) — searches for the given other string (not a regular expression) within s, and returns the first index where it begins or -1 if not found
- s.replace(‘old’, ‘new’) — returns a string where all occurrences of ‘old’ have been replaced by ‘new’
- s.split(‘delim’) — returns a list of substrings separated by the given delimiter. The delimiter is not a regular expression, it’s just text. ‘aaa,bbb,ccc’.split(‘,’) -> [‘aaa’, ‘bbb’, ‘ccc’]. As a convenient special case s.split() (with no arguments) splits on all whitespace chars.
- s.join(list) — opposite of split(), joins the elements in the given list together using the string as the delimiter. e.g. ‘—‘.join([‘aaa’, ‘bbb’, ‘ccc’]) -> aaa—bbb—ccc

### String Slices:

The slice s[start:end] is the elements beginning at start and extending up to but not including end. Let’s take an example s=”Hello”
{% highlight python %}

>>> s="Python"
>>> print(s[:]) #similar to printing whole string
Python
>>> print(s[1:]) #from 1 to end of string
ython
>>> print(s[1:4]) #from 1 to 3rd of string
yth
>>> print(s[1:100]) #from 1 to end of string
ython
>>> print(s[-1]) #last char
n
>>> print(s[-4]) #4th from the end
t
>>> print(s[:-3]) #going up to but not including the last 3 chars.
Pyt
>>> print(s[-3:]) #starting with 3rd to end of string
hon

{% endhighlight %}

So, that covers the basic of print and string function.

So be connected. Thanks for visiting.

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