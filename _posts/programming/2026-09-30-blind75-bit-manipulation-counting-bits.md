---
title:  "Blind 75: Bit Manipulation: Counting Bits"
mathjax: true
layout: post
categories: programming
---

## Question
```
Given an integer n, return an array ans of length n + 1 such that for each i (0 <= i <= n), ans[i] is the number of 1's in the binary representation of i.

Do not solve it with built-in functions (i.e., like __builtin_popcount in C++).
```

## Solution
Since they don't want you to use a bit counting function, these kinds of problems usually have some sort of relationship you have to find. It's likely that newer 1 bit values have some relation to previous ones.

In this case, after careful examination, you will realize that every number n is `n >> 1` followed by a 1 bit if its odd or 0 if even. This is to say, 
the number of 1 bits is the number of 1 bits until the rightmost bit. 

### Sorting by start time 
```python
class Solution:
    def countBits(self, n: int) -> list[int]:
        result = [0] * (n + 1)
        if n < 1:
            return result
        result[1] = 1
        for i in range(2, n + 1):
            if i % 2 == 0:
                result[i] = result[i >> 1]
            else:
                result[i] = result[i >> 1] + 1
        return result
```


