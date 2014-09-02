---
layout: article
title: Project Euler Problem 1
date: 2013-11-22 10:28:00.000000000 -08:00
---
<small>(Spoilers below!)</small>

I just started learning python, so to get more practice I've decided to try my hand at Project Euler problems. Here we go:

> If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23. 
  Find the sum of all the multiples of 3 or 5 below 1000. 

<small> side note: wow markdown is sweet! </small>

As someone more comfortable with C++, I started off with a for loop and called it a day. It works, but it doesn't take advantage of what you can do with python.

<pre> <code>
sum = 0
for x in range(1000):
	if x % 5 == 0 or x % 3 == 0:
		sum += x
print(sum)
</code> </pre>

After looking around, here's the pythonified one-liner that I came up with. It uses something called 'list comprehension' which lets us write about lists like in math.

<pre> <code>
print sum(number for number in range(1000) if number % 3 is 0 or number % 5 is 0)
 </code> </pre>

(Hurray!)
