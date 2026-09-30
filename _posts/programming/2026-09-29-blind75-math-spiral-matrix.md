---
title:  "Blind 75: Math: Spiral Matrix"
mathjax: true
layout: post
categories: programming
---

## Question
```
Given an m x n matrix, return all elements of the matrix in spiral order.
```

## Solution
This gets tricky because my first instinct is to reduce this problem to traversing the edges of a rectangle of size m x n. I could possibly
get this to work, but the code is extremely tricky, because i'm dealing with indices like (x + m - 2), etc that get confusing.

A better visualization is to think of the boundary and imagine an entire side disappearing with every iteration through the matrix.

- Time complexity: <span style='font-size:16px'>$$O(m * n)$$</span>
- Space complexity: <span style='font-size:16px'>$$O(1)$$</span>

### Sorting by start time 
```python
class Solution:

```
