---
title:  "Blind 75: Math: Set Matrix Zeroes"
mathjax: true
layout: post
categories: programming
---

## Question
```
Given an m x n integer matrix matrix, if an element is 0, set its entire row and column to 0's.

You must do it in place.
```

## Solution
You could try brute forcing and set every corresponding column and row every time you see a 0. The insight here is that the time complexity of that approach would be <span style='font-size:16px'>$$O(m * n * (m + n))$$</span>.

To do this more efficiently, we have to recognize that the brute force method results in a lot of duplicate work and we try to figure out a way to avoid it. Some observations here -
1. If (x, y) is a 0, then all (x, [0 - n]) and (y, [0, m]) need to be reset.
2. If we knew all the x and y co-ordinates of 0 elements, we could fully determine what matrix elements to reset.

- Time complexity: <span style='font-size:16px'>$$O(m * n)$$</span>
- Space complexity: <span style='font-size:16px'>$$O(1)$$</span>

### Sorting by start time 
```python
class Solution:
    def setZeroes(self, matrix: list[list[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        i_cords = set()
        j_cords = set()
        for i in range (0, len(matrix)):
            for j in range (0, len(matrix[0])):
                if matrix[i][j] == 0:
                    i_cords.add(i)
                    j_cords.add(j)
        for i in range (0, len(matrix)):
            for j in range (0, len(matrix[0])):
                if i in i_cords or j in j_cords:
                    matrix[i][j] = 0
```
