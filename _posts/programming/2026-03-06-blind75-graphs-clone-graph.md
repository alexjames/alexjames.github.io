---
title:  "Blind 75: Graphs: Clone Graph"
mathjax: true
layout: post
categories: programming
---

## Question
``Given a reference of a node in a connected undirected graph.

Return a deep copy (clone) of the graph.``

## Solutions
- Time complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
from collections import deque

from typing import Optional
class Solution:
    def cloneGraph(self, node: Optional['Node']) -> Optional['Node']:
        if node == None:
            return None

        starting_node = Node(node.val)
        node_map = {node: starting_node}
        
        q = deque()    
        q.append(node)
        while len(q) > 0:
            n = q.popleft()
            cloned_node = node_map[n]
            for neighbor in n.neighbors:
                if neighbor in node_map:
                    cloned_node.neighbors.append(node_map[neighbor])
                else:
                    m = Node(neighbor.val)
                    node_map[neighbor] = m
                    cloned_node.neighbors.append(m)
                    q.append(neighbor)
        return starting_node
```
