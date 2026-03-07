---
title:  "Blind 75: Stacks: Find Minimum in Rotated Sorted Array"
mathjax: true
layout: post
categories: programming
---

## Question
``Suppose an array of length n sorted in ascending order is rotated between 1 and n times. For example, the array nums = [0,1,2,4,5,6,7] might become:

[4,5,6,7,0,1,2] if it was rotated 4 times.
[0,1,2,4,5,6,7] if it was rotated 7 times.
Notice that rotating an array [a[0], a[1], a[2], ..., a[n-1]] 1 time results in the array [a[n-1], a[0], a[1], a[2], ..., a[n-2]].

Given the sorted rotated array nums of unique elements, return the minimum element of this array.

You must write an algorithm that runs in O(log n) time.``

## Solutions
# Using Modified Binary Search
This problem can seem hard to reason about if you try evaluating all the cases of the mid-point and all possiblities of the surrounding edge values. It's easier to think about this in terms of the "pivot" point.
The minimum if the pivot point. So we need to figur out what side of the list the pivot point would be at.

This ends up being simpler as we see that if nums[mid] < nums[right] i.e. strictly increasing, the pivot point is guaranteed to be at the mid point or to the left.

- Space complexity: <span style='font-size:16px'>$$O(1)$$</span>
- Time complexity: <span style='font-size:16px'>$$O(log n)$$</span>

```python
    def findMin(self, nums: List[int]) -> int:
        i = 0
        j = len(nums) - 1
        while i < j:
            if j - i <= 1:
                return min(nums[i], nums[j])
            mid = int((i + j) / 2)
            left = nums[i]
            right = nums[j]
            if left > nums[mid] or right > nums[mid]:
                j = mid
            else:
                i = mid
        return nums[i]
```
