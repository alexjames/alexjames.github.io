---
title:  "Blind 75: 1D DP: Word Break"
mathjax: true
layout: post
categories: programming
---

## Question
```
You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money.

Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

You may assume that you have an infinite number of each kind of coin.

```

### Solutions

```python
class Solution:
    def coinChange(self, coins: list[int], amount: int) -> int:
        if amount == 0:
            return 0
        dp = [-1] * (amount + 1)
        dp[0] = 0
        for coin in coins:
            for i in range(coin, amount + 1):
                if dp[i - coin] > -1:
                    if dp[i] == -1:
                        dp[i] = 1 + dp[i - coin]
                    else:
                        dp[i] = min(dp[i], 1 + dp[i - coin])
        return dp[amount]
```
