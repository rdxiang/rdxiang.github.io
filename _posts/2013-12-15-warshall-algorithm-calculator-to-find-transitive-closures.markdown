---
layout: post
title: Warshall Algorithm 'Calculator' to find Transitive Closures
date: 2013-12-15 10:54:56.000000000 -08:00
---
<h4> Background and Side Story</h4>
I've been trying out a few [Udacity](http://www.udacity.com) courses in my spare time, and after the first unit of CS253 (Web applications), I decided to try my hand at making one!

Granted this one is super super basic and probably like the least safe thing ever (oops...), but at least it's something! 

Fun fact: I missed out on watching <i> Catching Fire </i> with friends because I was took too long to finish my Discrete Math homework! (I realized I forgot to do a problem on transistive closures until a few moments before submitting /planned movie watching).  

Sad thing was that if I just programmed this instead, I probably would have been ale to make the movie! (It's very simple code, but at least it's faster then multiplying matricies or doing Warshall's Algorithm by hand!)


<h4> Actually relevant info! </h4>

[Here's](http://omglookitsanapp.appspot.com) a link to the page. It's running on Google's app engine since that's what the Udacity course teaches you to use. 

It uses Warshall's algorithm (which is pretty awesome!) to find the transistive closure of a $ n$ by $n$ matrix representing a relation and gives you $W\_1, W\_2 ... W\_n  $ in the process.  

Here's the python function I used:

<pre><code>
 def transitiveClosure (matrix):
    result = ""
    length = len(matrix)
    for k in range(0, length):
        for row in range(0, length):
            for col in range(0, length):
                matrix[row] [col] = matrix[row][col] or (matrix[row][k] and matrix[k][col])
        result += ("\n W" + str(k) +" is: \n" + str(matrix).replace("]," , "] \n") + "\n")
    result += ("\n Transitive closure is \n" + str(matrix).replace("]," , "]\n"))
    print result
    return result
</code> </pre>
