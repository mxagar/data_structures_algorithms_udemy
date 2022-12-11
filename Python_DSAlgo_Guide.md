# Python for Algorithms, Data-Structures, and Interviews

This repository contains a compilation of algorithm & data structure implementations in python. I forked it originally from a repository by J.M. Portilla, who has a Udemy course on the topic:

[Python for Algorithms, Data-Structures, and Interviews](https://www.udemy.com/course/python-for-data-structures-algorithms-and-interviews)

I added comments and alternative implementations in some cases.

:warning: This repository is some kind of sandbox where I try things, so if don't expect it to be tidy and 100% PEP8-compliant :stuck_out_tongue_winking_eye:.

The present file is a non-exhaustive guide of the repository and the course.

Another related repository of mine is [python_interviews](https://github.com/mxagar/python_interviews). I created that repository while following the course / learning path [Ace the Python Coding Interview](https://www.educative.io/path/ace-python-coding-interview) in [educative.io](educative.io).

## Overview of Contents

- [Python for Algorithms, Data-Structures, and Interviews](#python-for-algorithms-data-structures-and-interviews)
  - [Overview of Contents](#overview-of-contents)
  - [1. Algorithm Analysis and Big O](#1-algorithm-analysis-and-big-o)
  - [2. Array Sequences](#2-array-sequences)
    - [Basics](#basics)
    - [Dynamic Arrays](#dynamic-arrays)
    - [Exercises](#exercises)
  - [3. Stacks, Queues and Deques](#3-stacks-queues-and-deques)
    - [Stacks](#stacks)
    - [Queues](#queues)
    - [Deques](#deques)
    - [Exercises](#exercises-1)
  - [4. Linked Lists](#4-linked-lists)
    - [Singly Linked Lists](#singly-linked-lists)
    - [Doubly Linked Lists](#doubly-linked-lists)
    - [Exercises](#exercises-2)
  - [5. Recursion](#5-recursion)
    - [Recursion Basics](#recursion-basics)
    - [Memoization](#memoization)
    - [Exercises](#exercises-3)
  - [6. Trees](#6-trees)
  - [7. Searching and Sorting](#7-searching-and-sorting)
  - [8. Graph Algorithms](#8-graph-algorithms)
  - [9. Riddles](#9-riddles)
  - [10. Python Tips \& Tricks](#10-python-tips--tricks)
  - [11. Other Topics](#11-other-topics)
    - [Salary Negotiation](#salary-negotiation)

## 1. Algorithm Analysis and Big O

- [Big-O Cheat Sheet](https://www.bigocheatsheet.com/)

## 2. Array Sequences

### Basics

- Arrays = lists.
- Arrays are collections of elements/objects that are stored in contiguous memory cells. `O(1)` access.
- Referential arrays: slices; they are pointers to the original objects!
- Mutable and immutable: can change or not; references are converted to new objects if we assign anew immutable to a referenced cell.
  - Mutable: lists, sets, dicts
  - Immutable: numbers, strings, tuples, frozen sets
- `append()` vs `extend()`
  - `append()`: appends a specified object at the end of the list.
  - `extend()`: extends the list by appending elements from the specified iterable.

```python
# Slicing is referential: we have pointers to original objects
temp = primes[3:6]
# But, if we change something in temp, a new object is created for that cell
# if the objects are immutable
temp[2] = 15 # primes is unchanged is we assign an immutable
# Shallow copy: references to original objects!
backup = list(primes)
# Deep copy: new list/array with new objects
from copy import deepcopy
backup = deepcopy(primes)
# All 4 cells reference the same object!
counters = [0]*4 # [0,0,0,0]
# But, if we add a value to one cell, a new object is created for that cell
# if the objects are immutable
counters[2] += 1 # [0,0,1,0]
# Extend takes references to original objects
prime.extend(extras)
```

### Dynamic Arrays

- Dynamic arrays: we can add elements to the array.
- Memory is allocated first and if we append new immutables, 50%-%100 of current allocation is added every n additions.

```python
import sys

data = []

# Size in bytes
sys.getsizeof(data) # 64, even though it contains nothing
data.append(1) # [1]
sys.getsizeof(data) # 96
```

- If we want to manually extend an array `a`:
  - Allocate new array `b` with larger capacity.
  - `b[i] = a[i]` and `a = b`.
  - Assign new element to `b` after last cell counter of `a`.
  - Free the old array `a`, typically handled by the garbage collector.
- Exercise: [`Dynamic Array Exercise.ipynb`](./Array%20Sequences/Dynamic%20Array%20Exercise.ipynb)
- Amortization: if we extend the capacity by doubling the current one, we achieve an amortized extension complexity of `O(1)*`.

### Exercises

The exercises with solutions and comments are located in [`Array Sequences`](./Array%20Sequences/):

- [`Anagram Check - SOLUTION.ipynb`](Array%20Sequences/Array%20Sequence%20Interview%20Questions%20-%20SOLUTIONS/Anagram%20Check%20-%20SOLUTION.ipynb)
  - Problem: Given two strings, check to see if they are anagrams.
  - Solution 1: Sort and compare strings.
  - Solution 2: Count dictionary: count adding with first string, subtract with second.
- [`Array Pair Sum - SOLUTION.ipynb`](./Array%20Sequences/Array%20Sequence%20Interview%20Questions%20-%20SOLUTIONS/Array%20Pair%20Sum%20-%20SOLUTION.ipynb)
  - Problem: Given an integer array, output all the *unique* pairs that sum up to a specific value `k`.
  - Solution: Iterate once array and check if difference to target is in array, using sets. Build a set of unique pairs.
- [`Find the Missing Element - SOLUTION.ipynb`](./Array%20Sequences/Array%20Sequence%20Interview%20Questions%20-%20SOLUTIONS/Find%20the%20Missing%20Element%20-%20SOLUTION.ipynb)
  - Problem: Consider an array of non-negative integers. A second array is formed by shuffling the elements of the first array and deleting a random element. Given these two arrays, find which element is missing in the second array.
  - Solution 1: sum both arrays and subtract; difference is missing value.
  - Solution 2: Sort array and check zipped pairs; when different, we have missing value.
  - Solution 3: count item occurrences in short array and then compare them to the ones in long array
- [`Largest Continuous Sum - SOLUTION.ipynb`](./Array%20Sequences/Array%20Sequence%20Interview%20Questions%20-%20SOLUTIONS/Largest%20Continuous%20Sum%20-%20SOLUTION.ipynb)
  - Problem: Given an array of integers (positive and negative) find the largest continuous sum.
  - Solution: Start summing max value so far, reset continuous sum is it starts decreasing, update maximum value if current sum is bigger.
- [`Sentence Reversal - SOLUTION.ipynb`](./Array%20Sequences/Array%20Sequence%20Interview%20Questions%20-%20SOLUTIONS/Sentence%20Reversal%20-%20SOLUTION.ipynb)
  - Problem: Given a string of words, reverse all the words.
  - Solution: Slice words, reverse list.
- [`String Compression -SOLUTION.ipynb`](./Array%20Sequences/Array%20Sequence%20Interview%20Questions%20-%20SOLUTIONS/String%20Compression%20-SOLUTION.ipynb)
  - Problem: Compress strings as 'AAABCCc' to 'A3B1C2c1'.
  - Solution: Start checking current and next string, if the same update counter, else, update compressed representation string.
- [`Unique Characters in String - SOLUTION.ipynb`](./Array%20Sequences/Array%20Sequence%20Interview%20Questions%20-%20SOLUTIONS/Unique%20Characters%20in%20String%20-%20SOLUTION.ipynb)
  - Problem: Given a string, determine if it is comprised of all unique characters.
  - Solution: Create and empty set which to which we add new characters; if the character to be added is in the set, return `False`.

## 3. Stacks, Queues and Deques

Stacks, Queues and Deques: linear, ordered data structures.

### Stacks

- Stack: LIFO = Last in, first out; pile of books: we take the last that was added.
  - `push()`: to the top.
  - `pop()`: from the top.
  - Both operations are performed at the top!
- **Pushing and then popping items from a stack reverses the order!**
- A list behaves like a stack, where:
  - `pop()` is the `pop()` function itself
  - and `append(item)` or `extend(item)` are the `push(item)` function.
- [`Implementation of Stack.ipynb`](./Stacks%2C%20Queues%20and%20Deques/Implementation%20of%20Stack.ipynb)

```python
class Stack:
    def __init__(self):
        self.items = []

    def isEmpty(self):
        return self.items == []

    def push(self, item):
        self.items.append(item)

    def pop(self):
        return self.items.pop()

    def peek(self):
        return self.items[len(self.items)-1]

    def size(self):
        return len(self.items)
```

### Queues

- Queues: FIFO: First in, first out: a waiting queue of people: the first that arrived is served first, and the next, next; first come, fist served.
  - `push()`: to the front; aka. `enqueue()`.
  - `pop()`: from the rear/back; aka. `dequeue()`.
  - The operations are performed at different ends of the collection!
- In contrast to stacks, queues don't reverse the order; we can achieve a queue behavior by using two stacks.
- A list can behave like a queue, with these functions:
  - `pop()` is `pop()` or `dequeue()`.
  - `insert(0,item)` is `push(item)` or `enqueue(item)`. 
- [`Implementation of Queue.ipynb`](./Stacks%2C%20Queues%20and%20Deques/Implementation%20of%20Queue.ipynb)

```python
class Queue:
    def __init__(self):
        self.items = []

    def isEmpty(self):
        return self.items == []

    def enqueue(self, item):
        self.items.insert(0,item)

    def dequeue(self):
        return self.items.pop()

    def size(self):
        return len(self.items)
```

:warning: Note that we add to the front, not to the rear!

### Deques

- Deque: double ended queue: we and add/remove items either to the front/rear of the data structure.
- Deques integrate the functionalities of stacks and queues; but we need to use them properly. **We need to picture what's going on as we use the basic operations and know where we're addding/subtracting items, i.e. at the rear or the front.**
- Lists can behave like deques by using these functions:
  - `addFront()`: `append(item)`
  - `addRear()`: `insert(0,item)`
  - `removeFront()`: `pop()`
  - `removeRear()`: `pop(0)`

```python
class Deque:
    def __init__(self):
        self.items = []

    def isEmpty(self):
        return self.items == []

    def addFront(self, item):
        self.items.append(item)

    def addRear(self, item):
        self.items.insert(0,item)

    def removeFront(self):
        return self.items.pop()

    def removeRear(self):
        return self.items.pop(0)

    def size(self):
        return len(self.items)
```

### Exercises

- [`Balanced Parentheses Check - SOLUTION.ipynb`](./Stacks%2C%20Queues%20and%20Deques/Stacks%2C%20Queues%2C%20Deques%20Interview%20Questions%20-SOLUTIONS/Balanced%20Parentheses%20Check%20-%20SOLUTION.ipynb)
  - Problem: Given a set of parenthesis, determine if it's balanced or not.
  - Solution: a stack is used to collect all opening parenthesis in the string; when we find a closing, we pop the last opening in the stack and check if it matches with the closing.
  - **This question is popular in interviews**.
- [`Implement a Queue -Using Two Stacks - SOLUTION.ipynb`](./Stacks%2C%20Queues%20and%20Deques/Stacks%2C%20Queues%2C%20Deques%20Interview%20Questions%20-SOLUTIONS/Implement%20a%20Queue%20-Using%20Two%20Stacks%20-%20SOLUTION.ipynb)
  - Problem: Given a stack class, implement a queue class using two stacks.
  - Solution: One stack reverses the order, but two stacks bring it back to the original order; a queue maintains the order, precisely.
  - **This question is popular in interviews**.

## 4. Linked Lists

### Singly Linked Lists

- Sequence of nodes, each containing 2 things:
  - A value or reference to an object.
  - Reference/pointer to the next node.
- We additionally have 2 special nodes:
  - `head`: reference to the first node in the list.
  - `tail`: reference to the last node, which points to `None`.
- We can add/remove values anywhere:
  - We need to locate the node by traversing the list: we already know where the `head` and `tail` are.
  - We create new node.
  - We update the references of the new node and the one before it.
- Access to the element `k` is `O(k)` bevcause we need to traverse the list from the tail, but insertion/deletion once we found it is `O(1)`.
- IMPORTANT: we only have the reference to the next node, not the previous! That makes necessary traversals in some cases. A doubly linked list solves that by keeping two references per node: the one to the next and the one to the previous.

Example of singly linked list which contains airport codes/names:

![Singly Linked List](./assets/singly_linked_list.png)

Inserting/removing a node in the `head` is `O(1)`; removing at the `tail` is `O(n)`, because we need to traverse until the predecessor of the `tail`!

![Singly Linked List: Insertion at Head](./assets/singly_linked_list_insert_head.png)

Implementation:

```python
class Node:
    def __init__(self,value):
        self.value = value
        self.nextnode = None # tail, default

a = Node(1)
b = Node(2)
c = Node(3)

a.nextnode = b
b.nextnode = c
```

### Doubly Linked Lists

- A doubly linked list is like a singly linked list, but each node has two references instead of one; so altogether, we have:
  - The value or a reference to an object.
  - A reference to the previous node.
  - A reference to the next node.
- As with singly lists, we have:
  - A `head`, aka. `header`
  - A `tail`, aka. `trailer`
  - Both are also called *sentinels*.
- Thus, we have `O(1)` insertion/deletion at `head`/`tail`.
- Access to the element `k` is still `O(k)` (we can traverse the list from the head or the tail), but insertion/deletion once we found it is `O(1)`.

Example of how insertion works in a doubly linked list:

![Doubly Linked List: Insertion](./assets/doubly_linked_list_insertion.png)

Implementation:

```python
class DoublyLinkedListNode(object):
    def __init__(self,value):
        self.value = value
        self.next_node = None
        self.prev_node = None

a = DoublyLinkedListNode(1)
b = DoublyLinkedListNode(2)
c = DoublyLinkedListNode(3)

# Setting b after a
b.prev_node = a
a.next_node = b

# Setting c after a
b.next_node = c
c.prev_node = b
```

### Exercises

- [`Singly Linked List Cycle Check - SOLUTION.ipynb`](./Linked%20Lists/Linked%20Lists%20Interview%20Problems/Singly%20Linked%20List%20Cycle%20Check%20-%20SOLUTION.ipynb)
  - Problem: Given a singly linked list, write a function which takes in the first node in a singly linked list and returns a boolean indicating if the linked list contains a "cycle". A cycle is when a node's next point actually points back to a previous node in the list. This is also sometimes known as a circularly linked list.
  - Solution: we implement two traverses simultaneously, one advances one node at each step (slow) the other two (fast); if there is a cycle, there is no tail, so the traverse never stops and eventually both traverses will meet.
- [`Linked List Reversal - SOLUTION.ipynb`](./Linked%20Lists/Linked%20Lists%20Interview%20Problems/Linked%20List%20Reversal%20-%20SOLUTION.ipynb)
  - Problem: Write a function to reverse a Linked List in place.
  - Solution: We traverse the list node by node and change the pointers to go in opposite directions.
- [`Linked List Nth to Last Node - SOLUTION.ipynb`](./Linked%20Lists/Linked%20Lists%20Interview%20Problems/Linked%20List%20Nth%20to%20Last%20Node%20-%20SOLUTION.ipynb)
  - Problem: Write a function that takes a head node and an integer value n and then returns the n-th to last node in the linked list.
  - Solution: We use two iterators/traverses; we advance the first iterator n steps, then we advance the first and second iterator together until the first reaches the end - the second iterator must be n steps away from the tail now. 
- [`Implement a Linked List -SOLUTION.ipynb`](./Linked%20Lists/Linked%20Lists%20Interview%20Problems/Implement%20a%20Linked%20List%20-SOLUTION.ipynb)
  - Problem: Implement a singly linked list and a doubly linked list; often, in interviews, we're not given their implementation.
  - Solution: The implementation is in the above sections.

## 5. Recursion

### Recursion Basics

- Recursion: when a function calls itself; it's a ways of avoiding loops.
- We distinguish:
  - The base case: when the recursion stops; when recursive cases don't work we use it.
  - Recursive cases: when the function is called again.

Example: Factorial of an integer:

```python
def factorial(n):
  if n < 2: # base case, n = 0; in this case, also 1 and for checks negative numbers
    return 1
  else: # recursive cases
    return n*factorial(n)
```

More examples in [`Recursion Homework Example Problems - SOLUTIONS.ipynb`](./Recursion/Recursion%20Homework%20Example%20Problems%20-%20SOLUTIONS.ipynb):

- Write a recursive function which takes an integer and computes the cumulative sum of 0 to that integer.
- Given an integer, create a function which returns the sum of all the individual digits in that integer.
- Split a stream of strings in words defined in a dictionary, if possible.

### Memoization

[Memoization](https://en.wikipedia.org/wiki/Memoization) consists in caching/storing often *expensive* solutions to a problem and re-using them later. If we apply memoization to recursion, we're doing **dynamic programming**.

Example of factorial function with memoization:

```python

def factorial(k):
    if k < 2: 
        return 1
    else: 
        return k * factorial(k-1)

# Function memoization
# Create cache for known results
# Note: we can also perform function memoization
# by defining inside the original function:
# - the dictionary
# - and a helper recursive function
# See Recursion Problem 4: Change-making problem
factorial_memo = {}

def factorial_1(k):
    if k < 2: 
        return 1
    if not k in factorial_memo:
        factorial_memo[k] = k * factorial(k-1)
    return factorial_memo[k]

# Class memoization
class Memoize:
    def __init__(self, f):
        self.f = f
        self.memo = {}
    def __call__(self, *args):
        if not args in self.memo:
            self.memo[args] = self.f(*args)
        return self.memo[args]

# 2.19 ms
%%timeit
factorial(20)

# 117 ns
%%timeit
factorial_1(20)

# 187 ns
%%timeit
factorial_2(20)
```

### Exercises

- [`Recursion Problem 1 - Reverse String - SOLUTION.ipynb`](./Recursion/Recursion%20Problems%20-%20%20SOLUTIONS/Recursion%20Problem%201%20-%20Reverse%20String%20-%20SOLUTION.ipynb)
  - Problem: Reverse a string with recursion.
  - Solution: Take last character and reverse rest recursively. Or, better, the other way around: take first character, call `reverse()` and return result with first character appended.
- [`Recursion Problem 2 - String Permutation- SOLUTION.ipynb`](./Recursion/Recursion%20Problems%20-%20%20SOLUTIONS/Recursion%20Problem%202%20-%20String%20Permutation-%20SOLUTION.ipynb)
  - Problem: Given a string, write a function that uses recursion to output a list of all the possible permutations of that string.
  - Solution: We traverse all letters in the string and permute the rest. The base case is one letter. Each permutation call returns the current letter and the permutation result concatenated. Note that a permutation is a factorial itself.
- [`Recursion Problem 3 - Fibonacci Sequence - SOLUTION.ipynb`](./Recursion/Recursion%20Problems%20-%20%20SOLUTIONS/Recursion%20Problem%203%20-%20Fibonacci%20Sequence%20-%20SOLUTION.ipynb)
  - Problem: Compute the Fibonacci sequence with recursion, dynamically (recursion + memoization) and iteratively.
  - Solution: Recursion is straightforward. The others are engineering:
    - Dynamic version: Memoization class is used directly.
    - Iterative version: Tuple unpacking can be used.
- [`Recursion Problem 4 - Coin Change - SOLUTION.ipynb`](./Recursion/Recursion%20Problems%20-%20%20SOLUTIONS/Recursion%20Problem%204%20-%20Coin%20Change%20-%20SOLUTION.ipynb)
  - Problem: Given a target amount n and a list (array) of distinct coin values, what's the fewest coins needed to make the change amount.
  - Solution: Have a look at the notebook. Basically, a dictionary is built to store previous values. Then, we build the base case and 
  - Very popular problem: [Change-making problem](https://en.wikipedia.org/wiki/Change-making_problem).


## 6. Trees

## 7. Searching and Sorting

## 8. Graph Algorithms

## 9. Riddles

## 10. Python Tips & Tricks

```python
###
# General
###

# Time execution time with several loops
%%timeit
foo()

# Maximum possible value
float("inf")

###
# Arrays / Lists, Strings, Dictionaries, Sets & Co.
###

# Last element
a[-1]

# Reverse
a[::-1]
# Equivalent
reversed(a)

# Sort
sorted(a)
a.sort() # in place

# Dictionaries
d = {}
d['key'] = 'value'
for k in d.keys():
    pass

# List/Dictionary comprehensions & enumerate
[v for v in range(10) if v%2 == 0] # [0, 2, 4, 6, 8]
{k:v for k,v in enumerate(range(0,10,2))} # {0: 0, 1: 2, 2: 4, 3: 6, 4: 8}

# Sets: nice way of reducing time complexity!
s = set()
s.add(obj) # can be an int, tuple, etc.
if e in s:
    print(f"{e} is in set s")

# Sums, Max, Min
a = [1,2,3]
s = sum(a) # 6
max_ = max(a) # 3
min_ = max(a) # 1

# Zip
arr1 = [1, 2, 3]
arr1 = [4, 5, 6]
for p in zip(arr1,arr2):
    print(p) # (1, 4), (2, 5), (3, 6)
    # unpacking
    a, b = p

# Tuple unpacking
a, b = my_tuple
# Note there is an order!
# First right side is evaluated
# then left side is assigned the right side
a, b = b, a + b
# Equivalent to
a_new = b
b_new = a + b
a = a_new
b = b_new
# Variable swap, without temp
x, y = y, x

# Collections: Counter, OrderedDict, defaultdict, namedtuple(), ...
# https://docs.python.org/3/library/collections.html
# Counter: 
c = Counter()                           # a new, empty counter
c = Counter('gallahad')                 # a new counter from an iterable
c = Counter({'red': 4, 'blue': 2})      # a new counter from a mapping
c = Counter(cats=4, dogs=8)             # a new counter from keyword args
c = Counter(['eggs', 'ham'])
c['bacon']                              # 0, there is no such key
c['sausage'] = 0                        # counter entry with a zero count
del c['sausage']                        # del actually removes the entry
Counter('abracadabra').most_common(3)   # [('a', 5), ('b', 2), ('r', 2)]
# defaultdict: if no key, it initializes it

# String handling basics
# Reverse a text
s = "Hello world"
s.split() # ["Hello", "world"]
" ".join(s[::-1]) # "world Hello"
# Remove spaces and lowercase letters
s1 = s1.replace(' ','').lower()
s2 = s2.replace(' ','').lower()
# Prefixes & suffixes
s.startswith('01_')
s.endswith('exe')



```



## 11. Other Topics

### Salary Negotiation

- [How to Negotiate Your Job Offer - Prof. Deepak Malhotra (Harvard Business School)](https://www.youtube.com/watch?v=km2Hd_xgo9Q)

