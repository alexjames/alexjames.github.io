---
title:  "Blind 75: 1D DP: House Robber 1"
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
It's tempting here to think that similar to the climbing problem, you always pick the `n`th house and the max dp value from `n - 2`. However, this results in incorrect results because the maximum value solution at point `n` house.

Thus, `dp[i] = max(dp[i] + dp[i - 2], dp[i - 1])`.


```python
class Solution:
    def climbStairs(self, n: int) -> int:
        if n == 1:
            return 1
        if n == 2:
            return 2
        a = 1
        b = 2
        for i in range(3, n + 1):
            a, b = b, a + b
        return b
```
