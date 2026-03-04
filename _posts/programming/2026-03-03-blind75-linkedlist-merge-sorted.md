---
title:  "Blind 75: Linked List: Merge Two Sorted Lists"
mathjax: true
layout: post
categories: programming
---

## Question
``You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.``

## Solutions
# Create a new list
This works exactly the same as merging two sorted arrays, except you add nodes to the end of a new linked list.

# In-place Merge
Merging in-place seems tricky if you try visualizing it in terms of `p` and `q` pointers that need to weave together. It's far easier to 
think of it as generating a new list `f` that picks its next node as the smaller of `p` and `q`.

```python
def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
    if list1 == None:
        return list2
    if list2 == None:
        return list1
    
    p = list1
    q = list2
    f = None
    new_head = None
    if p.val <= q.val:
        f = p
        new_head = f
        p = p.next
    else:
        f = q
        new_head = f
        q = q.next

    while p != None and q != None:
        if p.val <= q.val:
            f.next = p
            f = p
            p = p.next
        else:
            f.next = q
            f = q
            q = q.next
    
    if q == None:
        f.next = p
    else:
        f.next = q

    return new_head
```
