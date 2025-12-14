---
title:  "Blind 75: Arrays and Hashes: Products of Array Except Self"
mathjax: true
layout: post
categories: programming
---

## Question
``Given an integer array nums, return an array output where output[i] is the product of all the elements of nums except nums[i].``

## Solution
A solution we might pursue here might be to take product of all elements in the array and then divide by nums[i]. This creates problems in a few cases:
1. 0 or divide by 0
2. negative integers


###
- Time Complexity: <span style='font-size:16px'>$$O(n)$$</span>
- Space Complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        leftproducts = [1] * len(nums)
        for i in range(1, len(nums)):
            leftproducts[i] = nums[i-1] * leftproducts[i-1]
        rightproducts = [1] * len(nums)
        for i in range(len(nums) - 2, -1, -1):
            rightproducts[i] = nums[i+1] * rightproducts[i+1]
        result = []
        for i in range(len(nums)):
            result.append(rightproducts[i] * leftproducts[i])
        return result
```
