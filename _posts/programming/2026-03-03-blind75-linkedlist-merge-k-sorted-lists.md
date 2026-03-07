---
title:  "Blind 75: Linked List: Merge k Sorted Lists"
mathjax: true
layout: post
categories: programming
---

## Question
``You are given an array of k linked-lists lists, each linked-list is sorted in ascending order.

Merge all the linked-lists into one sorted linked-list and return it.``

## Solutions
# Merge lists one-by-one
We implement a merge function and use that to have the lists merge one by one. We use a dummy node for simplicity.

```python
def mergeLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
    f = ListNode(-1)
    head = f
    p = list1
    q = list2
    while p != None and q != None:
        if p.val < q.val:
            f.next = p
            f = p
            p = p.next
        else:
            f.next = q
            f = q
            q = q.next
    if p != None:
        f.next = p
    if q != None:
        f.next = q
    return head.next
    
def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
    if len(lists) == 0:
        return None
    final_list = lists[0]
    for i in range(1, len(lists)):
        final_list = self.mergeLists(final_list, lists[i])
    return final_list
```
