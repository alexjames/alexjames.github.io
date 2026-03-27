---
title:  "Blind 75: Graphs: Number of Islands"
mathjax: true
layout: post
categories: programming
---

## Question
``Given an m x n 2D binary grid grid which represents a map of '1's (land) and '0's (water), return the number of islands.

An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.``

## Solutions
- Time complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
class Solution:
    def demarkIsland(self, i: int, j: int, grid: List[List[str]]):
        if i < 0 or i >= len(grid):
            return
        if j < 0 or j >= len(grid[0]):
            return
        if grid[i][j] == "0":
            return
        grid[i][j] = "0"
        for x in range(i - 1, i + 2):
            for y in range(j - 1, j + 2):
                if x != i and y != j:
                    continue
                self.demarkIsland(x, y, grid)

    def numIslands(self, grid: List[List[str]]) -> int:
        num_islands = 0
        for i in range(0, len(grid)):
            for j in range(0, len(grid[0])):
                if grid[i][j] == "1":
                    self.demarkIsland(i, j, grid)
                    num_islands += 1
        return num_islands
```
