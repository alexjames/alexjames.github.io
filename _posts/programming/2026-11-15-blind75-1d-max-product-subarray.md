---
title:  "Blind 75: 1D DP: Maximum Product Subarray"
mathjax: true
layout: post
categories: programming
---

## Question
```
Given an integer array nums, find a subarray that has the largest product, and return the product.

A subarray is a contiguous non-empty sequence of elements within an array.

You can assume the output will fit into a 32-bit integer.

Note that the product of an array with a single element is the value of that element.

```

### Solutions
The optimum solution is going to be a modification of Kadane's algorithm. On every iteration through the array we will look at three values:

`nums[i]`

`max_val * nums[i]`

`min_val * nums[i]`

```python
class Solution:
    def maxProduct(self, nums: list[int]) -> int:
        result = max_val = min_val = nums[0]
        for i in range(1, len(nums)):
            tmp = max(max_val * nums[i], min_val * nums[i], nums[i])
            min_val = min(max_val * nums[i], min_val * nums[i], nums[i])
            max_val = tmp
            result = max(result, max_val)
        return result
```
