---
title:  "Blind 75: 1D DP: House Robber 2"
mathjax: true
layout: post
categories: programming
---

## Question
```
You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?
```

## Solution
This seems tricky because if we pick the first house, we can't pick the last. And vice-versa.

Imagine you could break the chain and lay the houses out. We can then simulate house robber 1 twice for all but the first and all but the last.
The answers should be the max of these two.

```python
class Solution:
    def rob_houses(self, nums: list[int]) -> int:
        dp = [0] * len(nums)
        dp[0] = nums[0]
        dp[1] = max(nums[0], nums[1])
        for i in range(2, len(nums)):
            dp[i] = max(nums[i] + dp[i-2], dp[i-1])
        return dp[-1]

    def rob(self, nums: list[int]) -> int:
        if len(nums) <= 2:
            return max(nums)
        return max(self.rob_houses(nums[1:]), self.rob_houses(nums[:-1]))
```
