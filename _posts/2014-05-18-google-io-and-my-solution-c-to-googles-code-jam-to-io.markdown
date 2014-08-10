---
layout: post
title: Google I/O! (and my solution C to Google's Code Jam to I/O)
date: 2014-05-18 10:47:41.000000000 -07:00
---
![](/content/images/2014/May/Screen_Shot_2014_05_16_at_6_42_53_PM.png)

"But wait Rachel - how are you an important partner to Google?" you may ask. And you would be right! 



## About Google Code Jam to I/O for Women

A few weeks ago, I was lucky enough to hear about the [Google Code Jam to I/O for Women](https://sites.google.com/site/codejamtoioforwomen/home). Any resident of the US could participate and the top 100 competitors receive a ticket to Google I/O 2014. 

It was my first coding competition of this sort, but it was a wonderful 2.5 hours of biting my nails, coding, and thinking that the competition was 1.5 hours long (oops). 

The competition consisted of 3 problems. The rules of the competition were similar to other Google Code Jam competitions (short input, long input, time penalty for wrong short answers). You could program in any language you wanted as long as it met the requirements in the rules.

I made the mistake of going between python and C++ (to be or not to be a semicolon??). And in the future I think I'll just stick with python. (I recommend using JetBrain's [PyCharm IDE](http://www.jetbrains.com/pycharm/); there's even a free community edition!)


## My answer to Question C

Anyway, I wanted to do a quick walk through of my solution to the last problem. Here's the problem statement:

>[...]  Saanvi is planning seating for the dinner with N people. [...] She's planning to write a program to compute the number of possible seating arrangements.

>There are K round tables at the dinner, numbered 1 through K. It is important to have exactly the same number of people sitting at each table. If that is impossible (N is not divisible by K), then the table with the most people must have at most one more person sitting at it than the table with the fewest people.

>Each of the N people will be assigned a unique number between 0 and N - 1. What matters is who is sitting next to whom, and not exactly where they're sitting. In other words, two arrangements, A and B, are considered different if there exists a pair of numbers, α and β, such that persons α and β are sitting next to each other at the same table in arrangement A, but they are not sitting next to each other in arrangement B.

>For example, if N is 5, and K is 2, we must have 3 people seated at one of the tables, and 2 people seated at the other table. Here is the list of all 10 of the possible arrangements: <br>

>[[0, 1, 2], [3, 4]]<br>
[[0, 1, 3], [2, 4]]<br>
[[0, 1, 4], [2, 3]]<br>
[[0, 2, 3], [1, 4]]<br>
[[0, 2, 4], [1, 3]]<br>
[[0, 3, 4], [1, 2]]<br>
[[1, 2, 3], [0, 4]]<br>
[[1, 2, 4], [0, 3]]<br>
[[1, 3, 4], [0, 2]]<br>
[[2, 3, 4], [0, 1]]<br>

>All other arrangements are similar to one of the arrangements above and are not counted as different. In particular, all of the following arrangements are considered to be the same:<br>
[[0, 1, 2], [3, 4] <br>
[[2, 0, 1], [3, 4]]<br>
[[1, 2, 0], [4, 3]]<br>
[[0, 2, 1], [3, 4]]<br>
[[3, 4], [0, 2, 1]]<br>

>This is because the following pairs of people (and no other pairs) are sitting next to each other in each of these 5 arrangements:<br>
0 and 1
0 and 2
1 and 2
3 and 4




At first, I was tempted to write a brute force solution to generate each permutation and check it with other generated solutions. This would pretty hideous time complexity, but it would probably be quick enough for the small input.

However, I realized that since the program only need the number of unique seating arrangements, and not the arrrangements themselveds, I could try to create a more mathematically elegant solution.

You can break the problem down into two parts: how many different ways can I distribute **N** people into **K** tables, and how many ways can I uniquely seat a table of **X** people.

###  Step 1: Different Ways To Split People into Tables

Since we don't care about the actual seating order of people in this step, we use combinations instrad of permutations. Basically, for each table for **X** people, we multiply our answer by N choose **X** (where N is the number of people who haven't been seated).

One trick is that since order doesn't matter, if we have **Y** tables of the same size (which happens often with this problem), we'll need to divide by **Y!**.

**PsuedoCode:**
<pre> <code>

//Calculating differnt ways to split people into tables
ways := 1
peopleAtTable = floor(N/K)

// Tables with one additional person
for tables with (peopleAtTable + 1) people:
	ways *= nCr(N, peopleAtTable + 1)
    N -= peopleAtTable +1
    
ways /= number of Tables with (peopleAtTable +1) people

for tables with (peopleatTable) people"
	ways *= nCr(N, peopleAtTable)
    N -= peopleAtTable

ways /= number of Tables with (peopleAtTable) people

// ways now has the number of different combinations you can split people into
</code> </pre>


### Step 2: Number of unique seating arrangements with X people.

Now that we have split people into tables, let's just worry about one table by itself. I couldn't think of way to calculate this off the top of my head. When this happens, I like to write down cases until I can come up with a pattern.

With 1 person, theres only 1 way to arrange the table. With 2 people and 3 person tables, the same is true. (They will always sit next to everyone at the table no matter how to order them).  Once we get to four people, there are 3 ways to arrange the table for this problem. For a 5 person table, there are 12 ways.

I started noticing a pattern - you're basically trying to calculate different permutations of people to not sit by. With a four person table, there are `nPr(3,1)` different ways to not sit by someone. With 5 people there are `nPr(4,2)` ways to choose who you're not sitting by. This can be expressed by `(X-1)! / (2)!`



## Solution

<pre><code>

import math

#Combinations
def nCr(n,r):
    f = math.factorial
    return f(n) / f(n-r) / f(r)



if __name__ == "__main__":
    # Getting Google Code Jam Style Input
    f = math.factorial
    numInputs = int(input())

    inputList = []
    for x in range(numInputs):
        s = input()
        inputList.append(s)


    # For each test case
    case= 1
    for x in range(numInputs):
        line = inputList[x]
        line = line.split(" ")

        n = int(line[0]) # total people
        k = int(line[1]) # number of tables

        answer = 1

        people = int(n/ k) #num people per smaller table
        numTablesWithExtraPerson = n % k

    # tables  with extra people to people % tables
        for y in range(numTablesWithExtraPerson):
            temp = nCr(n, people+1)
            n -= people+1
            #Step 2
            if people + 1 > 3:
                answer *= math.factorial(people)/2
            answer *= temp
            
        answer /= math.factorial(numTablesWithExtraPerson)

    # tables with normal people = tables -tablesWithExtra
        for w in range (k - numTablesWithExtraPerson):
            temp = nCr(n, people)
            n-= people
            #Step 2
            if people > 3:            
                answer *= f(people -1)/2
            answer *= temp
    
        answer /= math.factorial(k-numTablesWithExtraPerson)
        print ("Case #" + str(case) +  ": " + str(int(answer)) )
        case += 1


</code></pre>


I waited until after the competition was over to submit (perhaps I'm too risk adversive!) It passed both the large and small text files.










