---
layout: post
title:  How to Teach Kids Programming
subtitle: How to Teach Kids Programming
date:   2015-06-01 06:21:11 -0800
categories: [Programming]
tags: [Problem Solving]
---
# How to Teach Kids Programming

Programming is about solving problems effectively and efficiently.

## Basic Programming Constructs

* Variables
  * box with name and value
  * value has a type, box type can be inferred from the value
* Statements (a small block of code)
  * Expression which yields a value, like `[index]`, `object.`
  * Operators
    * unary, `++i`
    * binary, `a + b`,
    * ternary, `a > 0? b : c`
* Control flows
  * if / elseif / else
  * switch
  * do while / while do
  * continue and break in iteration
  * return and void
* Functions
  * named or anonymous (lambda)
  * parameters (definition) and arguments (passed-in)
  * returnable and void
* Events
  * while true
  * keyboard and mouse related

### Primitive types

#### boolean

and operator

or operator

#### number

##### integer

##### float

#### string

##### substring

##### pattern match

##### diff

### Array

A shelf of boxes (variables). The boxes usually hold the same type of value. Array provides great support to other data structures.

* Instantiation
* Index and items
* Add and remove items
  * first and last (Queue and stack)
  * inline at specified index
* Iteration
  * value lookup
    * value exists
    * max or min value
  * Aggregation
    * count, sum, avg, median
  * Inline item exchange
    * Partitioning
  * Basic Sorting
    * [Insertion](https://en.wikipedia.org/wiki/Insertion_sort)
    * [Selection](https://en.wikipedia.org/wiki/Selection_sort)
    * [Bubble](https://en.wikipedia.org/wiki/Bubble_sort)
  * Projection
    * Distinct
    * Grouping
  * Set, usually two arrays, each array holds distinct values
    * Union
    * Except
    * Intersection  

#### Sorted Array

Why do we need sorted items:

* Binary Search
* Priority queue and Heap
* O(n) get distinct values

### List and custom collections

The size of array in some languages like C# is fixed. List is built upon array with auto-adjusted size.

### Symbol table

Symbol table is also known as associative array, map or dictionary, it is an abstract collection type to store items.

The index in a list is automatically incremented. For symbol table, each item is associated with a single key with a value and caller needs to specify the key.

```CSharp
list.Add(value);

dictionary.Add(key, value);
```

Instead of using index, a unique key is used to locate the item in the container. If the caller puts a key-value pair into a table already containing that key (and an associated value), the new value replaces the old one.

Only one value is associated with each key as there is no duplicate keys in the container.

#### Hash function

[Hash function](https://en.wikipedia.org/wiki/Hash_function)

### Linked list

Linked list has no index of the items. Each item is a node in the linked list which has a next property instead of index.

## Beyond the basics

### Bits

### Numbers

## Mastery

### Recursion

## Problem Solving

[Tutorials and Practice Problems](https://www.hackerearth.com/practice/)

### Divide and conquer
