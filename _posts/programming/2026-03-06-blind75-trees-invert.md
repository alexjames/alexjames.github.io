---
title:  "Blind 75: Trees: Invert Binary Tree"
mathjax: true
layout: post
categories: programming
---

## Question
``Given the root of a binary tree, invert the tree, and return its root.``

## Solutions
Mirroring involves swapping the left subtree with the right subtree. We do this recursively.

- Space complexity: <span style='font-size:16px'>$$O(log n)$$</span> (for the call stack)
- Time complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
    if root == None:
        return
    self.invertTree(root.left)
    self.invertTree(root.right)
    root.left, root.right = root.right, root.left
    return root
```
