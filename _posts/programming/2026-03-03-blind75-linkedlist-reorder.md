---
title:  "Blind 75: Linked List: Re-order List"
mathjax: true
layout: post
categories: programming
---

## Question
``You are given the head of a singly linked-list. The list can be represented as:

L0 → L1 → … → Ln - 1 → Ln
Reorder the list to be on the following form:

L0 → Ln → L1 → Ln - 1 → L2 → Ln - 2 → …
You may not modify the values in the list's nodes. Only nodes themselves may be changed.``

## Solution
# Split-Reverse-Merge
Looking at the pattern, we are picking nodes alternating between nodes from the start and the end of the list.
To re-create this pattern, we would need to do the following operations -
(1) Split the list in half
(2) Reverse the second half
(3) Merge the two lists

```python
    def reorderList(self, head: Optional[ListNode]) -> None:
        """
        Do not return anything, modify head in-place instead.
        """
        p = head
        len = 0
        while p != None:
            len = len + 1
            p = p.next
        if len <= 2:
            return
        len = len / 2
        p = head
        while len > 1:
            len = len - 1
            p = p.next

        prev = None
        curr = p.next
        p.next = None
        while curr != None:
            nxt = curr.next
            curr.next = prev
            prev = curr
            curr = nxt
        
        p = head
        q = prev
        while p and q:
            nextp, nextq = p.next, q.next
            p.next = q
            q.next = nextp
            p, q = nextp, nextq
```
