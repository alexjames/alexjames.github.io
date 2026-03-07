---
title:  "Blind 75: Trees: Maximum Depth of Binary Tree"
mathjax: true
layout: post
categories: programming
---

## Question
``Given the root of a binary tree, return its maximum depth.

A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.``

## Solutions
- Time complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
def maxDepth(self, root: Optional[TreeNode]) -> int:
    if root == None:
        return 0
    else:
        return 1 + max(self.maxDepth(root.left), self.maxDepth(root.right))
```
