---
title:  "Blind 75: Linked List: Reverse Linked List"
mathjax: true
layout: post
categories: programming
---

## Question
``Given the head of a linked list, remove the nth node from the end of the list and return its head.``

## Solutions
# Find the length of the list
We find the length of the list, then position our pointer before the nth node to remove it.

```python
def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
    if head == None:
        return head
    p = head
    len = 0
    while p != None:
        len = len + 1
        p = p.next
    if n == len:
        return head.next
    p = head
    while len - n > 1:
        len = len - 1
        p = p.next
    p.next = p.next.next
    return head
```
