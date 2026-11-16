---
title:  "Blind 75: 1D DP: Coin Change"
mathjax: true
layout: post
categories: programming
---

## Question
```
You are given an integer array coins representing coins of different denominations (e.g. 1 dollar, 5 dollars, etc) and an integer amount representing a target amount of money.

Return the fewest number of coins that you need to make up the exact target amount. If it is impossible to make up the amount, return -1.

You may assume that you have an unlimited number of each coin.
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
