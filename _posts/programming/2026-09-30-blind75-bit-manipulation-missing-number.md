---
title:  "Blind 75: Bit Manipulation: Missing Number"
mathjax: true
layout: post
categories: programming
---

## Question
```
Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.
```

## Solution
This is another standard problem where the summation series can be used to find the missing number.

```python
class Solution:
    def missingNumber(self, nums: list[int]) -> int:
        s = sum(nums)
        n = len(nums)
        expected = int((n * (n + 1)) / 2)
        return expected - s
```



