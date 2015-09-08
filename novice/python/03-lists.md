---
layout: page
title: Building programs with Python
subtitle: Arrays, Lists etc
minutes: 15
---
> ## Learning Objectives {.objectives}
>
> *   Lists and Arrays in Python
> *   Indexing and slicing

### Arrays in Python

One of the most fundamental data structures in any language is the array. Python doesn't have 
a native array data structure, but it has the list which is much more general and can be used 
as a multidimensional array quite easily.

#### List basics

Just as a `for` loop is a way to do operations many times, a list is a way to store many values.
A list in python is just an ordered collection of items which can be of any type. By comparison 
an array is an ordered collection of items of a single type - so a list is more flexible than an 
array.

A list is also a dynamic mutable type and this means we can add and delete elements from the list 
at any time. 

Unlike Numpy arrays, lists are built into the language (so we don't have to load a library to use them).

To define a list we simply write a comma separated list of items in square brackets:

~~~{.python}
odds = [1, 3, 5, 7]
print('Odds are:', odds)
~~~

~~~{.output}
Odds are: [1, 3, 5, 7]
~~~

We select individual elements from lists by indexing them:


~~~{.python}
myList = [1,2,3,4,5,6]
~~~

This looks like an array because we can use *slicing* notation to pick out an individual element - 
indexes start from 0.

~~~{.python}
 print(myList[2])
~~~

will display the third element, i.e. the value 3 in this case. Similarly to change the third element we can 
assign directly to it:

~~~{.python}
myList[2] = 100
~~~

The *Slicing* notation looks like array indexing but it is a lot more flexible. For example:

~~~{.python}
myList[2:5]
~~~

is a sublist from the third element to the fifth i.e. from `myList[2]` to `myList[4]`. Notice that the 
final element specified i.e. `[5]` is not included in the slice.

Also notice that you can leave out either of the start and end indexes and they will be assumed to have their maximum possible value. 
For example:

~~~{.python}
myList[5:]
~~~

is the list from `myList[5]` to the end of the list and

~~~{.python}
myList[:5]
~~~

is the list up to and not including myList[5] and

~~~{.python}
myList[:]
~~~

is the entire list.

## Slicing strings 

A section of an array is called a [slice](../../reference.html#slice).
We can take slices of character strings as well:

~~~ {.python}
element = 'oxygen'
print('first three characters:', element[0:3])
print('last three characters:', element[3:6])
~~~

~~~ {.output}
first three characters: oxy
last three characters: gen
~~~
>
> ##Slicing strings challenge{.challenge}
>
> What is the value of `element[:4]`?
> What about `element[4:]`?
> Or `element[:]`?
>
> What is `element[-1]`?
> What is `element[-2]`?
> Given those answers,
> explain what `element[1:-1]` does.

List slicing is more or less the same as string slicing except that we can modify a slice. For example:

~~~{.python}
myList[0:2]=[0,1]
~~~

has the same effect as

~~~{.python}
myList[0]=0
myList[1]=1
~~~

Finally is it worth knowing that the list we assign to a slice doesn't have to be the same size as the slice - 
it simply replaces it even if it is a different size.

## Thin slices 

The expression `element[3:3]` produces an [empty string](../../reference.html#empty-string),
 i.e., a string that contains no characters.

### Basic array operations

So far so good, and it looks as if using a list is as easy as using an array.

Where things start to go wrong just a little is when we attempt to push the similarities 
between lists and arrays one step too far. For example, suppose we want to create an array 
initialised to a particular value. Following the general array idiom in most languages we 
might write:

~~~ {.python}
myList=[]
for i in range(10):
    myList[i]=1
~~~

only to discover that this doesn't work because we can't assign to a list element that doesn't already exist.
One solution is to use the append method to add elements one by one:

~~~ {.python}
myList=[]
for i in range(10):
    myList.append(1)
~~~

This works but it only works if we need to build up the list in this particular order - which most of the time you do. 

