---
title:  "Blind 75: Trees: Subtree of Another Tree"
mathjax: true
layout: post
categories: programming
---

## Question
``Given the roots of two binary trees root and subRoot, return true if there is a subtree of root with the same structure and node values of subRoot and false otherwise.

A subtree of a binary tree tree is a tree that consists of a node in tree and all of this node's descendants. The tree tree could also be considered as a subtree of itself.``

## Solutions
### Using an equivalence helper

- Time complexity: <span style='font-size:16px'>$$O(n ^ 2)$$</span>

```python
def subtreeMatch(self, root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
    if root == None and subRoot == None:
        return True
    if root == None or subRoot == None:
        return False
    return (root.val == subRoot.val) and self.subtreeMatch(root.left, subRoot.left) and self.subtreeMatch(root.right, subRoot.right)

def isSubtree(self, root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
    if root == None or subRoot == None:
        return False
    if root.val == subRoot.val:
        if self.subtreeMatch(root, subRoot) == True:
            return True
    return self.isSubtree(root.left, subRoot) or self.isSubtree(root.right, subRoot)
```
