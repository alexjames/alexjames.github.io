---
title:  "Blind 75: Greedy: Maximum Subarray"
mathjax: true
layout: post
categories: programming
---

## Question
``
Given an integer array nums, find the subarray with the largest sum, and return its sum.
``

## Solutions
This is harder to reason about from scratch, especially when thinking about all edge cases with negative numbers.
The simplification of this is - "as long as the current number I'm looking keeps the running total back positive, include it,
otherwise make this number the start of a new window". This is also known as Kadane's algorithm.

Edge cases to consider -
 * [-10, -5, -3]
 * [-10, -5, -3, 7]
 * [7, 4, 0, 0, -2, 3]

- Time complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        running_sum = nums[0]
        largest_sum = running_sum
        for i in range(1, len(nums)):
            if running_sum > 0 and nums[i] + running_sum > 0: // if the running sum is negative, just drop it
                running_sum += nums[i]
            else:
                running_sum = nums[i]
            largest_sum = max(largest_sum, running_sum)
        return largest_sum
```
