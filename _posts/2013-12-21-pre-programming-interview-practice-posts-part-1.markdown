---
layout: post
title: Python Basics
date: 2013-12-21 22:17:05.000000000 -08:00
---
** Note: This post is not done yet! I published too early and now I'm too lazy to make a new one whoops...**


Hi there! I have my first programming interview coming up, so natrually,  I'm <s>really nervous </s> going to do a few practice problems to get more comfortable. 

I think I'll be interviewing in Python since my wise and talented friend (who reads my blog heh) advised me to do so. It'll probably allow me to write fewer lines of code and make fewer mistakes, but I've only started writing Python a few months ago so I definitely need to practice... nervous laughter.

---
<small> Note: Much of this content comes from python 3 documentation and the open soruce(!) [Runstone Interactive Python Guide](http://interactivepython.org/runestone/static/pythonds/index.html) which is amazing. I honestly can't recommend it enough. This blog post is basicaly information from both sources put together in a format that'll be quicker for me to review in the future. Seriously though, all of the lovely tables are from the runestone guide</small>

##Topics Covered

1. [Basics and  Arithmetic](#basic)
2. [Control Statements](#control)
3. [Basic Data Structures/Collections](#datastructs)
	- Built-in 
		- Lists
        - Strings
        - Tuples
    	- Sets
    	- Dictionaries
        - List Comprehension
    - Other fun
    	- Queues
        - Stacks 
        - Deques
    - When should I use what? (Efficiency)
4. [Functions](#functions)
	- Generators / Generator functions
5. [Classes](#classes)
6. [Sorts and Searches](#sands)
7. [Error Handling](#errors)
8. [Style](#style)

---
<a name="basic"/> </a>

## Basics and  Arithmetic
###Things to remember: 
- Division always returns a float even if it's a whole number. 
- Use `//` for int division. Always rounds towards minus infinity
- Use `**` for powers 
- `divmod(x,y)` returns the pair `x//y , x %y`. Might be useful for functions like converting numbers to a different base.
- Multiple Assignmentis wonderful `x,y = y,x` without a temp variable. Easy swapping especially for implementing sorts.
- Use `and, not, or` instead of `&&, ||` (this ain't C++, girl!)


---
<a name="control"/> </a>

##Control Statements
 **Selection**
 Here's an example. Similar to other languages.
<pre> <code> 
def shouldIWakeUp(time):
	if time < 5:
    	print("Omg go back to sleep ungodly hour")
    elif time < 9:
    	print("You could probably wake up")
    else:
    	print("You're probably late. Look what you did.")  
</code> </pre>

 
 **Iteration**
 Here's two exampes (while and for). Similar to other languages. Note the use of `range()` with the for loop.
 <pre> <code> 
while true:
	print("This is an infinite loop and" 
    "probably not the greatest example"
    "But at least I'm demonstrating string concatination!")
</code> </pre>

 <pre> <code> 
 for x in range(10, 0, -1):
 	print("Counting down:" + str(x) + "seconds to go!")
</code> </pre>

---

<a name="datastructs"/> </a>


##Basic Data Structures/Collections
###Built-in 
###The Sequential (Ordered) Collections - Lists, Strings, Tuples

<table border="1" class="docutils" id="tab-sequence">
<caption><strong>Operations on Any Sequence in Python </strong></caption>
<colgroup>
<col width="33%" />
<col width="17%" />
<col width="49%" />
</colgroup>
<thead valign="bottom">
<tr class="row-odd"><th class="head"><strong>Operation Name</strong></th>
<th class="head"><strong>Operator</strong></th>
<th class="head"><strong>Explanation</strong></th>
</tr>
</thead>
<tbody valign="top">
<tr class="row-even"><td>indexing</td>
<td>[ ]</td>
<td>Access an element of a sequence</td>
</tr>
<tr class="row-odd"><td>concatenation</td>
<td>+</td>
<td>Combine sequences together</td>
</tr>
<tr class="row-even"><td>repetition</td>
<td>*</td>
<td>Concatenate a repeated number of times</td>
</tr>
<tr class="row-odd"><td>membership</td>
<td>in</td>
<td>Ask whether an item is in a sequence</td>
</tr>
<tr class="row-even"><td>length</td>
<td>len</td>
<td>Ask the number of items in the sequence</td>
</tr>
<tr class="row-odd"><td>slicing</td>
<td>[ : ]</td>
<td>Extract a part of a sequence</td>
</tr>
</tbody>
</table>

*taken from Runestone Interactive*

**Lists**

<table border="1" class="docutils" id="tab-listmethods">
<caption><strong>Methods Provided by Lists in Python</strong></caption>
<colgroup>
<col width="23%" />
<col width="25%" />
<col width="52%" />
</colgroup>
<thead valign="bottom">
<tr class="row-odd"><th class="head"><strong>Method Name</strong></th>
<th class="head"><strong>Use</strong></th>
<th class="head"><strong>Explanation</strong></th>
</tr>
</thead>
<tbody valign="top">
<tr class="row-even"><td><tt class="docutils literal"><span class="pre">append</span></tt></td>
<td><tt class="docutils literal"><span class="pre">alist.append(item)</span></tt></td>
<td>Adds a new item to the end of a list</td>
</tr>
<tr class="row-odd"><td><tt class="docutils literal"><span class="pre">insert</span></tt></td>
<td><tt class="docutils literal"><span class="pre">alist.insert(i,item)</span></tt></td>
<td>Inserts an item at the ith position in a list</td>
</tr>
<tr class="row-even"><td><tt class="docutils literal"><span class="pre">pop</span></tt></td>
<td><tt class="docutils literal"><span class="pre">alist.pop()</span></tt></td>
<td>Removes and returns the last item in a list</td>
</tr>
<tr class="row-odd"><td><tt class="docutils literal"><span class="pre">pop</span></tt></td>
<td><tt class="docutils literal"><span class="pre">alist.pop(i)</span></tt></td>
<td>Removes and returns the ith item in a list</td>
</tr>
<tr class="row-even"><td><tt class="docutils literal"><span class="pre">sort</span></tt></td>
<td><tt class="docutils literal"><span class="pre">alist.sort()</span></tt></td>
<td>Modifies a list to be sorted</td>
</tr>
<tr class="row-odd"><td><tt class="docutils literal"><span class="pre">reverse</span></tt></td>
<td><tt class="docutils literal"><span class="pre">alist.reverse()</span></tt></td>
<td>Modifies a list to be in reverse order</td>
</tr>
<tr class="row-even"><td><tt class="docutils literal"><span class="pre">del</span></tt></td>
<td><tt class="docutils literal"><span class="pre">del</span> <span class="pre">alist[i]</span></tt></td>
<td>Deletes the item in the ith position</td>
</tr>
<tr class="row-odd"><td><tt class="docutils literal"><span class="pre">index</span></tt></td>
<td><tt class="docutils literal"><span class="pre">alist.index(item)</span></tt></td>
<td>Returns the index of the first occurrence of <tt class="docutils literal"><span class="pre">item</span></tt></td>
</tr>
<tr class="row-even"><td><tt class="docutils literal"><span class="pre">count</span></tt></td>
<td><tt class="docutils literal"><span class="pre">alist.count(item)</span></tt></td>
<td>Returns the number of occurrences of <tt class="docutils literal"><span class="pre">item</span></tt></td>
</tr>
<tr class="row-odd"><td><tt class="docutils literal"><span class="pre">remove</span></tt></td>
<td><tt class="docutils literal"><span class="pre">alist.remove(item)</span></tt></td>
<td>Removes the first occurrence of <tt class="docutils literal"><span class="pre">item</span></tt></td>
</tr>
</tbody>
</table>



**Strings** are immutable (remember this!)

*Methods*

- `str.find(char)` and `str.find(char, start, end)` to find the index of a char in a string (between start and end which are optional). `str.rfind()` works similarly but finds highest index.
- `str.split()` splits a string on whitespace or a string argument if supplied. 
- `str.lower()` and `str.upper()` return str in upper or lowercase.
- Use variabes in strings like so: `print ("Hello I'm %n and %a years old" % (name, age))

There are also some useful constants like `string.ascii_lowercase` etc.


**Tuples** are similar to lists but are *immutable* (even though they can contain mutable objects, like lists). They consist of values seperated by commas and as output are surrounded by `()`. 

Example Code:

<pre> <code>
t1 = 123, '24', True # make a tuple
x, y, z = t1 # sequence unpacking example
t2 = () # make empty tuple
t3 = ('cats' ,) # note the comma, tuple with one element
</code></pre>

---
###Unordered Collections (Dictionaries and Sets)

**Sets**

Sets are unordered and denoted using `{}`. You can use them similarly to sets in the mathematical sense. Similar to mathematical sets, they only contain unique elements. They're very useful! 

<table border="1" class="docutils" id="tab-setmethods">
<caption><strong> Methods Provided by Sets in Python</strong></caption>
<colgroup>
<col width="20%" />
<col width="27%" />
<col width="53%" />
</colgroup>
<thead valign="bottom">
<tr class="row-odd"><th class="head"><strong>Method Name</strong></th>
<th class="head"><strong>Use</strong></th>
<th class="head"><strong>Explanation</strong></th>
</tr>
</thead>
<tbody valign="top">
<tr class="row-even"><td><tt class="docutils literal"><span class="pre">union</span> </tt>*</td>
<td><tt class="docutils literal"><span class="pre">aset.union(otherset)</span></tt></td>
<td>Returns a new set with all elements from both sets</td>
</tr>
<tr class="row-odd"><td><tt class="docutils literal"><span class="pre">intersection</span></tt>*</td>
<td><tt class="docutils literal"><span class="pre">aset.intersection(otherset)</span></tt></td>
<td>Returns a new set with only those elements common to both sets</td>
</tr>
<tr class="row-even"><td><tt class="docutils literal"><span class="pre">difference</span></tt>*</td>
<td><tt class="docutils literal"><span class="pre">aset.difference(otherset)</span></tt></td>
<td>Returns a new set with all items from first set not in second</td>
</tr>
<tr class="row-odd"><td><tt class="docutils literal"><span class="pre">issubset</span></tt>*</td>
<td><tt class="docutils literal"><span class="pre">aset.issubset(otherset)</span></tt></td>
<td>Asks whether all elements of one set are in the other</td>
</tr>
<tr class="row-even"><td><tt class="docutils literal"><span class="pre">add</span></tt></td>
<td><tt class="docutils literal"><span class="pre">aset.add(item)</span></tt></td>
<td>Adds item to the set</td>
</tr>
<tr class="row-odd"><td><tt class="docutils literal"><span class="pre">remove</span></tt></td>
<td><tt class="docutils literal"><span class="pre">aset.remove(item)</span></tt></td>
<td>Removes item from the set</td>
</tr>
<tr class="row-even"><td><tt class="docutils literal"><span class="pre">pop</span></tt></td>
<td><tt class="docutils literal"><span class="pre">aset.pop()</span></tt></td>
<td>Removes an arbitrary element from the set</td>
</tr>
<tr class="row-odd"><td><tt class="docutils literal"><span class="pre">clear</span></tt></td>
<td><tt class="docutils literal"><span class="pre">aset.clear()</span></tt></td>
<td>Removes all elements from the set</td>
</tr>
</tbody>
</table>


*You can also use `|`, `&`, `-` and `<=` for these operations respectively. 

**Dictionaries**

Dictionaries use hashing to store key:value pairs. 

<table border="1" class="docutils" id="tab-dictmethods">
<caption><strong>Methods Provided by Dictionaries in Python</strong></caption>
<colgroup>
<col width="22%" />
<col width="19%" />
<col width="59%" />
</colgroup>
<thead valign="bottom">
<tr class="row-odd"><th class="head"><strong>Method Name</strong></th>
<th class="head"><strong>Use</strong></th>
<th class="head"><strong>Explanation</strong></th>
</tr>
</thead>
<tbody valign="top">
<tr class="row-even"><td><tt class="docutils literal"><span class="pre">keys</span></tt></td>
<td><tt class="docutils literal"><span class="pre">adict.keys()</span></tt></td>
<td>Returns the keys of the dictionary in a dict_keys object</td>
</tr>
<tr class="row-odd"><td><tt class="docutils literal"><span class="pre">values</span></tt></td>
<td><tt class="docutils literal"><span class="pre">adict.values()</span></tt></td>
<td>Returns the values of the dictionary in a dict_values object</td>
</tr>
<tr class="row-even"><td><tt class="docutils literal"><span class="pre">items</span></tt></td>
<td><tt class="docutils literal"><span class="pre">adict.items()</span></tt></td>
<td>Returns the key-value pairs in a dict_items object</td>
</tr>
<tr class="row-odd"><td><tt class="docutils literal"><span class="pre">get</span></tt></td>
<td><tt class="docutils literal"><span class="pre">adict.get(k)</span></tt></td>
<td>Returns the value associated with <tt class="docutils literal"><span class="pre">k</span></tt>, <tt class="docutils literal"><span class="pre">None</span></tt> otherwise</td>
</tr>
<tr class="row-even"><td><tt class="docutils literal"><span class="pre">get</span></tt></td>
<td><tt class="docutils literal"><span class="pre">adict.get(k,alt)</span></tt></td>
<td>Returns the value associated with <tt class="docutils literal"><span class="pre">k</span></tt>, <tt class="docutils literal"><span class="pre">alt</span></tt> otherwise</td>
</tr>
</tbody>
</table>


---

**List Comprehension**

<small>Note: You can also do this with sets, and dictionaries.
</small>

Python lets you iterate through lists in a very nice one-line format. For example `l = [ x for x in range(0, 100) if x % 2 == 0]` gives a list of even integers between 0 and 99.

**Nested List Comprehension**

One tip that helps me is to ask what the nestest list statement would be written out in loop form. Here's a general form for nested loop comprehension:

<pre> <code>
[ expression
	for x in y if  predicate(x)
    for y in z]
</code> </pre>

corresponds to 

<pre> <code>
for y in z:
	for x in y:
    	if predicate(x):
        	list.append(expression)
</code> </pre>

The ordering is pretty similar except for that the expression is before everything else.

---
### Other fun


#### Stacks 
Stacks are FILO (first in last out) structures. You can use a list for a stack (simply use `pop()` and `append()` since these are O(1) for lists).

#### Queues
Queues are FIFO (first in first out) and while you can implement one with a list (`.pop(0)` and `.append()`), it's probably not the best idea since once you pop the first term, all of the other term are shfted over in O(n) time.

Thankfully you can `import queue` and create one using `queue.Queue()`. Use `q.put(element)` and `q.get()`. 

####Deques
Can function as both queues and stacks.

---

###When should I use what? (Efficiency)



---
  
<a name="functions"/> </a>

## Functions 
**basics**

Here's an example:

<pre> <code>
def foo(argument):
	result = []
    #do something
    return result #if you want
</code> </pre>

**advanced topics**

-  You can have optional arguments by assigning a default value for them. (Watch out these are evaluated at the definition of the function, not at each function call).
-  You can also have an arbitrary number of arguments by using `*` or `**`
- To get command line arguments use `sys.argv`. 

Examples:
<pre> <code>
def foo(title = "Untitled" , *names, **capitals):
	print (title)
    #names is a tuple of your inputs
    for n in names:
    	print n
     #capitals is a dictionary
   	return capitals.keys() 
</code> </pre>


---

<a name="classes"/>  </a>

## Classes
**How to define a class**
<pre> <code>
#Basic Class Example
class Animal():
    def  __init__(self, name):
        self.name = name
        self.greet()

    def greet(self):
        print("Hi my name is " + self.name)

#Polymorphism example
class Chicken(Animal):
    def __init__(self, name):
        super().__init__(name)
        self.__eggsLaid = 0 #"private" member variable

    def greet(self):
        print("Cluck! My name is " + self.name)
        
    def layEgg(self):
		self.__eggsLaid += 1
        
class Cow(Animal):
    def greet(self):
        print("Moo! My name is " + self.name)
</code> </pre>

**Private**

To make things "private" add double underscores. Note that this isn't exactly like private in other languages like Java or C++. The underscores just "mangle" the name of the variable so it's harder to access. 


Sample Output:
<pre> <code>
>>> a = Animal("Annie")
Hi my name is Annie"
>> ch = Chicken("Betty")
Cluck! My name is Betty
</code> </pre>



**Multiple Inheritance and super()**

Let's update our above example. Remember that in Python, multiple polymorphism is depth-first, left to right. This means it will search the first base class (and it's related clases) first for the  attribute and if it's not found it will go to the next base class.

<pre> <code>

class FlyingThings:
    def __init__ (self):
        self.inAir = False
        self.greet()

    def greet(self):
        print("Vrooom!")

    def fly(self):
        print("Look at me fly!")
        self.inAir = True


class Chicken(Animal, FlyingThings):
    def __init__(self, name):
        super().__init__(name)
        self.__eggsLaid = 0 #"private" member variable

    def greet(self):
        print("Cluck! My name is " + self.name)
        
    def layEgg(self):
		self.__eggsLaid += 1

</code> </pre>

Sample Code:
<pre> <code>
>>> c = Chicken("Betty") 
Cluck! My name is Betty
>>> c.fly()
Look at me fly!
</code> </pre>



---

<a name="sands"/>  </a>

##Searches and Sorts

###Searches
####Linear
 Simply iterate along until you find your desired object or reach the end. O(n) time worst case. 
 
 <pre> <code>
 def linearSearch(lst, obj):
 	for x in range(0, len(lst)-1):
    	if lst[x] == obj:
        	return True
    return False
 </code> </pre>


####Binary
This allows you to search an ordered list in O(log  n). First compare to a midpoint value. There are 3 cases:

1. It's your value (congrats)
2. Your value is less than the midpoint (In which case you know if your value is in the list it falls in the first half of the list so you should search that)
3. Your value is greater than the midpoint (In which case you know if your value is in the list it falls in the second half of the list so you should search that)


Implementation:
<pre> <code>
def binarySearch(lst, obj):
	# Using iteration since it will take up less space (fewer function frames)
    start, end = 0, len(lst)
    while start != end:
    	midpoint = (start + end -1) // 2
        if obj == lst[midpoint]:
        	return True
        elif obj <= lst[midpoint]:
            end = midpoint - 1
        else 
        	start = midpoint + 1
    return False
</code> </pre>

###Sorts

I'm just going to write my implementations of them here and a brief summary to review for my interview. However, there are some great explainations and vizualizations out there if you're starting from scratch.


####Bubble

A pretty simple sort. Compare adjacent terms and swap if they're in the wrong order. Worst case: $O(n^2)$

<pre> <code>
def bubSort(lst):
	for i in range(len(lst)-1, 0, -1):
    	for j in range(i):
        	if lst[j] > lst[j+1]:
            	lst[j], lst[j+1] = lst[j+1], lst[j]
     return lst
</code> </pre>

####Selection

Another simple sort. Make *n* passes over a list and each time select the largest term and swap it into it's proper location.  Worst case: $O(n^2)$

<pre><code>
def selSort(lst):
	for i in range(len(lst), 0, -1):
    	#find the index of the largest in the pass
        indexLargest = 0
    	for j in range(i):
        	if lst[j] > lst[indxLargest]:
            	indexLargest = j
        #swap the largest to the correct spot
        lst[indexLargest], lst[i-1] = lst[i-1], lst[indexLargest] 
    return lst
</code> </pre>

####Insertion

With insertion sort, we start off with a "sorted" sublist of length 1. With each pass we look at the next element and insert it into the right place, shifting as appropriate. (This increases the length of the sorted sublist by 1 until it emcompasses all elements of the list.) Worst case: $O(n^2)$

<pre> <code>
def insSort(lst):
    for next in range(1,len(lst)):
        nextElt = lst[next]
        for j in range(next-1, -1, -1):
            if lst[j] > nextElt:
                lst[j+1] = lst[j]
                if j is 0:
                    lst[j] = nextElt
           else:
                lst[j+1] = nextElt
                break
    return lst
</code> </pre>

#####Merge

Things start to get fun/tricky here! This sort method uses a 'divide and conquer' approach to split the list into halves repeatedly, sort the halves and merget them together in order. Let's give this a go:

*note: I went out of my way to try to avoid slicing as an challenge on the RunseStone Interactive page (by passing in start and end indicies) though I ended up using one to make a copy of a list anyways.  :(*

<pre><code>
def mergeSort(lst, start = 0, end = None):
    if end is None:
        end = len(lst)
    if end - start > 1:
        midpoint = (start + end) //2
        mergeSort(lst, start, midpoint)
        mergeSort(lst, midpoint, end)
        # merge the two halves
        copy = lst[:]
        leftIndex = start
        rightIndex = midpoint
        for x in range(start, end):
            if rightIndex >= end or copy[leftIndex] < copy[rightIndex]:
                lst[x] = copy[leftIndex]
                leftIndex += 1
            else:
                lst[x] = copy[rightIndex]
                rightIndex += 1
    return lst
</code></pre>

Interesting link on making merge sort more efficient/tail recursive in Python: [here](http://blog.garillot.net/post/9048852162/how-do-you-make-a-recursive-merge-sort-more-efficient)


#####Quick
 
 Oy! I'm jetlagged been awake since 3:30 am so I'm going to write this one later!
 
 
#####Radix and Bucket



---

<a name="errors"/>  </a>

###  Error Handling




---

<a name="style"/>  </a>

### Style 
From the Google Python Style Guide

Naming Conventions I usually Ignore because Underscores smh
<table rules="all" border="1" cellspacing="2" cellpadding="2">      
      <tr>
        <th>Type</th>
        <th>Public</th>
        <th>Internal</th>
      </tr>
    	<tr>
        <td>Packages</td>
        <td><code>lower_with_under</code></td>
        <td></td>
      </tr>

      <tr>
        <td>Modules</td>
        <td><code>lower_with_under</code></td>
        <td><code>_lower_with_under</code></td>
      </tr>

      <tr>
        <td>Classes</td>
        <td><code>CapWords</code></td>
        <td><code>_CapWords</code></td>
      </tr>

      <tr>
        <td>Exceptions</td>
        <td><code>CapWords</code></td>
        <td></td>
      </tr>

      

      <tr>
        <td>Functions</td>
        <td><code>lower_with_under()</code></td>
        <td><code>_lower_with_under()</code></td>
      </tr>

      <tr>
        <td>Global/Class Constants</td>
        <td><code>CAPS_WITH_UNDER</code></td>
        <td><code>_CAPS_WITH_UNDER</code></td>
      </tr>

      <tr>
        <td>Global/Class Variables</td>
        <td><code>lower_with_under</code></td>
        <td><code>_lower_with_under</code></td>
      </tr>

      <tr>
        <td>Instance Variables</td>
        <td><code>lower_with_under</code></td>
        <td><code>_lower_with_under (protected) or __lower_with_under (private)</code></td>
      </tr>

      

      <tr>
        <td>Method Names</td>
        <td><code>lower_with_under()</code></td>
        <td><code>_lower_with_under() (protected) or __lower_with_under() (private)</code></td>
      </tr>

      <tr>
        <td>Function/Method Parameters</td>
        <td><code>lower_with_under</code></td>
        <td></td>
      </tr>

      <tr>
        <td>Local Variables</td>
        <td><code>lower_with_under</code></td>
        <td></td>
      </tr>
      

    </table>
    

- We always use the three double-quote """ format for doc strings (per PEP 257). A doc string should be organized as a summary line (one physical line) terminated by a period, question mark, or exclamation point, followed by a blank line, followed by the rest of the doc string starting at the same cursor position as the first quote of the first line. 

-  In Python, pydoc as well as unit tests require modules to be importable. Your code should always check if `if __name__ == '__main__':` before executing your main program so that the main program is not executed when the module is imported.
	All code at the top level will be executed when the module is imported. Be careful not to call functions, create objects, or perform other operations that should not be executed when the file is being pydoced.
    
<pre> <code>
	def main():
    	  ...

	if __name__ == '__main__':
    	main()
</code> </pre>
