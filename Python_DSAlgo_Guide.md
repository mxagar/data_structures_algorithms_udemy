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
  - [3. Stacks, Queues and Deques](#3-stacks-queues-and-deques)
  - [4. Linked Lists](#4-linked-lists)
  - [5. Recursion](#5-recursion)
  - [6. Trees](#6-trees)
  - [7. Searching and Sorting](#7-searching-and-sorting)
  - [8. Graph Algorithms](#8-graph-algorithms)
  - [9. Riddles](#9-riddles)
  - [10. Other Topics](#10-other-topics)
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
- Memory is allocated first and if we append new immutables, %50 of current allocation is added every n additions.

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


## 3. Stacks, Queues and Deques

## 4. Linked Lists

## 5. Recursion

## 6. Trees

## 7. Searching and Sorting

## 8. Graph Algorithms

## 9. Riddles

## 10. Other Topics

### Salary Negotiation

- [How to Negotiate Your Job Offer - Prof. Deepak Malhotra (Harvard Business School)](https://www.youtube.com/watch?v=km2Hd_xgo9Q)

