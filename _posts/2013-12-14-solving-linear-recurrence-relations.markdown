---
layout: article
title: Solving Linear Recurrence Relations
date: 2013-12-14 12:50:07.000000000 -08:00
---
<small> Side note: My discrete math final's coming up so I've decided to write a series of small posts on basic topics (while listening to Beyonce's new album(!)) to help me study. Hopefully this'll prove to be a helpful reference in the future too in case this topic comes up.</small>

----
More specifically, this post will cover how to solve homogenous recurrence relations.  So what does that mean? Here's a general form:


$$ a\_n = c\_1 a\_{n-1} + c\_2 a\_{n-2} + ... + c\_k a\_{n-k}  $$

It's a recurrence relation as the $n^{th} $ term depends upon the previous terms. It's linear because the RHS is a sum of the previous terms (with coeffecientnts) and it's homogeneous because all terms are multiplied with $ a\_x $ . A non-homogenous relation might also depend on some term like $ 4 ^ n$ or some other f(n). 

<h4> Basic example </h4>
Now, here's an example we'll solve:

$$ a\_n = 13 a\_{n-1} - 22 a\_{n-2} \: if  \:a\_0 = 3, a\_1 = 15 $$


Basically our goal is to find some non-recurrence equation to represent $a\_n$. So to start, we simply guess that $a\_n = x ^n$ and figure out x later. 

Let's substitute $x^n$ for $a_n$ and move things to the left:

$$ x^n = 13 x ^{n-1} - 22 x^{n-2}$$
$$ x^n -  13 x ^{n-1} - 22 x^{n-2} = 0 $$
 
Now if we divide everything by $x^{n-2}$, things will start to look familiar. (In general, just divide by the lowest power you have).

$$ x^2 -  13 x  + 22 = 0 $$

This is called the <b>characteristic equation.</b> We find that the two roots of the equation are x = 11 and x = 2. We call these the <b> characteristic roots </b>. Now what?

We can use these roots to find an explicit forumula by using the following formula. Constants are represented with 'c' and our roots are represented with 'r'. 

$$ a\_n = c\_1 (r\_1^ n)  + c\_2 (r\_2^ n) $$ 

Since we have the roots and we know the first 2 terms of the relation, we can solve for our constants using a system of equations.

$$ a\_0 = 3 =  c\_1 (11^ 0)  + c\_2 (2^ 0)
a\_1 = 15 =   c\_1 (11)  + c\_2 (2) $$

When we solve this, we find that $c\_1 =1, \: c\_2 = 2$. And now we're done. If we plug in our numbers we have:

$$a_n = 11^n + 2(2 ^n) $$

---


 <h4> What to do when you have 2+ of one root?</h4>
When we roots with a multiplicity of 2 and above, we use a different formula once we have the characteristic roots. Let's say our characteristic equation turns out to be \((x-2) ^2 \). The root 2 has a multiplicity of 2 and we'll use the following equation instead.
 
 $$a_n = c_1 (2 ^n) + c_2 n (2^n)$$
 

 
 
 
 <h4> What to do when you imaginary roots?</h4>
 Work as usual.
 
<h4> What do you do with a non-homogeneous eqation?</h4>
<s> <small> it's okay, Rachel, that's not on the final! </small></s>
Just kidding - I'll write a post on that later!







