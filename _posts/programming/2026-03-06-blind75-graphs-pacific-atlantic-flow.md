---
title:  "Blind 75: Graphs: Pacific Atlantic Water Flow"
mathjax: true
layout: post
categories: programming
---

## Question
```
You are given a rectangular island heights where heights[r][c] represents the height above sea level of the cell at coordinate (r, c).

The islands borders the Pacific Ocean from the top and left sides, and borders the Atlantic Ocean from the bottom and right sides.

Water can flow in four directions (up, down, left, or right) from a cell to a neighboring cell with height equal or lower. Water can also flow into the ocean from cells adjacent to the ocean.

Find all cells where water can flow from that cell to both the Pacific and Atlantic oceans. Return it as a 2D list where each element is a list [r, c] representing the row and column of the cell. You may return the answer in any order.
```

## Solutions
- Time complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
class Solution:
    def __init__(self):
        self.pacific = set()
        self.atlantic = set()

    def visit(self, i: int, j: int, visited: set, heights: List[List[int]]):
        visited.add((i,j))
        for x in range(i - 1, i + 2):
            for y in range(j - 1, j + 2):
                if x < 0 or x >= len(heights):
                    continue
                if y < 0 or y >= len(heights[0]):
                    continue
                if x != i and y != j:
                    continue
                if (x,y) in visited:
                    continue
                if heights[x][y] >= heights[i][j]:
                    self.visit(x, y, visited, heights)

    def pacificAtlantic(self, heights: List[List[int]]) -> List[List[int]]:
        for i in range(0, len(heights)):
            self.visit(i, 0, self.pacific, heights)
        for j in range(0, len(heights[0])):
            self.visit(0, j, self.pacific, heights)

        for i in range(0, len(heights)):
            self.visit(i, len(heights[0]) - 1, self.atlantic, heights)
        for j in range(0, len(heights[0])):
            self.visit(len(heights) - 1, j, self.atlantic, heights)

        return list(self.pacific & self.atlantic)
```
