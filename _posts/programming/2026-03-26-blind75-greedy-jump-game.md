---
title:  "Blind 75: Greedy: Jump Game"
mathjax: true
layout: post
categories: programming
---

## Question
``
You are given an integer array nums. You are initially positioned at the array's first index, and each element in the array represents your maximum jump length at that position.
``

``
Return true if you can reach the last index, or false otherwise.
``

## Solutions
Keep track of your maximum reach. Keep going until the maximum reach can touch the end of the array or it no longer increases.

- Time complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        curr_reach = nums[0]
        i = 1
        while i <= curr_reach and curr_reach < len(nums) - 1:
            curr_reach = max(curr_reach, i + nums[i])
            i = i + 1
        return curr_reach >= len(nums) - 1
```
