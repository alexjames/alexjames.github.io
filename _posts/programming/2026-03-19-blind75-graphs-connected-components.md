---
title:  "Blind 75: Graphs: Number of Connected Components in an Undirected Graph"
mathjax: true
layout: post
categories: programming
---

## Question
```
You have a graph of n nodes. You are given an integer n and an array edges where edges[i] = [aᵢ, bᵢ] indicates that there is an edge between aᵢ and bᵢ in the graph.

Return the number of connected components in the graph.
```

## Solutions
Standard DFS works here.

Things to watch out for:
(1) Cycles in the undirected graph
(2) Singular nodes with no edges also count as a component

- Time complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
class Solution:
    def __init__(self):
        self.graph = {}
        self.visited = set()
        self.current_path = []

    def dfs(self, n: int, parent: int):
        self.visited.add(n)
        for x in self.graph.get(n, []):
            if x == parent:
                continue
            if not x in self.visited:
                self.dfs(x, n)

    def countComponents(self, n: int, edges: List[List[int]]) -> int:
        for edge in edges:
            if edge[1] in self.graph:
                self.graph[edge[1]].append(edge[0])
            else:
                self.graph[edge[1]] = [edge[0]]
        for edge in edges:
            if edge[0] in self.graph:
                self.graph[edge[0]].append(edge[1])
            else:
                self.graph[edge[0]] = [edge[1]]
        num_components = 0
        for k in range(0, n):
            if not k in self.visited:
                num_components += 1
                self.dfs(k, -1)
        return num_components
```
