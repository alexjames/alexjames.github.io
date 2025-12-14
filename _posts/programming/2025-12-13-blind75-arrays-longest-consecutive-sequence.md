---
title:  "Blind 75: Arrays and Hashes: Products of Array Except Self"
mathjax: true
layout: post
categories: programming
---

## Question
``Given an array of integers nums, return the length of the longest consecutive sequence of elements that can be formed.``

``A consecutive sequence is a sequence of elements in which each element is exactly 1 greater than the previous element. The elements do not have to be consecutive in the original array.``

## Solution


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
