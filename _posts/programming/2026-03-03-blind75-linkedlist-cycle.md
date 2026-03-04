---
title:  "Blind 75: Linked List: Cycle"
mathjax: true
layout: post
categories: programming
---

## Question
``Given head, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to. Note that pos is not passed as a parameter.

Return true if there is a cycle in the linked list. Otherwise, return false.``

## Solutions
# Fast-Slow Pointer/Hare-Tortoise Algorithm
This is a standard cycle detection algorithm. The main insight of this algorithm is that if you have two pointers, one moving one
step at a time and another moving two steps at a time, they will eventuall converge once they enter a cycle, because the fast
pointer reduces its distance from the slow pointer by 1 node in each turn.

```python
def hasCycle(self, head: Optional[ListNode]) -> bool:
    slow = fast = head
    while slow != None and fast != None:
        slow = slow.next
        if fast.next == None:
            return False
        fast = fast.next.next
        if slow == fast:
            return True
    return False
```
