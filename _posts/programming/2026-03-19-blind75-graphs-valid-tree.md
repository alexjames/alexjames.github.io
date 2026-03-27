---
title:  "Blind 75: Graphs: Graph Valid Tree"
mathjax: true
layout: post
categories: programming
---

## Question
```
Given n nodes labeled from 0 to n - 1 and a list of undirected edges (each edge is a pair of nodes), write a function to check whether these edges make up a valid tree.
```

## Solutions
A graph is a tree if all its nodes are connected and there is no cycle.

Things to watch out for:
(1) Since this is an undirected graph, the same edge appears on both nodes. From the directed edge perspective, this appears as cyclical. The way to work around this is to keep track of the parent node you traversed down.
(2) Watch out for cycles on the same node.
(3) Disconnected graphs are not a tree.

- Time complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
class Solution:
    def __init__(self):
        self.graph = {}
        self.visited = set()
        self.current_path = []
    
    def dfs(self, n: int) -> bool:
        self.current_path.append(n)
        for x in self.graph.get(n, []):
            if x in self.current_path and len(self.current_path) > 1 and x != self.current_path[-2]:
                return True
            if len(self.current_path) > 1 and x == self.current_path[-2]:
                continue
            if not x in self.visited and self.dfs(x):
                return True
        self.current_path.pop()
        self.visited.add(n)
        return False

    def validTree(self, n: int, edges: List[List[int]]) -> bool:
        if len(edges) == 0:
            return True
        for edge in edges:
            if edge[0] == edge[1]:
                return False
            if edge[1] in self.graph:
                self.graph[edge[1]].append(edge[0])
            else:
                self.graph[edge[1]] = [edge[0]]
        for edge in edges:
            if edge[0] in self.graph:
                self.graph[edge[0]].append(edge[1])
            else:
                self.graph[edge[0]] = [edge[1]]
        if self.dfs(0):
            return False
        if len(self.visited) != len(self.graph.keys()):
            return False
        return True 
```
