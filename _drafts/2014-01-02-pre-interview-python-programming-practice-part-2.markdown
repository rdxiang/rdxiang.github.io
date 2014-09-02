---
layout: article
title: Pre-Interview Python Programming Practice Part 2
---
I was doing a few more practice interview problems today and thought I should write a small post since I'm proud of this one! This one happens to also be about nested list comprehension (I think I'm geetting the hang of it).

Here's the task:

> Given a N x N matrix representation of an image, rotate the matrix 90 degrees.


Here's my first solution (split into seperate lines for readability):

<pre> <code>
def rotate90(matrix):
	return [ [ matrix[row][col]
    		for row in range(len(matrix)-1, -1, -1) ] 
            for col in range(len(matrix))]
</code></pre>

It's nice and short! It has $O(n^2)$ time efficiency (I don't think there's anyways to go lower since you have to process all N x N pixels), but it also uses $O(n^2)$ memory by creating a new matrix when we can do the transformation in place. 

