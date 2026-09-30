---
title:  "Blind 75: Bit Manipulation: Number of 1 Bits"
mathjax: true
layout: post
categories: programming
---

## Question
```
Given a positive integer n, write a function that returns the number of set bits in its binary representation (also known as the Hamming weight).
```

## Solution
Standard solution. Right shift and test right-most bit. Only thing to remember are the Python bit-wise operators - `>>` and `&`.

- Time complexity: <span style='font-size:16px'>$$O(n)$$</span> (`n` is number of bits)
- Space complexity: <span style='font-size:16px'>$$O(1)$$</span>

### Sorting by start time 
```python
class Solution:
    def hammingWeight(self, n: int) -> int:
        count = 0
        while n > 0:
            if n & 1 == 1:
                count += 1
            n >>= 1
        return count

```
