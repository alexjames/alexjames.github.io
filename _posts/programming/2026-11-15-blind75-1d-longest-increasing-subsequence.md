---
title:  "Blind 75: 1D DP: Longest Increasing Subsequence"
mathjax: true
layout: post
categories: programming
---

## Question
```
Given an integer array nums, return the length of the longest strictly increasing subsequence.
```

### Solutions
```python
class Solution:
    def lengthOfLIS(self, nums: list[int]) -> int:
        dp = [1] * len(nums)
        dp[len(nums) - 1] = 1
        for i in range(len(nums) - 1, -1, -1):
            for j in range(len(nums) - 1, i, -1):
                if nums[i] < nums[j]:
                    dp[i] = max(dp[i], 1 + dp[j])
        return max(dp)
```
