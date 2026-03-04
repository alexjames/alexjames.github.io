---
title:  "Blind 75: Linked List: Reverse Linked List"
mathjax: true
layout: post
categories: programming
---

## Question
``Given the head of a singly linked list, reverse the list, and return the reversed list.``

## Solutions
# Two pointers
- Time complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
    if head == None:
        return

    prev = None
    curr = head
    while curr != None:
        tmp = curr.next
        curr.next = prev
        prev = curr
        curr = tmp
    return prev
```
