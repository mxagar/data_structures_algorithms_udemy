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
  - [4. Linked Lists](#4-linked-lists)
  - [5. Recursion](#5-recursion)
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

## 4. Linked Lists

## 5. Recursion

## 6. Trees

## 7. Searching and Sorting

## 8. Graph Algorithms

## 9. Riddles

## 10. Python Tips & Tricks

```python

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
s = "Hello world"
s.split() # ["Hello", "world"]
" ".join(s[::-1]) # "world Hello"
# Remove spaces and lowercase letters
s1 = s1.replace(' ','').lower()
s2 = s2.replace(' ','').lower()

```



## 11. Other Topics

### Salary Negotiation

- [How to Negotiate Your Job Offer - Prof. Deepak Malhotra (Harvard Business School)](https://www.youtube.com/watch?v=km2Hd_xgo9Q)

