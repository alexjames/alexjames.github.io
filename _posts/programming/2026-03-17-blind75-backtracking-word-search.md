---
title:  "Blind 75: Backtracking: Word Search"
mathjax: true
layout: post
categories: programming
---

## Question
``Given an m x n grid of characters board and a string word, return true if word exists in the grid.

The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.``

## Solutions
Be careful about the indices (m, n, i ,j) as well as ensuring `visited` is unset if all paths from a node do not lead to a match. 

- Time complexity: <span style='font-size:16px'>$$O(m * n * w)$$</span>

```python
class Solution:
    m = 0
    n = 0
    visited: List[List[bool]]

    def dfs(self, i: int, j: int, board: List[List[str]], word: str):
        if i >= self.n or i < 0:
            return False
        if j >= self.m or j < 0:
            return False
        if self.visited[j][i]:
            return False
        if len(word) < 1:
            return False
        if board[j][i] != word[0]:
            return False
        if len(word) == 1:
            return True

        self.visited[j][i] = True
        retval = False
        for x in range(j-1, j+2):
            for y in range(i-1, i+2):
                if x != j and y != i:
                    continue
                retval = retval or self.dfs(y, x, board, word[1:])
        self.visited[j][i] = False
        return retval

    def exist(self, board: List[List[str]], word: str) -> bool:
        self.m = len(board)
        self.n = len(board[0])

        for j in range(0, self.m):
            for i in range(0, self.n):
                if board[j][i] == word[0]:
                    self.visited = [[False] * self.n for _ in range(self.m)]
                    if self.dfs(i, j, board, word) == True:
                        return True
        return False
```
