---
title:  "Blind 75: Bit Manipulation: Reverse Bits"
mathjax: true
layout: post
categories: programming
---

## Question
```
Reverse bits of a given 32 bits signed integer.
```

## Solution
Standard solution.

### Sorting by start time 
```python
class Solution:
    def reverseBits(self, n: int) -> int:
        result = 0
        for _ in range(32):
            result <<= 1
            if n & 1 == 1:
                result += 1
            n >>= 1
        return result
```

