---
title:  "Blind 75: Graphs: Course Schedule"
mathjax: true
layout: post
categories: programming
---

## Question
```
There are a total of numCourses courses you have to take, labeled from 0 to numCourses - 1. You are given an array prerequisites where prerequisites[i] = [ai, bi] indicates that you must take course bi first if you want to take course ai.

For example, the pair [0, 1], indicates that to take course 0 you have to first take course 1.
Return true if you can finish all courses. Otherwise, return false.
```

## Solutions
Things to watch out for:
(1) Since this is an undirected graph, the same edge appears on both nodes. From the directed edge perspective, this appears as cyclical. The way to work around this is to keep track of the parent node you traversed down.
(2) Watch out for cycles on the same node.

- Time complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
class Solution:
    def __init__(self):
        self.visited = set()
        self.graph = {}
        self.current_path = set()

    def dfs(self, n: int) -> bool:
        self.current_path.add(n)
        for k in self.graph.get(n, []):
            if k in self.current_path:
                return True
            if not k in self.visited and self.dfs(k):
                return True
        self.current_path.remove(n)
        self.visited.add(n)
        return False

    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        for prereq in prerequisites:
            if prereq[1] in self.graph:
                self.graph[prereq[1]].append(prereq[0])
            else:
                self.graph[prereq[1]] = [prereq[0]]
        for c in self.graph.keys():
            if c in self.visited:
                continue
            if self.dfs(c):
                return False
        return True
```
