---
layout: article
title: Pre-Interview Python Programming Practice Part 1
date: 2013-12-30 16:43:21.000000000 -08:00
---
<small> I show my emotions through alliteration, okay?</small>

Here's a question I did initally as part of my Python Basics post, but i decided it deserved to be its own post.


Task:

> Write a function that takes in a list of words and returns a list of letters in those words without repeats.

Now, to get started let's write the loops we want to turn into list comprehension:

<pre> <code>
def letters(wordsList):
	letterlst= []
	for word in wordsList:
    	for letter in word:
        	if letter not in letterlst:
            	letterlst.append(letter)
    return letterlst
</code> </pre>

Now let's try using list comprehension. This was my first attempt:

<pre> <code>
def letters(wordsList):
	letterlst = []
	letterlst =  [(letter for letter in word if letter not in letterlst) for word in wordList]
    return letterlst
</code> </pre>

This actually creates two generator objects (they're very interesting and somthing I'd barely heard of before which is why they'll be having their own section soon in my Python Basics post)

Now let's try again. 
<pre> <code>
def letters(wordsList):
	letterlst =  [letter for word in wordList for letter in word if letter not in letterlst]
    return letterlst 
</code> </pre>

This code will return an error because we are referencing letterlst before we assign anything to the variable. So we could try to get around this by instantiating the variaable with `letterlst = []` before we do anything, but that doesn't solve our problem. Each time, the list comprehension would check the empty list and we would be left with repeats. 

So what do we do? Remember how you can do list comprehension over a set? Let's try that.

<pre> <code>
def letters(wordsList):
	letterlst =  list({letter for word in wordList for letter in word})
    return letterlst 
</code> </pre>
 
 Done!

