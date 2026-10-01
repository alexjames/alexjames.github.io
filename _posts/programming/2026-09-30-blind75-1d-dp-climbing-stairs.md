---
title:  "Blind 75: 1D DP: Climbing Stairs"
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
Applying DP thinking, ways to get to each step build on ways to get to two previous step.

Since we can only climb 1 or 2 steps at a time, the ways to get to step `n` would be taking two steps from `n - 2` or one step from `n - 1`.
The answer would thus be the summation of the two ways.

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

