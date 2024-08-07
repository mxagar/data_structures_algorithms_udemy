# Python for Algorithms, Data-Structures, and Interviews

This repository contains a compilation of algorithms & data structures and their implementations in Python. I forked it originally from a repository by J.M. Portilla, who has a Udemy course on the topic:

[Python for Algorithms, Data-Structures, and Interviews](https://www.udemy.com/course/python-for-data-structures-algorithms-and-interviews)

Additionally, I added comments and alternative implementations, in some cases after checking other resources, such as (always referenced):

- Educative: [Ace the Python Coding Interview](https://www.educative.io/path/ace-python-coding-interview)
- DataCamp: [Writing Efficient Python Code](https://app.datacamp.com/learn/courses/writing-efficient-python-code)
- Cousera: [Accelerated Computer Science Fundamentals Specialization](https://www.coursera.org/specializations/cs-fundamentals); check my notes on the Specialization: [mxagar/accelerated_computer_science_coursera](https://github.com/mxagar/accelerated_computer_science_coursera).

**The present file is a (non-exhaustive) guide of the repository and the course.**

Another related repository of mine is [design_patterns_notes](https://github.com/mxagar/design_patterns_notes). I created that repository while following the Udemy course [Design Patterns in Python](https://www.udemy.com/course/design-patterns-python/) by Dmitri Nesteruk.

<!--
Another related repository of mine is [python_interviews](https://github.com/mxagar/python_interviews). I created that repository while following the course / learning path [Ace the Python Coding Interview](https://www.educative.io/path/ace-python-coding-interview) in [educative.io](educative.io).
-->

*:warning: Disclaimer: This repository is some kind of sandbox where I try things, so if don't expect it to be tidy and 100% PEP8-compliant :stuck_out_tongue_winking_eye:.*

## Overview of Contents

- [Python for Algorithms, Data-Structures, and Interviews](#python-for-algorithms-data-structures-and-interviews)
  - [Overview of Contents](#overview-of-contents)
  - [1. Algorithm Analysis and Big O](#1-algorithm-analysis-and-big-o)
    - [Complexity of Python Data Structures](#complexity-of-python-data-structures)
    - [Some Summary Figures](#some-summary-figures)
    - [Interesting Links](#interesting-links)
  - [2. Array Sequences](#2-array-sequences)
    - [Basics](#basics)
    - [Dynamic Arrays](#dynamic-arrays)
    - [Array Exercises](#array-exercises)
  - [3. Stacks, Queues and Deques](#3-stacks-queues-and-deques)
    - [Stacks](#stacks)
    - [Queues](#queues)
    - [Deques](#deques)
    - [Stack \& Queue Exercises](#stack--queue-exercises)
  - [4. Linked Lists](#4-linked-lists)
    - [Singly Linked Lists](#singly-linked-lists)
    - [Doubly Linked Lists](#doubly-linked-lists)
    - [List Exercises](#list-exercises)
  - [5. Recursion](#5-recursion)
    - [Recursion Basics](#recursion-basics)
    - [Memoization and Dynamic Programming](#memoization-and-dynamic-programming)
    - [Least Recently Used Cache: `lru_cache`](#least-recently-used-cache-lru_cache)
    - [Recursion Exercises](#recursion-exercises)
  - [6. Trees](#6-trees)
    - [Basics and Implementation](#basics-and-implementation)
    - [Traversals](#traversals)
    - [Priority Queues with Binary Heaps](#priority-queues-with-binary-heaps)
      - [Tree structure and node localization](#tree-structure-and-node-localization)
      - [Insertion of nodes](#insertion-of-nodes)
      - [Delete minimum value](#delete-minimum-value)
      - [Create a heap from a list](#create-a-heap-from-a-list)
      - [Final class with all the algorithms](#final-class-with-all-the-algorithms)
    - [Binary Search Trees (BST)](#binary-search-trees-bst)
      - [Insert a node](#insert-a-node)
      - [Retrieve a value](#retrieve-a-value)
      - [Delete a node](#delete-a-node)
      - [BST implementation code](#bst-implementation-code)
    - [Tree Exercises](#tree-exercises)
    - [Extra: Tries, aka. Prefix Trees](#extra-tries-aka-prefix-trees)
      - [Structure of a Trie](#structure-of-a-trie)
      - [Insertion in a Trie](#insertion-in-a-trie)
      - [Search in a Trie](#search-in-a-trie)
      - [Deletion in a Trie](#deletion-in-a-trie)
      - [Full Trie Implementation](#full-trie-implementation)
      - [Examples, Exercises](#examples-exercises)
  - [7. Searching and Sorting](#7-searching-and-sorting)
  - [8. Graph Algorithms](#8-graph-algorithms)
  - [9. Riddles and Brain Teasers](#9-riddles-and-brain-teasers)
    - [Examples, Exercises](#examples-exercises-1)
  - [10. Extra: Subsets - Combinations, Permutations and Co.](#10-extra-subsets---combinations-permutations-and-co)
    - [Permutations](#permutations)
    - [Combinations (without Replacement)](#combinations-without-replacement)
    - [Combinations with Replacement](#combinations-with-replacement)
    - [Python Implementations](#python-implementations)
    - [Example: Largest Palindromic Number](#example-largest-palindromic-number)
  - [11. Extra: Python Tips \& Tricks](#11-extra-python-tips--tricks)
    - [Interesting Articles, Links](#interesting-articles-links)
    - [Python Tools](#python-tools)
    - [Testing](#testing)
    - [Tricks](#tricks)
  - [12. Extra: Writing Efficient Python Code](#12-extra-writing-efficient-python-code)
  - [13. Design Patterns](#13-design-patterns)

## 1. Algorithm Analysis and Big O

> Big-O notation describes how quickly runtime will grow relative to the input as the input get arbitrarily large.

- We focus on the term with the largest degree for `n`.
- Added or multiplied constants are dropped: `O(2n) -> O(n)`.

Related topics to consider:

- We distinguish between worst, average and best cases; each case can have a different `O()`. Example algorithm that finds a match in a list:
  - Best case: `O(1)`, because the matched element is the first. **Try to always comment best cases**.
  - Worst case: `O(n)`, because the matched element is the last.
- Space complexity: related to memory allocation instead of time complexity.

### Complexity of Python Data Structures

Lists:

```python
# Slow
def method1():
    l = []
    for n in range(10000):
        l = l + [n]

# Faster
def method2():
    l = []
    for n in range(10000):
        l.append(n)

# Even faster
def method3():
    l = [n for n in range(10000)]

# Fastest!
def method4():
    l = list(range(10000))
```

![Python List Operations](./assets/python_list_operations.jpg)

Dictionaries = hash tables.

```python
d = {'k1':1, 'k2':2}
d['k1'] # 1
```

![Python Dictionary Operations](./assets/python_dict_operations.jpg)

### Some Summary Figures

![Complexity Graph](./assets/complexity_graph.jpg)

![Data Structure Operation Complexity](./assets/data_structure_operation_complexity.jpg)

![Array Sorting Complexity](./assets/array_sorting.jpg)

### Interesting Links

- [Big O in Plain English](https://stackoverflow.com/questions/487258/what-is-a-plain-english-explanation-of-big-o-notation/487278#487278).
- [Explanation of O log n](https://stackoverflow.com/questions/2307283/what-does-olog-n-mean-exactly).
- [Big-O Cheat Sheet](https://www.bigocheatsheet.com/).

## 2. Array Sequences

### Basics

- Arrays = in Python, Sequences, which can be
  - Lists
  - Tuples
  - Strings
- Arrays are collections of elements/objects that are stored in contiguous memory cells.
  - All cells have the same size.
  - `O(1)` access.
- Referential arrays: slices; they are pointers to the original objects!
- Mutable and immutable: can change or not; references are converted to new objects if we assign anew immutable to a referenced cell.
  - Mutable: lists, sets, dicts
  - Immutable: numbers, strings, tuples, frozen sets
- `append()` vs `extend()`
  - `append()`: appends a specified object at the end of the list.
  - `extend()`: extends the list by appending elements from the specified iterable. But references are added if we're using immutables, not new objects.

```python
# Slicing is referential: we have pointers to original objects
# That is, we're not creating new objects
temp = primes[3:6]
# But, if we change something in temp, a new object is created for that cell
# if the objects are IMMUTABLE
temp[2] = 15 # primes is unchanged is we assign an immutable
# Shallow copy: references to original objects!
backup = list(primes)
# Deep copy: new list/array with new objects
from copy import deepcopy
backup = deepcopy(primes)
# All 4 cells reference the same object!
counters = [0]*4 # [0,0,0,0]
# But, if we add a value to one cell, a new object is created for that cell
# if the objects are IMMUTABLE
counters[2] += 1 # [0,0,1,0]
# Extend takes references to original objects
prime.extend(extras)
```

### Dynamic Arrays

- Dynamic arrays: we can add elements to the array.
  - When an array is initiated, it has more capacity than its size.
- Memory is allocated first and if we append new immutables, 50%-%100 of current allocation is added every n additions. In theory, doubling the size when we run out of capacity leads to an amortized runtime of `O(1)*` for addition of elements to an array.

```python
import sys

data = []
len(data) # 0

# Size in bytes: Capacity
sys.getsizeof(data) # 64, even though it contains nothing
data.append(1) # [1]
sys.getsizeof(data) # 96
```

- If we want to **manually** extend an array `a`:
  - Allocate new array `b` with larger capacity.
  - `b[i] = a[i]` and `a = b`.
  - Assign new element to `b` after last cell counter of `a`.
  - Free the old array `a`, typically handled by the garbage collector.
- Exercise in which that manual allocation is implemented: [`Dynamic Array Exercise.ipynb`](./Array%20Sequences/Dynamic%20Array%20Exercise.ipynb)
- Amortization: if we extend the capacity by doubling the current one, we achieve an amortized extension complexity of `O(1)*`.

### Array Exercises

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
- [`String Compression - SOLUTION.ipynb`](./Array%20Sequences/Array%20Sequence%20Interview%20Questions%20-%20SOLUTIONS/String%20Compression%20-SOLUTION.ipynb)
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
- Note: I understand another implementation would be:
  - `push()` = `append()`
  - `pop()` = `pop(0)`
  - That seems to me more logically easy to understand; however, note that the order of the elements in the sequence (list) is the inverse.

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

### Stack & Queue Exercises

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
- Access to the element `k` is `O(k)` because we need to traverse the list from the tail, but insertion/deletion once we found it is `O(1)`.
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

### List Exercises

- [`Singly Linked List Cycle Check - SOLUTION.ipynb`](./Linked%20Lists/Linked%20Lists%20Interview%20Problems/Singly%20Linked%20List%20Cycle%20Check%20-%20SOLUTION.ipynb)
  - Problem: Given a singly linked list, write a function which takes in the first node in a singly linked list and returns a boolean indicating if the linked list contains a "cycle". A cycle is when a node's next point actually points back to a previous node in the list. This is also sometimes known as a circularly linked list.
  - Solution: we implement two traverses simultaneously, one advances one node at each step (slow) the other two (fast); if there is a cycle, there is no tail, so the traverse never stops and eventually both traverses will meet.
- [`Linked List Reversal - SOLUTION.ipynb`](./Linked%20Lists/Linked%20Lists%20Interview%20Problems/Linked%20List%20Reversal%20-%20SOLUTION.ipynb)
  - Problem: Write a function to reverse a Linked List in place.
  - Solution: We traverse the list node by node and change the pointers to go in opposite directions.
- [`Linked List Nth to Last Node - SOLUTION.ipynb`](./Linked%20Lists/Linked%20Lists%20Interview%20Problems/Linked%20List%20Nth%20to%20Last%20Node%20-%20SOLUTION.ipynb)
  - Problem: Write a function that takes a head node and an integer value n and then returns the n-th to last node in the linked list.
  - Solution: We use two iterators/traverses; we advance the first iterator n steps, then we advance the first and second iterator together until the first reaches the end - the second iterator must be n steps away from the tail now. 
- [`Implement a Linked List - SOLUTION.ipynb`](./Linked%20Lists/Linked%20Lists%20Interview%20Problems/Implement%20a%20Linked%20List%20-SOLUTION.ipynb)
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

### Memoization and Dynamic Programming

[Memoization](https://en.wikipedia.org/wiki/Memoization) consists in caching/storing often *expensive* solutions to a problem and re-using them later. If we apply memoization to recursion, we're doing **dynamic programming**. Memoization & dynamic programming are very important because solutions to seemingly simple problems can explode in complexity; for instance, have a look at the 

Example of factorial function with memoization:

```python

def factorial(k):
    if k < 2: 
        return 1
    else: 
        return k * factorial(k-1)

# Function memoization
# Create cache for known results

factorial_memo = {}

def factorial(k):
    if k < 2: 
        return 1
    # Memoization consists in checking if we have computed the value
    # already; if so, we return it, if not, we compute it with
    # recursion as store it!
    if not k in factorial_memo:
        factorial_memo[k] = k * factorial(k-1)
    return factorial_memo[k]

# Note: we can also perform function memoization
# by defining inside the original function:
# - the dictionary
# - and a helper recursive function
# See Recursion Problem 4: Change-making problem
def factorial_1(k):

    def factorial_recursive(k):
        if k < 2: 
            return 1
        # Memoization consists in checking if we have computed the value
        # already; if so, we return it, if not, we compute it with
        # recursion as store it!
        if not k in factorial_memo:
            factorial_memo[k] = k * factorial_1(k-1)
        return factorial_memo[k]
  
    factorial_memo = {}

    return factorial_recursive(k)

# Class memoization
class Memoize:
    def __init__(self, f):
        self.f = f
        self.memo = {}
    def __call__(self, *args):
        # Memoization consists in checking if we have computed the value
        # already; if so, we return it, if not, we compute it with
        # recursion as store it!
        if not args in self.memo:
            self.memo[args] = self.f(*args)
        return self.memo[args]

factorial_2 = Memoize(factorial)

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

### Least Recently Used Cache: `lru_cache`

Python has a built-in memoization decorator: `lru_cache`!

The cache discards the least recently used items first when the cache limit is reached. We can set the maximum size of the cache to limit memory usage.

```python
from functools import lru_cache

# The cache discards the least recently used items first when the cache limit is reached. 
# We can set the maximum size of the cache to limit memory usage.
# maxsize=None allows the cache to grow without bound
@lru_cache(maxsize=None)
def fibonacci(n):
    if n < 2:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

print(fibonacci(10))  # Outputs: 55
```

### Recursion Exercises

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
  - Solution: Have a look at the notebook. Basically, a dictionary is built to store previous values. Then, we build the base case and a recursion which stores previous values. The recursion considers all coins and the difference to the target of each coin. **This problem is very interesting; have a look at it!**
  - Very popular problem: [Change-making problem](https://en.wikipedia.org/wiki/Change-making_problem).

## 6. Trees

### Basics and Implementation

Some properties of trees:

- Trees have:
  - Root, branches & leaves.
  - Parent and children nodes; each child belongs to one parent.
- Each leaf node is unique.
- Each node can have
  - A name, also known as *key*.
  - A *value* or additional information, also known as *payload*; usually the payload is not used in the algorithms, but in practice it is what we're looking for.
- Edges are connections between parent-children nodes.
- The root node is the only node with no incomming edges.
- Leaf nodes have no children.
- We can create paths in trees when we traverse the nodes.
- There is a unique path from the root to a node.
- Nodes that share a parent are siblings.
- If each node has a maximum number of 2 children, we have a **binary tree**.
- **Level** of a node: number of edges on the path from the root to the node.
- **Height** of the tree: maximum level of an node in the tree.
- Trees can be defined recursively: a tree is a tree if it contains a root and optionally other subtrees. That definition is relevant, because it opens the door to recursive implementations.
- When processing trees, we can take entire branches (which are subtrees) and move them around; in fact, that's what is done when we add new nodes/branches in a given node level.

Example of a binary tree:

![Binary tree](./assets/binary_tree.jpg)

The simplest way (non-optimal) of implementing trees in python is using **lists of lists**:

- The first item is the root node, which contains its children nodes
- The second element is one subtree, i.e., a children *tree* of the root, which also contains its children nodes or *sub-trees*
- And so on...

```python
# This example is implemented with functions
# without OOP, but it could be implemented with classes
# as shown below

def BinaryTree(r):
    # first: root value
    # second: left subtree
    # third: right subtree
    # we could extend this structure to be a general (i.e., non-binary) tree
    return [r, [], []]

def insertLeft(root, newBranch):
    # We extract the element in position 1: left child
    t = root.pop(1)
    # If the left child is not empty,
    # insert it to the left of the new branch
    # else, insert a new barnch to the empty left child of root
    if len(t) > 1:
        root.insert(1, [newBranch, t, []])
    else:
        root.insert(1, [newBranch, [], []])
    return root

# Same as insertLeft, but with position 2 == right side
def insertRight(root,newBranch):
    t = root.pop(2)
    if len(t) > 1:
        # Insert existing prior child to the right == position 2
        root.insert(2, [newBranch, [], t])
    else:
        root.insert(2, [newBranch, [], []])
    return root

def getRootVal(root):
    return root[0]

def setRootVal(root, newVal):
    root[0] = newVal

def getLeftChild(root):
    return root[1]

def getRightChild(root):
    return root[2]

###

r = BinaryTree(3) #  [3, [], []]
insertLeft(r,4) # [3, [4, [], []], []]
insertLeft(r,5) # [3, [5, [4, [], []], []], []]
insertRight(r,6) # [3, [5, [4, [], []], []], [6, [], []]]
insertRight(r,7) # [3, [5, [4, [], []], []], [7, [], [6, [], []]]]
l = getLeftChild(r)
print(l) # [5, [4, [], []], []]
setRootVal(l,9)
print(r) # [3, [9, [4, [], []], []], [7, [], [6, [], []]]]
```

Another (more sophisticated) way of implementing a tree in python is using **Object-Oriented Programming (OOP) with nodes and references**:

```python
class BinaryTree(object):
    def __init__(self, rootObj):
        # The root expects a value to be stored
        # Here we use the attribute key, but I think
        # it would have been better to name it value/payload
        self.key = rootObj
        self.leftChild = None
        self.rightChild = None

    def insertLeft(self, newNode):
        # If we have no left child, create new and add newNode
        # to root; else, create new node, add to its left the current
        # left child and assign to the left child the newly create node
        # This approach is the same as with lists, but using classes,
        # nodes and references, instead
        if self.leftChild == None:
            self.leftChild = BinaryTree(newNode)
        else:
            # create a new node
            t = BinaryTree(newNode)
            # push to the left of the new node the current left node
            t.leftChild = self.leftChild
            # the current left node is assigned the new node!
            self.leftChild = t

    # Same as insertLeft but for the right side
    def insertRight(self, newNode):
        if self.rightChild == None:
            self.rightChild = BinaryTree(newNode)
        else:
            t = BinaryTree(newNode)
            t.rightChild = self.rightChild
            self.rightChild = t

    def getRightChild(self):
        return self.rightChild

    def getLeftChild(self):
        return self.leftChild

    def setRootVal(self, obj):
        self.key = obj

    def getRootVal(self):
        return self.key

###

r = BinaryTree('a')
print(r.getRootVal()) # a
print(r.getLeftChild()) # None
r.insertLeft('b')
print(r.getLeftChild()) # <__main__.BinaryTree object at 0x7faa19fce750>
print(r.getLeftChild().getRootVal()) # b
r.insertRight('c')
print(r.getRightChild()) # <__main__.BinaryTree object at 0x7fa9f06f2050>
print(r.getRightChild().getRootVal()) # c
r.getRightChild().setRootVal('hello')
print(r.getRightChild().getRootVal()) # hello

```

### Traversals

There are 3 basic tree traversal operations, depending on when we visit the root node:

- Preorder
  1. First, visit **root** node.
  2. Then, a recursive preorder traversal of **left** sub-tree.
  3. Finally, recursive preorder traversal of the **right** sub-tree.
- Inorder
  1. First, a recursive inorder traversal of **left** sub-tree.
  2. Then, visit **root** node.
  3. Finally, recursive inorder traversal of the **right** sub-tree.
- Postorder
  1. First, a recursive postorder traversal of **left** sub-tree.
  2. Then, recursive postorder traversal of the **right** sub-tree.
  3. Finally, visit **root** node.

Given the following book section tree, we would read the contents in the following order with each approach:

![Tree Example: Book](./assets/tree_example_book.jpg)

- Preorder: all sections and their text in the natural order: Book, Ch 1, S 1.1, S 1.2, S 1.2.1, S 1.2.2, ...
- Inorder: we go as deep as possible first: S 1.1, Ch 1, S 1.2.1, S 1.2, ...
- Postorder: we visit the leaves first!

We can implement the traversals in the class or outside; sometimes it's preferable to implement them outside, because traversing is not necessarily a function of the tree, but a method applied on it:

```python
def preorder(tree):
    if tree:
        print(tree.getRootVal())
        preorder(tree.getLeftChild())
        preorder(tree.getRightChild())

def inorder(tree):
    if tree:
        inorder(tree.getLeftChild())
        print(tree.getRootVal())
        inorder(tree.getRightChild())

def postorder(tree):
    if tree:
        postorder(tree.getLeftChild())
        postorder(tree.getRightChild())
        print(tree.getRootVal())

# If inside the class...
def preorder(self)
    print(self.key)
    if self.leftChild:
        self.leftChild.preorder()
    if self.rightChild:
        self.rightChild.preorder()
```

### Priority Queues with Binary Heaps

A priority queue is a queue, but its elements are ordered according to their relevance or priority, not their order of insertion. We can:

- Dequeue elements from the front, being the front item the most important one. The ones at the back have less priority.
- Enqueue elements: they are inserted in the position determined by their relevance.

A typical application is to order items in such a way that the minimum/maximum value is always at the front.

The classical way to implement a priority queue is a [**binary heap**](https://en.wikipedia.org/wiki/Binary_heap), which allows to enqueue/dequeue items with `O(logn)`! Following the application of keeping the min/max value at the front, we have two variations for binary heaps:

- Min heaps
- Max heaps

Some interesting additional material:

- The Wikipedia article on [**binary heaps**](https://en.wikipedia.org/wiki/Binary_heap)
- [`02_Ordered_DS`](https://github.com/mxagar/accelerated_computer_science_coursera/tree/main/02_Ordered_DS) from the Accelerated Computer Science Structures Specialization.

Altogether, the following sections/operations are covered here:

- [Tree structure and node localization](#tree-structure-and-node-localization)
- [Insertion of nodes](#insertion-of-nodes)
- [Delete minimum value](#delete-minimum-value)
- [Create heap from a list](#create-heap-from-a-list)
- [Final class with all the algorithms](#final-class-with-all-the-algorithms)

#### Tree structure and node localization

- We will work with binary trees which are **complete**, i.e.:
  - Perfect until the last level: all nodes filled in
  - In the last level, all the nodes pushed to the left
- In that case, the binary tree can be represented in an array (reserving the first element), and given the position `p` of a node, the position of its children is given by `2*p + c`, `c = 0` for the left child, `c = 1` for the right. Similarly, the parent of a node in position `p` will be `p//2`.
- Note that the first item in the list is not used so that the children-parent localization works as explained.

![Binary Tree: Heap](./assets/binary_tree_heap.jpg)

#### Insertion of nodes

Appending to the end of the list to insert a node is compliant with the tree structure, **BUT** it violates the heap structure property. To solve that, we can re-gain the heap structure simply by swaping items! That's implemented in the function `percUp()`: it swaps the current node with its parent if the parent has a larger value (in the case of a min heap). The action is called *percolation* or *heapifying up*.

![Heap: Percolate Up](./assets/heap_percolate_up_1.jpg)

![Heap: Percolate Up](./assets/heap_percolate_up_2.jpg)

![Heap: Percolate Up](./assets/heap_percolate_up_3.jpg)

#### Delete minimum value

Detecting the minimum value in a min heap is very easy: it's always going to be the root! However, popping it complicates the situation: we need to percolate down or swap nodes so that the heap structure is not violated.

The following steps are followed:

- We remove the root node, which contains the minimum element in the min heap.
- We replace the empty root with the last item in the heap list.
- We percolate down the new root: we check its children (left/right) and swap it with the smallest one; the process continues until the children beneath are larger.

![Heap: Percolate Down](./assets/heap_percolate_down_1.jpg)

![Heap: Percolate Down](./assets/heap_percolate_down_2.jpg)

![Heap: Percolate Down](./assets/heap_percolate_down_3.jpg)

![Heap: Percolate Down](./assets/heap_percolate_down_4.jpg)

#### Create a heap from a list

We could create a heap from a list by inserting the items one by one. However, a more efficient way, `O(n)`, is the following:

- We assign the unordered list to the heap list.
- Then, we start percolating down all the nodes in the heap/tree except the leaves; recall that each level, we double the nodes in a binary tree as a heap - thus, num_nodes//2 equals all nodes except the leaves. This works in `O(n)`.

![Heap from list](./assets/heap_from_list.jpg)

#### Final class with all the algorithms

```python
# Note: This is the implmentation of the Min Heap
# The children nodes have always a smaller value than their parents.
# The root node contains the smallest value in the tree.

class BinHeap:
    def __init__(self):
        # The first 0 element of the heap is not used
        # it's there for convenience in the tree node locailzation
        self.heapList = [0]
        self.currentSize = 0

    def percUp(self,i):
        # percUp() swaps the current node with its parent
        # if the parent has a larger value. That ensures
        # that the inserted node doesn't break the heap
        # structure in the array; i.e., to insert a node,
        # we simply append it to the end and then
        # apply percUp until the parent of the node is smaller.
        while i // 2 > 0:
            if self.heapList[i] < self.heapList[i // 2]:
                tmp = self.heapList[i // 2]
                self.heapList[i // 2] = self.heapList[i]
                self.heapList[i] = tmp
            i = i // 2

    def insert(self,k):
        # Appending to the end of the list to insert a node
        # is compliant with the tree structure, BUT
        # it violates the heap structure property.
        # To solve that, we can re-gain the heap structure
        # simply by swaping items! That's percUp()
        # percUp() swaps the current node with its parent
        # if the parent has a larger value.
        self.heapList.append(k)
        self.currentSize = self.currentSize + 1
        self.percUp(self.currentSize)

    def percDown(self,i):
        # We have removed the root node and replaced it with
        # the last node; now, we need to fix the heap structure
        # by percolating down the swaped node.
        # Basically, the new root is swaped with the smallest child
        # beneath until there's no smaller child.
        while (i * 2) <= self.currentSize:
            # Select smallest child: left or right?
            mc = self.minChild(i)
            # If current node is larger than the smallest child
            # SWAP both!
            if self.heapList[i] > self.heapList[mc]:
                tmp = self.heapList[i]
                self.heapList[i] = self.heapList[mc]
                self.heapList[mc] = tmp
            i = mc

    def minChild(self,i):
        # Select the smallest child of node i: left or right?
        if i * 2 + 1 > self.currentSize:
            return i * 2
        else:
            if self.heapList[i*2] < self.heapList[i*2+1]:
                return i * 2
            else:
                return i * 2 + 1

    def delMin(self):
        # We remove the root node, which contains the
        # minimum element in the min heap.
        # To ensure the heap structure, we need to
        # swap the nodes with percDown()
        retval = self.heapList[1] # root node
        # Swap last node to root position
        self.heapList[1] = self.heapList[self.currentSize]
        # Update size
        self.currentSize = self.currentSize - 1
        # Remove last node, because we moved it to the root
        self.heapList.pop()
        # Percolate down the new root node
        self.percDown(1)
        return retval

    def buildHeap(self,alist):
        # We assign the unordered list to the heap list
        # Then, we start percolating down all the nodes in the heap/tree
        # except the leaves; recall that each level, we double the nodes
        # in a binary tree as a heap - thus, num_nodes//2 equals all nodes
        # except the leaves.
        # This works in O(n)
        i = len(alist) // 2
        self.currentSize = len(alist)
        self.heapList = [0] + alist[:]
        while (i > 0):
            self.percDown(i)
            # Percolate all nodes up in the tree
            # Go up in the tree, that way we know that wan't below
            # has already been fixed.
            i = i - 1
```

### Binary Search Trees (BST)

Key-value mappings can be achieved in two major ways:

- Hash tables: dictionaries.
- Binary search trees.

Binary search trees are defined with the **BST property**: keys that are less than the parent are found in the left subtree and key that are larger than the parent are found in the right subtree.

![Binary Search Tree](./assets/binary_search_tree.jpg)

To implement a tree, two classes are defined:

- `TreeNode`
- `BinarySearchTree`

In the following, the most important operations are explained, followed by the code that implements the binary search tree:

- [Insert a node](#insert-a-node)
- [Retrieve a value](#retrieve-a-value)
- [Delete a node](#delete-a-node)
- [BST implementation code](#bst-implementation-code)

#### Insert a node

To **insert** a node with the key-value pair, we call a `put()` method, which inserts the node in its correct place by recursively calling itself and checking the left and right node keys. Note that the implementation shown below has an issue with duplicate keys: it is commented in the code.

Example of inserting a node with key 19:

![BST: Insert a Node](./assets/bst_insert_node.jpg)

#### Retrieve a value

To **retrieve the value of a node given its key**, we call the `get()` method, which searches recursively a given key until it is found of we end up in a leaf without having found the key. The method is easier than `put()` and it also uses a private recursive call.

#### Delete a node

Key deletion is the most challenging operation in BSTs.

Steps:

- First, find the node to delete by searching its key: `_get()`; the key can be:
  - not found: error
  - the root itself
  - another node
- Second, if the node is found, we call the function `remove()`.

The function `remove()` distinguishes 3 cases:

1. Case 1: The node to be deleted has no children, i.e., it's a leaf. In that case, we just delete the node by removing its reference in its parent.
2. Case 2: The node to be deleted has only one child. In that case, we promote the child to take the place of its removed parent, i.e., we replace the node with its child. The replacement needs to take into account whether the node is left/right/root and whether its child is left/right to set the references correctly.
3. Case 3: The node to be deleted has two children; it's the most general and difficult case. It works in two steps:
   - We find its successor: that's the node with the next largest key in the tree. The successor is found with `findSuccessor()` and `findMin()`.
   - We remove the successor with `spliceOut()`.
   - We replace the current deleted node with the successor key-value pair.

![BST: Delete node, case 1 - leaf](./assets/bst_delete_node_1.jpg)

![BST: Delete node, case 2 - one child](./assets/bst_delete_node_2.jpg)

![BST: Delete node, case 3 - two children](./assets/bst_delete_node_3.jpg)

#### BST implementation code

All the previous sections are implemented here in addition to the special methods `__setitem__`, `__getitem__`, `__delitem__`, `__iter__`, etc.

```python
# Basic node class
# which contains the key-value pair
# as well as references to 
# left child, right child, parent
class TreeNode:
    def __init__(self, key, val, left=None, right=None, parent=None):
        self.key = key
        self.payload = val
        self.leftChild = left
        self.rightChild = right
        self.parent = parent

    def hasLeftChild(self):
        return self.leftChild

    def hasRightChild(self):
        return self.rightChild

    def isLeftChild(self):
        return self.parent and self.parent.leftChild == self

    def isRightChild(self):
        return self.parent and self.parent.rightChild == self

    def isRoot(self):
        return not self.parent

    def isLeaf(self):
        return not (self.rightChild or self.leftChild)

    def hasAnyChildren(self):
        return self.rightChild or self.leftChild

    def hasBothChildren(self):
        return self.rightChild and self.leftChild

    def replaceNodeData(self, key, value, lc, rc):
        self.key = key
        self.payload = value
        self.leftChild = lc
        self.rightChild = rc
        if self.hasLeftChild():
            self.leftChild.parent = self
        if self.hasRightChild():
            self.rightChild.parent = self

    def __iter__(self):
        # Inorder iterator/traverse
        # yield returns a value and freezes the function 
        # so the next time it is called
        # it goes to the point it exited.
        # This code is recursive!
        # That's because its a generator in a loop
        # which calls the children of a tree every time.
        if self:
            if self.hasLeftChild():
                for elem in self.leftChild: # we're using the generator!
                    yield elem # this is a key!
            yield self.key # base case, recursion ends
            if self.hasRightChild():
                for elem in self.rightChild:
                    yield elem


class BinarySearchTree:
    def __init__(self):
        self.root = None
        self.size = 0

    def length(self):
        return self.size

    def __len__(self):
        # len(BinarySearchTree)
        return self.size

    def put(self, key, val):
        # Initial check + call private _put
        if self.root:
            self._put(key, val, self.root)
        else:
            self.root = TreeNode(key, val)
        self.size = self.size + 1

    def _put(self, key, val, currentNode):
        # Actual (private) put method that
        # 1) Checks whether the key is larger (right) / smaller (left) than the current node
        # 2) Recursively calls put() to insert the key-value pair in the correct place
        # HOWEVER: This method has an issue: it doesn't check
        # for duplicate keys, i.e., duplicates are inserted as the right child
        # so they are pushed down and never found, because the first one will be found first.
        # A solution is to REPLACE a node with a duplicate key.
        # To that end, I understand that we should add a 3rd new case in this if
        # and use replaceNodeData() in the case key == currentNode.key.
        if key < currentNode.key:
            # the key to be inserted is not smaller than the
            # search node we're in, thus, it should be put
            # on its left (BST property)
            if currentNode.hasLeftChild():
                # if there is a left child,
                # we need to use the put() method to push the correct node
                # downwards
                self._put(key, val, currentNode.leftChild)
            else:
                # if there's no left child, we create one
                currentNode.leftChild = TreeNode(key,
                                                 val,
                                                 parent=currentNode)
        else:
            # the key to be inserted is not smaller than the
            # search node we're in, thus, it should be put
            # on its right (BST property)
            if currentNode.hasRightChild():
                # if there is a right child,
                # we need to use the put() method to push the correct node
                # downwards
                self._put(key, val, currentNode.rightChild)
            else:
                # if there's no right child, we create one
                currentNode.rightChild = TreeNode(key,
                                                  val,
                                                  parent=currentNode)

    def __setitem__(self, k, v):
        # BinarySearchTree[k] = v
        self.put(k, v)

    def get(self, key):
        # Search for the key in the tree
        # and return its value if found.
        # The private _get() method is used recursively.
        if self.root:
            res = self._get(key, self.root)
            # If something not None found, return it
            if res:
                return res.payload
            else:
                return None
        else:
            return None

    def _get(self, key, currentNode):
        # If currentNode is None, return None
        if not currentNode:
            return None
        # If key found, return nodes's value/payload
        # Recursion ends here
        elif currentNode.key == key:
            return currentNode
        # If key is smaller than current node -> go to left (+ recursion)
        elif key < currentNode.key:
            return self._get(key,currentNode.leftChild)
        # If key is smaller than current node -> go to right (+ recursion)
        else:
            return self._get(key,currentNode.rightChild)

    def __getitem__(self, key):
        # v = BinarySearchTree[k]
        return self.get(key)

    def __contains__(self, key):
        # k in BinarySearchTree
        if self._get(key, self.root):
            return True
        else:
            return False

    def delete(self, key):
        if self.size > 1:
            nodeToRemove = self._get(key, self.root)
            if nodeToRemove:
                self.remove(nodeToRemove)
                self.size = self.size - 1
            else:
                raise KeyError('Error, key not in tree')
        elif self.size == 1 and self.root.key == key:
            self.root = None
            self.size = self.size - 1
        else:
            raise KeyError('Error, key not in tree')

    def __delitem__(self, key):
        # del BinarySearchTree[k]
        self.delete(key)

    def spliceOut(self):
        if self.isLeaf():
            if self.isLeftChild():
                self.parent.leftChild = None
            else:
                self.parent.rightChild = None
        elif self.hasAnyChildren():
            if self.hasLeftChild():
                if self.isLeftChild():
                    self.parent.leftChild = self.leftChild
                else:
                    self.parent.rightChild = self.leftChild
                    self.leftChild.parent = self.parent
        else:
            if self.isLeftChild():           
                self.parent.leftChild = self.rightChild
            else:
                self.parent.rightChild = self.rightChild
                self.rightChild.parent = self.parent

    def findSuccessor(self):
        # The successor is the next largest key in the tree
        succ = None
        if self.hasRightChild():
            # If the node has a right child, the next largest key
            # must be the minimum key down the right branch,
            # the leftmost key in the right branch.
            succ = self.rightChild.findMin()
        else:
            if self.parent: # not root, else None returned
                if self.isLeftChild():
                    succ = self.parent
                else:
                    self.parent.rightChild = None
                    succ = self.parent.findSuccessor()
                    self.parent.rightChild = self
        return succ

    def findMin(self):
        # The minimum value will be always to the left!
        # We keep going left until there no left child
        # Thus, the minimum value is the left-most leaf
        current = self
        while current.hasLeftChild():
            current = current.leftChild
        return current

    def remove(self, currentNode):
        if currentNode.isLeaf(): # Leaf: remove reference to in in parent
            if currentNode == currentNode.parent.leftChild:
                currentNode.parent.leftChild = None
            else:
                currentNode.parent.rightChild = None
        elif currentNode.hasBothChildren(): # Interior, 2 children
            succ = currentNode.findSuccessor()
            succ.spliceOut() # remove successor from tree
            # Replace removed node (current) with successor's key-value pair
            currentNode.key = succ.key
            currentNode.payload = succ.payload
        else: # This node has one child
            # We promote the child to take the place
            # of its removed parent; i.e., we replace the node
            # with its child. The replacement needs to take into account
            # whether the node is left/right/root
            # and whether its child is left/right
            # to set the references correctly.
            if currentNode.hasLeftChild():
                if currentNode.isLeftChild():
                    currentNode.leftChild.parent = currentNode.parent
                    currentNode.parent.leftChild = currentNode.leftChild
                elif currentNode.isRightChild():
                    currentNode.leftChild.parent = currentNode.parent
                    currentNode.parent.rightChild = currentNode.leftChild
                else: # root
                    currentNode.replaceNodeData(currentNode.leftChild.key,
                                    currentNode.leftChild.payload,
                                    currentNode.leftChild.leftChild,
                                    currentNode.leftChild.rightChild)
            else:
                if currentNode.isLeftChild():
                    currentNode.rightChild.parent = currentNode.parent
                    currentNode.parent.leftChild = currentNode.rightChild
                elif currentNode.isRightChild():
                    currentNode.rightChild.parent = currentNode.parent
                    currentNode.parent.rightChild = currentNode.rightChild
                else:
                    currentNode.replaceNodeData(currentNode.rightChild.key,
                                    currentNode.rightChild.payload,
                                    currentNode.rightChild.leftChild,
                                    currentNode.rightChild.rightChild)
```

### Tree Exercises

Recall that a tree can be simply implemented with a `Node` class:

```python
class Node:
    def __init__(self, key, value, left=None, right=None):
        self.key = key
        self.value = value
        self.left = left
        self.right = right
```

- [`Binary Search Tree Check - SOLUTION.ipynb`](./Trees/Trees%20Interview%20Problems%20-%20SOLUTIONS/Binary%20Search%20Tree%20Check%20-%20SOLUTION.ipynb):
  - Problem: Check if a tree is a Binary Search Tree (BST).
  - Solution: BST property is checked: given a node, its value must be between the values of the left and right children. The property is checked with recursive calls given a node.
- [`Tree Level Order Print - SOLUTION.ipynb`](./Trees/Trees%20Interview%20Problems%20-%20SOLUTIONS/Tree%20Level%20Order%20Print%20-%20SOLUTION.ipynb)
  - Problem: Given a binary tree of integers, print it in level order. The output will contain space between the numbers in the same level, and new line between different levels.
  - Solution: a FIFO queue (a list, basically) is filled with root node; then, we perform `pop(0)` from it, print the node's key and and `append()` its children in a while loop. This is a breadth-first traverse, like in the hierarchical VPS.
- [`Trim a Binary Search Tree - SOLUTION.ipynb`](./Trees/Trees%20Interview%20Problems%20-%20SOLUTIONS/Trim%20a%20Binary%20Search%20Tree%20-%20SOLUTION.ipynb)
  - Problem: Given the root of a binary search tree and 2 numbers min and max, trim the tree such that all the numbers in the new tree are between min and max (inclusive). The resulting tree should still be a valid binary search tree.
  - Solution: Post-order traversal (left, right, current) is performed checking the BST property in a recursive call. We visit worst-case all the nodes, so complexity is `O(n)`

### Extra: Tries, aka. Prefix Trees

Source: [Educative: Ace the Python Coding Interview](https://www.educative.io/path/ace-python-coding-interview); i.e., not the Udemy course.

Extra Folder: [`Trees/Tries/`](./Trees/Tries/).

Tries aka. Prefix Trees are derived from *retrieval* and are very efficient with strings. Typical applications:

- Dictionary word searches
- Search engine auto-suggestions: auto-completion, spell checking
- IP routing

Properties of a Trie:

- Similar to graphs: each node is a letter.
- Each node can point to `None` or other children nodes.
- The size is the number of symbols/characters; e.g., in English: 26.
- Depth: longest word it stores.
- The words are stored top-bottom; the last character has a flag `is_end_word = True`, i.e., leaf node.
- It provides the same path for words with the same prefix: `there, their, the`. This is key.

#### Structure of a Trie

![Structure of a Trie: top, thus, their](./assets/trie_structure.png)

A **Trie node**:

```python
class TrieNode:
    def __init__(self, char=''):
        # To store the value of a particular key
        self.char = char
        # This will store pointers to the children; size of alphabet
        self.children = [None] * 26
        # True if the node represents the end of word, i.e., leaf node
        self.is_end_word = False

trie_node = TrieNode('a')
print(trie_node.char)
```

The **Trie class**:

```python
class Trie:
    def __init__(self):
        self.root = TrieNode()  # Root node

    # Function to insert a key in the Trie
    def insert(self, key):
        pass

    # Function to search a given key in Trie
    def search(self, key):
        return False

    # Function to delete given key from Trie
    def delete(self, key):
        pass

```

In all cases

- We have a `root` without a key/letter, from which all operations start.
- Words are added/searched/deleted letter by letter.
- We can have several `is_end_word = True` flags along a path.

The complete class implementations can be found in [`Trees/Tries/Tries.ipynb`](./Trees/Tries/Tries.ipynb).

#### Insertion in a Trie

Insertion is in general as follows:

- for each key/letter, we check that it exists in the position it belongs to,
- if not present, we create a child/Trie node,
- if it is the last, we set `is_end_word = True`.

The letters are inserted/checked one by one, so if a word has `n` letters, the insertion complexity is `O(n)`.

There are 3 cases:

1. No common prefix
2. Common prefix
3. Word exists

**No common prefix:**

If we have a Trie with the word `t,h,e` in it and we want to insert `a,n,y`, we need to create a complete new branch, because no common prefix exists in the tree.

All the letters of the new word are inserted one by one.

For both `the` and `any`, their last letter is `end_of_word = True`.

![Trie: Insert with no common prefix](./assets/trie_insert_1.png)

**Common prefix:**

Another case: we have the word `t,h,e,i,r` in the tree and we'd like to insert `t,h,e,r,e`. We traverse the trie until the first `e` and create a new branch to add `r,e`.

![Trie: Insert with common prefix](./assets/trie_insert_2.png)

![Trie: Insert with common prefix](./assets/trie_insert_3.png)

**Word exists:**

If the word exists in the trie or it is a substring of a word in the trie, we set `end_of_word = True` in the appropriate letter, even it is not a leaf.

Example: we have the word `t,h,e,i,r` and want to insert `t,h,e`; we go one by one through the *new* set of letters and check the path exists, when the last letter is visited, its node is set to be `end_of_word = True` if it is not already.

![Trie: word as substring](./assets/trie_insert_4.png)

**Insert Method**

```python
class Trie:
    def __init__(self):
        self.root = TrieNode()  # Root node

    # Function to get the index of character 't'
    # Alphabet ordinal indices: 0-25
    def get_index(self, t):
        return ord(t) - ord('a')

    # Function to insert a key in the Trie
    # key = word; composed by letters
    # For a word of n letters,
    # O(n) since we need to make n iterations
    def insert(self, key):
        if key is None:
            return False  # None key

        key = key.lower()  # Keys are stored in lowercase
        current = self.root

        # Iterate over each letter in the key
        # If the letter exists, go down a level
        # Else simply create a TrieNode and go down a level
        for letter in key:
            index = self.get_index(letter)

            if current.children[index] is None:
                current.children[index] = TrieNode(letter)
                print(letter, "inserted")

            current = current.children[index]

        current.is_end_word = True
        print("'" + key + "' inserted")

    # Function to search a given key in Trie
    def search(self, key):
        return False

    # Function to delete given key from Trie
    def delete(self, key):
        pass


# Input keys (use only 'a' through 'z')
keys = ["the", "a", "there", "answer", "any",
        "by", "bye", "their", "abc"]

t = Trie()
print("Keys to insert:\n", keys)

# Construct Trie
for words in keys:
    t.insert(words)
```

#### Search in a Trie

> If we want to check whether a word is present in the trie or not, we just need to keep tracing the path in the trie corresponding to the characters/letters in the word.

Again, we have 3 cases:

1. No common prefix, non-existent word
2. Common prefix, word exists as a substring
3. Word exists

Let's consider the case in which we have a trie with the word `b,e,d` in it; we want to search

1. `bedroom`: not in it
   - we reach `None` before reaching the last letter of the query word
   - or, we reach `end_of_word = True` before reaching the last letter of the query word
2. `be`: in it as a substring, but not found!
   - we can track the path of the query word, but its last letter is not set as `end_of_word = True`; **thus, `be` will not be found!**
3. `bed`: entirely in it; success!
   - the query word letters are found one by one and the last letter is set to be `end_of_word = True` in the trie

![Trie: Search](./assets/trie_search.png)

Length of word `h` -> search complexity `O(h)`.

Implementation:

```python
class Trie:
    def __init__(self):
        self.root = TrieNode()  # Root node

    # Function to get the index of character 't'
    def get_index(self, t):
        return ord(t) - ord('a')

    # Function to insert a key in the Trie
    def insert(self, key):
        if key is None:
            return False  # None key

        key = key.lower()  # Keys are stored in lowercase
        current = self.root

        # Iterate over each letter in the key
        # If the letter exists, go down a level
        # Else simply create a TrieNode and go down a level
        for letter in key:
            index = self.get_index(letter)

            if current.children[index] is None:
                current.children[index] = TrieNode(letter)
                print(letter, "inserted")

            current = current.children[index]

        current.is_end_word = True
        print("'" + key + "' inserted")

    # Function to search a given key in Trie
    def search(self, key):
        if key is None:
            return False  # None key

        key = key.lower()
        current = self.root

        # Iterate over each letter in the key
        # If the letter doesn't exist, return False
        # If the letter exists, go down a level
        # We will return true only if we reach the leafNode (is_end_word = True)
        # and have traversed the Trie based on the length of the key
        for letter in key:
            index = self.get_index(letter)
            if current.children[index] is None:
                return False
            current = current.children[index]

        if current is not None and current.is_end_word:
            return True

        return False

    # Function to delete given key from Trie
    def delete(self, key):
        pass


# Input keys (use only 'a' through 'z')
keys = ["the", "a", "there", "answer", "any",
        "by", "bye", "their", "abc"]
res = ["Not present in trie", "Present in trie"]

t = Trie()
print("Keys to insert: \n", keys)

# Construct Trie
for words in keys:
    t.insert(words)

# Search for different keys
print("the --- " + res[1] if t.search("the") else "the --- " + res[0])
print("these --- " + res[1] if t.search("these") else "these --- " + res[0])
print("abc --- " + res[1] if t.search("abc") else "abc --- " + res[0])
```

#### Deletion in a Trie

> While deleting a node, we need to make sure that the node that we are trying to delete does not have any further child branches. If there are no branches, then we can easily remove the node.

The first condition to delete a word is that its search should return a positive answer; then, again, we have 3 case:

1. Word with No Suffix or Prefix.
2. Word is a Prefix.
3. Word Has a Common Prefix.

Length of word `h` -> delete complexity `O(h)`.

**Word with No Suffix or Prefix:**

If the word to be deleted is a single path with no suffixes of prefixes, **we can simply delete all the nodes in its path, starting from the leaf up to the root.**

Example: we delete `bat`, which is a unique branch or a non-shared path.

![Trie: Delete Word with No Suffix or Prefix](./assets/trie_delete_1.png)

**Word is a Prefix:**

If the word is a prefix, **we navigate to its leaf node and set `end_of_word = False`.**

Example: we delete `the`, which is a prefix of `their`.

![Trie: Word is a Prefix](./assets/trie_delete_2.png)

**Word Has a Common Prefix:**

If the word we want to delete has an ending branch/path only associated with it (i.e., no more children), but a prefix path shared with other words, the nodes of the ending non-shared path/branch are removed starting from the leaf node up to the node where the ending branch started.

Example: we delete `their`, which has the prefix `the`, by deleting the nodes `r,i`.

![Trie: Word Has a Common Prefix](./assets/trie_delete_3.png)

![Trie: Word Has a Common Prefix](./assets/trie_delete_4.png)

Implementation:

```python
class Trie:
    def __init__(self):
        self.root = TrieNode()  # Root node

    # Function to get the index of character 't'
    def get_index(self, t):
        return ord(t) - ord('a')

    # Function to insert a key in the Trie
    def insert(self, key):
        if key is None:
            return False  # None key

        key = key.lower()  # Keys are stored in lowercase
        current = self.root

        # Iterate over each letter in the key
        # If the letter exists, go down a level
        # Else simply create a TrieNode and go down a level
        for letter in key:
            index = self.get_index(letter)

            if current.children[index] is None:
                current.children[index] = TrieNode(letter)
                print(letter, "inserted")

            current = current.children[index]

        current.is_end_word = True
        print("'" + key + "' inserted")

    # Function to search a given key in Trie
    def search(self, key):
        if key is None:
            return False  # None key

        key = key.lower()
        current = self.root

        # Iterate over each letter in the key
        # If the letter doesn't exist, return False
        # If the letter exists, go down a level
        # We will return true only if we reach the leafNode and
        # have traversed the Trie based on the length of the key

        for letter in key:
            index = self.get_index(letter)
            if current.children[index] is None:
                return False
            current = current.children[index]

        if current is not None and current.is_end_word:
            return True

        return False

    # Recursive function to delete given key
    # key = word
    # current = root in the beginning, a node in recursive calls
    # length = len(key)
    # level = 0, 1, ..., len(key) 
    def delete_helper(self, key, current, length, level):
        deleted_self = False

        if current is None:
            print("Key does not exist")
            return deleted_self

        # Base Case:
        # We have reached at the node which points
        # to the alphabet at the end of the key,
        # i.e., when the algorithm reaches the last node of the key
        if level == length:
            # If there are no nodes ahead of this node in
            # this path, then we can delete this node
            print("Level is length, we are at the end")
            if current.children.count(None) == len(current.children):
                print("- Node", current.char, ": has no children, delete it")
                current = None
                deleted_self = True

            # If there are nodes ahead of current in this path
            # Then we cannot delete current. We simply unmark this as leaf
            else:
                print("- Node", current.char, ": has children, don't delete \
                it")
                current.is_end_word = False
                deleted_self = False

        else:
            index = self.get_index(key[level])
            print("Traverse to", key[level])
            child_node = current.children[index]
            child_deleted = self.delete_helper(
                key, child_node, length, level + 1)
            # print( "Returned from", key[level] , "as",  child_deleted)
            if child_deleted:
                # Setting children pointer to None as child is deleted
                print("- Delete link from", current.char, "to", key[level])
                current.children[index] = None
                # If current is a leaf node then
                # current is part of another key
                # So, we cannot delete this node and it's parent path nodes
                if current.is_end_word:
                    print("- - Don't delete node", current.char, ": word end")
                    deleted_self = False

                # If child_node is deleted and current has more children
                # then current must be part of another key
                # So, we cannot delete current Node
                elif current.children.count(None) != len(current.children):
                    print("- - Don't delete node", current.char, ": has \
                    children")
                    deleted_self = False

                # Else we can delete current
                else:
                    print("- - Delete node", current.char, ": has no children")
                    current = None
                    deleted_self = True

            else:
                deleted_self = False

        return deleted_self

    # Function to delete given key from Trie
    # key = word
    # Trivial cases handled and recursive function delete_helper called
    def delete(self, key):
        if self.root is None or key is None:
            print("None key or empty trie error")
            return
        print("\nDeleting:", key)
        self.delete_helper(key, self.root, len(key), 0)


# Input keys (use only 'a' through 'z')
keys = ["the", "a", "there", "answer", "any",
        "by", "bye", "their", "abc"]
res = ["Not present in trie", "Present in trie"]

t = Trie()
print("Keys to insert: \n", keys)

# Construct Trie
for words in keys:
    t.insert(words)

# Search for different keys
print("the --- " + res[1] if t.search("the") else "the --- " + res[0])
print("these --- " + res[1] if t.search("these") else "these --- " + res[0])
print("abc --- " + res[1] if t.search("abc") else "abc --- " + res[0])

# Delete abc
t.delete("abc")
print("Deleted key \"abc\" \n")

print("abc --- " + res[1] if t.search("abc") else "abc --- " + res[0])
```

#### Full Trie Implementation

File: [`Trees/Tries/Tries - Problems - SOLUTIONS/trie.py`](./Trees/Tries/Tries%20-%20Problems%20-%20SOLUTIONS/trie.py)

```python
"""This module contains the implementation
of a Trie data structure for English words.
"""

class TrieNode:
    def __init__(self, char=''):
        # To store the value of a particular key
        self.char = char
        # This will store pointers to the children; size of alphabet
        self.children = [None] * 26
        # True if the node represents the end of word, i.e., leaf node
        self.is_end_word = False

class Trie:
    def __init__(self):
        self.root = TrieNode()  # Root node

    # Function to get the index of character 't'
    def get_index(self, t):
        return ord(t) - ord('a')

    # Function to insert a key in the Trie
    def insert(self, key):
        if key is None:
            return False  # None key

        key = key.lower()  # Keys are stored in lowercase
        current = self.root

        # Iterate over each letter in the key
        # If the letter exists, go down a level
        # Else simply create a TrieNode and go down a level
        for letter in key:
            index = self.get_index(letter)

            if current.children[index] is None:
                current.children[index] = TrieNode(letter)

            current = current.children[index]

        current.is_end_word = True

    # Function to search a given key in Trie
    def search(self, key):
        if key is None:
            return False  # None key

        key = key.lower()
        current = self.root

        # Iterate over each letter in the key
        # If the letter doesn't exist, return False
        # If the letter exists, go down a level
        # We will return true only if we reach the leafNode and
        # have traversed the Trie based on the length of the key

        for letter in key:
            index = self.get_index(letter)
            if current.children[index] is None:
                return False
            current = current.children[index]

        if current is not None and current.is_end_word:
            return True

        return False

    # Recursive function to delete given key
    # key = word
    # current = root in the beginning, a node in recursive calls
    # length = len(key)
    # level = 0, 1, ..., len(key) 
    def delete_helper(self, key, current, length, level):
        deleted_self = False

        if current is None:
            return deleted_self

        # Base Case:
        # We have reached at the node which points
        # to the alphabet at the end of the key,
        # i.e., when the algorithm reaches the last node of the key
        if level == length:
            # If there are no nodes ahead of this node in
            # this path, then we can delete this node
            if current.children.count(None) == len(current.children):
                current = None
                deleted_self = True

            # If there are nodes ahead of current in this path
            # Then we cannot delete current. We simply unmark this as leaf
            else:
                current.is_end_word = False
                deleted_self = False

        else:
            index = self.get_index(key[level])
            child_node = current.children[index]
            child_deleted = self.delete_helper(
                key, child_node, length, level + 1)
            # print( "Returned from", key[level] , "as",  child_deleted)
            if child_deleted:
                # Setting children pointer to None as child is deleted
                current.children[index] = None
                # If current is a leaf node then
                # current is part of another key
                # So, we cannot delete this node and it's parent path nodes
                if current.is_end_word:
                    deleted_self = False

                # If child_node is deleted and current has more children
                # then current must be part of another key
                # So, we cannot delete current Node
                elif current.children.count(None) != len(current.children):
                    deleted_self = False

                # Else we can delete current
                else:
                    current = None
                    deleted_self = True

            else:
                deleted_self = False

        return deleted_self

    # Function to delete given key from Trie
    # key = word
    # Trivial cases handled and recursive function delete_helper called
    def delete(self, key):
        if self.root is None or key is None:
            return
        self.delete_helper(key, self.root, len(key), 0)

```

#### Examples, Exercises

- [Trees/Tries/Tries - Problems - SOLUTIONS/01_Trie_Total_Number_Words.ipynb](./Trees/Tries/Tries%20-%20Problems%20-%20SOLUTIONS/01_Trie_Total_Number_Words.ipynb):
  - Problem: Given a Trie with several words in it, count them.
  - Solution: The number of words in a tree amounts to the number of leafs in it, i.e., we need to count the number of nodes with `end_of_word = True`. We can create a recursive function which increases counter if a leaf node is found and calls itself if node children exist.
- [Trees/Tries/Tries - Problems - SOLUTIONS/02_Trie_All_Words.ipynb](./Trees/Tries/Tries%20-%20Problems%20-%20SOLUTIONS/02_Trie_All_Words.ipynb):
  - Problem: Given a Trie with several words in it, print all the words.
  - Solution: Depth-First Search is implemented recursively and using some helper functions (e.g., get maximum tree depth). The returned list is lexicographically ordered! The complexity is `O(n)`.
- [Trees/Tries/Tries - Problems - SOLUTIONS/03_Trie_List_Sort.ipynb](./Trees/Tries/Tries%20-%20Problems%20-%20SOLUTIONS/03_Trie_List_Sort.ipynb):
  - Problem: Given a list of strings as input, implement the `sort_list()` function, which sorts the elements of the list in lexicographical order
  - Solution: We construct a Trie with the words in the list and then we extract the words from it using a depth-first search, implemented recursive calls with a `get_words()` function. The complexity is `O(n)`.
- [Trees/Tries/Tries - Problems - SOLUTIONS/04_Trie_Word_Formation.ipynb](./Trees/Tries/Tries%20-%20Problems%20-%20SOLUTIONS/04_Trie_Word_Formation.ipynb):
  - Problem: Given a dictionary, find whether a given word can be formed by combining two words from the dictionary.
  - Solution: A trie is formed with all the words in the dictionary. Then, given a query word, we check its characters one by one to see if there exists a valid path in the trie, even though the word is not inserted (i.e., the flag `end_of_word` is not set).

## 7. Searching and Sorting

:construction:

TBD.

## 8. Graph Algorithms

:construction:

TBD.

## 9. Riddles and Brain Teasers

Types of riddles:

- Trick questions
- Estimation problems
- Math puzzles

Most of the companies have banned them.

Tips:

- Try to map the problem to a fundamental data structure.
- If we get stuck, try to solve it for a small number of items first, then generalize.

### Examples, Exercises

- [`Bridge Crossing - SOLUTION.ipynb`](./Riddles/Riddle%20Interview%20Problems/Riddle%20Interview%20Problems%20-%20SOLUTIONS/Bridge%20Crossing%20-%20SOLUTION.ipynb):
  - Problem: a group of 4 people with different walking speeds need to cross a bridge with a torch that only can hold the weight of two people; which is the fastest time they can accomplish?
  - Solution: a careful plan is drafted; maybe we could generate all combinations and pick the optimum?
- [`Coins and a Scale - SOLUTION.ipynb`](./Riddles/Riddle%20Interview%20Problems/Riddle%20Interview%20Problems%20-%20SOLUTIONS/Coins%20and%20a%20Scale%20-%20SOLUTION.ipynb):
  - Problem: find the heaviest coin in a group of 8 coins using a 2-pan scale.
  - Solution: create 2 groups, i.e., 2 groups of 3 and one of 2, then start using the scale. The key is creating 3 groups, not 2!
- [`Egg Drop - SOLUTION.ipynb`](./Riddles/Riddle%20Interview%20Problems/Riddle%20Interview%20Problems%20-%20SOLUTIONS/Egg%20Drop%20-%20SOLUTION.ipynb)
  - Problem: Given 2 eggs, discover the highest floor possible they can be thrown from without breaking. The highest floor is 100.
  - Solution: Start dropping the egg every 10th floor, when it breaks, use second to determine the unit; worst-case: 19 drops. Alternative: use binary search.
- [`Hallway Lockers - SOLUTION.ipynb`](./Riddles/Riddle%20Interview%20Problems/Riddle%20Interview%20Problems%20-%20SOLUTIONS/Hallway%20Lockers%20-SOLUTION.ipynb)
  - Problem: We go through a hall way with 100 lockers and toggle (open/close) the (n+1)th lockers in each nth pass. How many lockers remain open after 100 passes.
  - Solution: Select a small number of lockers (e.g., 12), perform n passes and see which patterns emerge. Then generalize. It turns out only perfect square numbers remain open.
- [`Jugs of Water - SOLUTION.ipynb`](./Riddles/Riddle%20Interview%20Problems/Riddle%20Interview%20Problems%20-%20SOLUTIONS/Jugs%20of%20Water%20-%20SOLUTION.ipynb)
  - Problem:
    > You have a five gallons jug and a three gallons jug, and an unlimited supply of water (but no measuring cups) How would you come up with exactly four gallons of water?
  - Solution: We combine both jugs to find the strategy; key idea: when one is partially filled, we can fill it with the other, simulating a subtraction operation. Since we are asked for 4 gallons, the jug with the 5 gallons should be part of the solution.
- [`Light Switches - SOLUTION.ipynb`](./Riddles/Riddle%20Interview%20Problems/Riddle%20Interview%20Problems%20-%20SOLUTIONS/Light%20Switches%20-%20SOLUTION.ipynb)
  - Problem: Three incandescent lights inside a room can be switched on with three switches outside of the room. Guess which switch belongs to each bulb.
  - Solution: Use the fact that incandescent bulbs get hot.
- [`Ropes Burning - SOLUTION.ipynb`](./Riddles/Riddle%20Interview%20Problems/Riddle%20Interview%20Problems%20-%20SOLUTIONS/Ropes%20Burning%20-%20SOLUTION.ipynb)
  - Problem: Three ropes of different material and burning rate take exactly 60 minutes to burn, but each burns inconsistently. Measure 45 minutes.
  - Solution: We can light the two ends of a rope, and one of another. When the first finishes, we light the second end of the second rope which is burning.

## 10. Extra: Subsets - Combinations, Permutations and Co.

Sources:

- [Easy Permutations and Combinations](https://betterexplained.com/articles/easy-permutations-and-combinations/)
- [Permutation and Combination in Python](https://www.geeksforgeeks.org/permutation-and-combination-in-python/)

Permutations and combinations create subsets from a larger set of objects; their difference, in short:

- Permutations are for lists: order matters.
- Combinations are for groups: order doesn't matter.

**A common strategy is to generate all possible subsets from a larger set and then filter the cases according to some rules.**

### Permutations

Permutations count **all possible ways** of doing something; order matters.

Example:

> We have 8 people. How many ways can we award a 1st, 2nd and 3rd place prize among eight contestants? (Gold / Silver / Bronze)

```
1: [A]lice
2: [B]ob
3: [C]harlie
4: [D]avid
5: [E]ve
6: [F]rank
7: [G]eorge
8: [H]oratio
```

Answer:

```
P(n, k) = n! / (n - k)!
P(n=8, k=3) = 8!/5! = 8 * 7 * 6 = 336
```

Where:

- `n`: total number in large set
- `k`: size of subsets

![Permutation](./assets/permutation.png)

Further examples:

- Picking a President, VP and Waterboy from a group of 10.

### Combinations (without Replacement)

Combinations count **all possible unordered subgroups**; order *does not* matter. **Important: this section is about combinations _without_ replacement**

Example:

> We have 8 people. The top 3 are selected independently of score and each one receives the same T-Shirt as present. How many ways can I give 3 T-Shirts to 8 people?

```
1: [A]lice
2: [B]ob
3: [C]harlie
4: [D]avid
5: [E]ve
6: [F]rank
7: [G]eorge
8: [H]oratio
```

Answer:

```
C(n, k) = P(n, k) / k! = n! / (k!(n - k)!)
C(n=8, k=3) = 8!/(3!5!) = 8 * 7 * 6 / (3 * 2 * 1) = 336 / 6 = 56
```

Where:

- `n`: total number in large set
- `k`: size of subsets

![Combination](./assets/combination.png)

**Important: C(n,k) is the [binomial coefficient](https://en.wikipedia.org/wiki/Binomial_coefficient)**

Further examples:

- Picking a team of 3 people from a group of 10.
- Choosing 3 desserts from a menu of 10.

### Combinations with Replacement

Example:

> There are five kinds of frozen yogurt: banana, chocolate, lemon, strawberry and vanilla. You can have three scoops. What number of varieties will there be?

```
C_R(n, k) = C(n+k-1, k) = (n+k-1)! / (k!(n - 1)!)
C_R(n=5, k=3) = C(n+k-1=5+3-1, k=3) = 7! / (3!*4!) = 7 * 6 * 5 / (3 * 2 * 1) = 35
```


### Python Implementations

The `itertools` module has these functions which not only count but generate the subgroups:

- `permutations`: `P(n, k) = n! / (n - k)!`
- `combinations`: `C(n, k) = P(n, k) / k! = n! / (k!(n - k)!)`
- `combinations_with_replacement`: `C(n+k-1, k) = (n+k-1)! / (k!(n - 1)!)`

```python
# A Python program to print all 
# permutations using library function 
from itertools import (
    permutations,
    combinations,
    combinations_with_replacement
)

 
# Get all permutations of [1, 2, 3]
# n = 3, k = 0
perm = permutations([1, 2, 3]) 
 
# Print the obtained permutations
# Complexity: O(n!), because there are n! 
for i in list(perm): 
    print(i)
    # (1, 2, 3)
    # (1, 3, 2)
    # (2, 1, 3)
    # (2, 3, 1)
    # (3, 1, 2)
    # (3, 2, 1)

# Get all permutations of length 2
# n = 3, k = 2
# Complexity: O(n^k)
perm = permutations([1, 2, 3], 2) 
 
# Print the obtained permutations 
for i in list(perm): 
    print(i)
    # (1, 2)
    # (1, 3)
    # (2, 1)
    # (2, 3)
    # (3, 1)
    # (3, 2)

# Get all combinations of [1, 2, 3]
# and length 2
# n = 3, k = 2
# Elements are treated as unique based on their position, 
# not on their value
comb = combinations([1, 2, 3], 2)
 
# Print the obtained combinations
for i in list(comb):
    print(i)
    # (1, 2)
    # (1, 3)
    # (2, 3)

# Get all combinations of [1, 2, 3]
# and length 2, but with REPLACEMENT
comb = combinations_with_replacement([1, 2, 3], 2) 
 
# Print the obtained combinations 
for i in list(comb): 
    print(i)
    # (1, 1)
    # (1, 2)
    # (1, 3)
    # (2, 2)
    # (2, 3)
    # (3, 3) 
```

### Example: Largest Palindromic Number

You are given a string `S` consisting entirely of decimal digits (0–9). Your task is to form the largest possible palindromic number using the digits from `S`. You must use at least one digit, and you can rearrange the digits in any order.

**Definition:**

A palindromic number is a number that reads the same forwards and backwards. For example, "7", "44", and "83238" are palindromic numbers.

**Constraints:**

- The palindromic number should not have any leading zeros (e.g., "0990" or "010").
- The length of `S` (denoted as `N`) is between 1 and 100,000.
- The string `S` contains only digits from 0 to 9.

**Examples:**

1. Given `S = "39878"`, the function should return `"898"`.
2. Given `S = "00900"`, the function should return `"9"`.
3. Given `S = "0000"`, the function should return `"0"`.
4. Given `S = "54321"`, the function should return `"5"`.

**Instructions:**

Write a function:

```python
def solution(S):
```

This function should take a string `S` and return a string representing the largest possible palindromic number that can be created from the digits in `S`.

**Edge Cases:**

- If all characters are zeros, the result should be `"0"`.
- Single digit strings should return the digit itself.

**Example Walkthrough:**

For `S = "8199"`, the possible palindromic numbers are "1", "8", "9", "99", "919", and "989". Among these, "989" is the largest.

**Solution:**

The following solution  generates all possible combinations and permutations of the digits, then checks each one to see if it is a valid palindrome without leading zeros. While this method is correct in theory, it is highly inefficient, especially given the constraints (up to 100,000 digits). Generating all permutations and combinations results in factorial time complexity, which is impractical for large inputs.

```python
from itertools import combinations, permutations

def is_palindrome(s):
    return s == s[::-1]

def solution(S):
    valid_palindromes = []

    # Generate all possible combinations of all lengths
    for r in range(1, len(S) + 1):
        for comb in combinations(S, r):
            # For each combination, generate all possible permutations
            for perm in permutations(comb):
                perm_str = "".join(perm)
                
                # Check if it's a palindrome and doesn't have leading zeros (except "0")
                if (perm_str[0] != '0' or perm_str == '0') and is_palindrome(perm_str):
                    valid_palindromes.append(perm_str)

    # Return the palindrome with the largest decimal value
    return max(valid_palindromes, key=int, default='0')

print(solution("39878")) # 898
print(solution("00900")) # 9
print(solution("0000")) # 0
print(solution("54321")) # 5

# Test functions
def test_solution():
    assert solution("39878") == "898"
    assert solution("00900") == "9"
    assert solution("0000") == "0"
    assert solution("54321") == "5"
    print("All tests passed!")

test_solution()

```

**Steps for a more efficient solution:**

1. Count the Frequency of Each Digit: Use a frequency counter to count how many times each digit appears in the string.
2. Form Half of the Palindrome: Collect the digits in descending order to form the first half of the palindrome.
3. Handle the Middle Digit: If any digit has an odd frequency, select the largest one as the middle digit.
4. Create the Full Palindrome: Mirror the first half to create the second half of the palindrome, inserting the middle digit if necessary.


## 11. Extra: Python Tips & Tricks

### Interesting Articles, Links

- [12 Python Features Every Data Scientist Should Know](https://medium.com/bitgrit-data-science-publication/12-python-features-every-data-scientist-should-know-1d233dbaab0c)
- [10 Python Anti-Patterns You Must Avoid When Writing Clean Code](https://medium.com/python-in-plain-english/10-python-anti-patterns-you-must-avoid-when-writing-clean-code-ff3635ca1510)

### Python Tools

```python
###
# General
###

# Time execution time with several loops
%%timeit
foo()

# Maximum possible value
float("inf")

# is and is not check whether two variables refer to the same object in memory
a = [1, 2, 3]
b = a.copy()
b != a # False: values compared
b is not a # True: memory address compared

# Divisions and modulo
5//2 # 2
5%2 # 1

# Lambda functions
def square(x):
    return x**2
# Lambda equivalent; use-once functions
s = lambda x: x**2
# See also map() and filter()

# Get a variable name as a string
def get_variable_name(variable):
    globals_dict = globals()
    if variable:
        return [var_name for var_name in globals_dict 
                    if globals_dict[var_name] is variable][0]
    else:
        return None

# Get a variable memory address
a = [1, 2, 3, 4, 5]
print(id(a)) # 140234866534752
a = 12
print(id(a)) # 94264748411744

# Check type: isinstance()
a = "hello"
if isinstance(a, int):
    print(1+a)
else:
    print(s)

# Casting
str(1) # "1"
int(1.01) # 1
float(1) # 1.0

# Non-booleans evaluate as True
# if they're not None or 0
# This is relevant for if/while/assert
a = -1
b = 0.0
c = None
d = [1, 2]
e = [0, 0]
if a:
  return True # True
assert b # False, Error
assert c # False, Error
assert d # True
assert e # True

# Unpacking iterables as arguments
# *args means "treat the elements of this iterable as positional arguments to this function call."
# **kwargs means "treat the key-value pairs in the dictionary as additional named arguments to this function call."

def foo(x, y):
    print(x, y)

t = (1, 2)
foo(*t) # 1 2

[1, *(2, 3), 4] # [1, 2, 3, 4]

d = {'x':1, 'y':2}
foo(**d) # 1 2

###
# Arrays / Lists, Strings, Dictionaries, Sets & Co.
###

# Last element
a[-1]

# Reverse
a[::-1]
# Equivalent
reversed(a)

# Slicing lets out of range indices!
a = [1,2,3]
a[3] # Out of index ERROR
a[5:] # [], NO ERROR!
text = 'abc'
text[5:] # '', NO ERROR!

# Check if element in list:
# -> first transform into set, because it's a hash table => O(1) serach!
L = ["San Sebastian", "Bilbao", "Gasteiz", "Eibar", "Irun"]
S = set(l)
K = "Madrid"
if K in S:
    print(f"{K} is in L")

# Sort
sorted(a)
a.sort() # in place

# More on Slicing
l = [1, 2, 3, 4, 5]
l1 = l[0:2] # [1, 2, 3]
l2 = l[2:4] # [4, 5]
l3 = l1 + l2 # [1, 2, 3, 4, 5]

# Dictionaries
d = {}
d['key'] = 'value'
for k in d.keys():
    pass
# To .extend() a dictionary
a.update(b) # dictionary a gets k:v from b and we get None in return
# Also with dictionaries
for k, v in d.items():
    pass

# List/Dictionary comprehensions & enumerate
[v for v in range(10) if v%2 == 0] # [0, 2, 4, 6, 8]
{k:v for k,v in enumerate(range(0,10,2))} # {0: 0, 1: 2, 2: 4, 3: 6, 4: 8}

# Conditional loops
for i in [n for n in numbers if n%2 ==0]:
    pass
# ... prefer them to for+if 
for i in numbers:
    if i%2 == 0:
        pass

# Initialize, append, pop
a = []
a.append(1) # [1]
a.extend([2, 3]) # [1, 2, 3]
a.append([4, 5]) # [1, 2, 3, [4, 5]]
b = a.pop() # a = [1, 2, 3], b = [4, 5]
c = a.pop(0) # a = [2, 3], c = 1

# Sets: nice way of reducing time complexity!
s = set()
s.add(obj) # can be an int, tuple, etc.
if e in s:
    print(f"{e} is in set s")

# sum(), max(), min()
a = [1,2,3]
s = sum(a) # 6
max_ = max(a) # 3
min_ = max(a) # 1

# zip()
arr1 = [1, 2, 3]
arr1 = [4, 5, 6]
for p in zip(arr1,arr2):
    print(p) # (1, 4), (2, 5), (3, 6)
    # unpacking
    a, b = p

# map(), filter(), all()
# map(function, iterable): apply function() all items from iterable and return new iterable
# filter(function->Bool, iterable)
# all(iterable)
list(map(lambda x: x**2, [1, 2, 3])) # [1, 4, 9]
list(filter(lambda x: x%2 == 0, [1, 2, 3])) # [2]
all(map(lambda x: x%2 == 0, [1, 2, 3])) # False

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
import collections
d = collections.defaultdict(int)
d[1] += 1 # even though d[1] was not created explicitly, it's initialized
# Deque: double ended queue, can be used as stack/queue
# pop & append work on the right; for the left, we have:
from collections import deque
numbers = deque([1, 2, 3, 4])
numbers.popleft() # 1
numbers.appendleft(10) # [10, 2, 3, 4]

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

### Testing

```python

# Function to be tested
def square(n):
    return n*n

# Unit test class
class UnitTest:
    
    def test(self, foo):
        assert (foo(2) == 4)
        assert (foo(-2) == 4)
        assert (foo(0) == 0)
        assert not (foo(3) == 10)
        print('All test cases passed')
        
# Run Tests
t = UnitTest()
t.test(square)

```

### Tricks

```python
## Get code of a function/class
import inspect

# Previously defined, somewhere...
class MyClass:
    def my_method(self):
        print("Hello, world!")

# In some other part of the code:
source_code = inspect.getsource(MyClass)
print(source_code)
```

## 12. Extra: Writing Efficient Python Code

DataCamp course [Writing Efficient Python Code](https://app.datacamp.com/learn/courses/writing-efficient-python-code):

- Foundations for efficiencies
  - `range()`, `enumerate()`, `map()`
  - Numpy arrays
- Timing and profiling code
  - `%timeit`
  - `%lprun`
  - `%mprun`
- Gaining efficiencies
  - Permutations, combinations
  - Optimizing and or eliminating loops
- Basic pandas optimizations
  - `.iterrows()`
  - `.itertuples()`
  - `.apply()`
  - `.iloc`

See [`Efficient_Python/`](./Efficient_Python/).

## 13. Design Patterns

See [mxagar/design_patterns_notes](https://github.com/mxagar/design_patterns_notes).
