---
title:  "Blind 75: Greedy: Jump Game"
mathjax: true
layout: post
categories: programming
---

## Question
``
You are given an integer array nums. You are initially positioned at the array's first index, and each element in the array represents your maximum jump length at that position.

Return true if you can reach the last index, or false otherwise.
``

## Solutions
This is harder to reason about from scratch, especially when thinking about all edge cases with negative numbers.
The simplification of this is - "as long as the current number I'm looking at increases the value of the current window, include it,
otherwise make this number the start of a new window".

- Time complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        running_sum = nums[0]
        largest_sum = running_sum
        for i in range(1, len(nums)):
            if nums[i] + running_sum > nums[i]:
                running_sum += nums[i]
            else:
                running_sum = nums[i]
            largest_sum = max(largest_sum, running_sum)

        return largest_sum
```
