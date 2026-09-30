---
title:  "Blind 75: Math: Rotate Image"
mathjax: true
layout: post
categories: programming
---

## Question
```
You are given an n x n 2D matrix representing an image, rotate the image by 90 degrees (clockwise).

You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.
```

## Solution
This one seems daunting at first. To solve this, you have to observe how elements go around in a circle in a fixed pattern. This pattern is
can be described as a function where `(x, y) --> (y, n - x)`. We apply this function to all elements except the one at the center. 

The other tricky part is the loop for calling the four-way swap function. You have to handle the odd/even case correctly and ensure the
center element stays untouched in case of an n is odd.

- Time complexity: <span style='font-size:16px'>$$O(n)$$</span>
- Space complexity: <span style='font-size:16px'>$$O(1)$$</span>

### Sorting by start time 
```python
class Solution:
    def _fourway_swap(self, i: int, j: int, matrix: list[list[int]]) -> None:
        n = len(matrix[0]) - 1
        x, y = i, j

        t = matrix[x][y]
        ### TODO(ajames): Put in a loop, unrolled for clarity
        # rot 1:
        t, matrix[y][n - x] = matrix[y][n - x], t
        x , y = y, n - x

        # rot 2:
        t, matrix[y][n - x] = matrix[y][n - x], t
        x , y = y, n - x

        # rot 3:
        t, matrix[y][n - x] = matrix[y][n - x], t
        x , y = y, n - x

        # rot 4:
        t, matrix[y][n - x] = matrix[y][n - x], t
        x , y = y, n - x


    def rotate(self, matrix: list[list[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        n = len(matrix[0])
        for i in range(0, int(n/2)):
            for j in range(i, n - 1 - i):
                self._fourway_swap(i, j, matrix)
```
