---
title:  "Blind 75: 1D DP: House Robber 2"
mathjax: true
layout: post
categories: programming
---

## Question
```
You have intercepted a secret message encoded as a string of numbers. The message is decoded via the following mapping:

"1" -> 'A'

"2" -> 'B'

...

"25" -> 'Y'

"26" -> 'Z'

However, while decoding the message, you realize that there are many different ways you can decode the message because some codes are contained in other codes ("2" and "5" vs "25").

For example, "11106" can be decoded into:

"AAJF" with the grouping (1, 1, 10, 6)
"KJF" with the grouping (11, 10, 6)
The grouping (1, 11, 06) is invalid because "06" is not a valid code (only "6" is valid).
Note: there may be strings that are impossible to decode.

Given a string s containing only digits, return the number of ways to decode it. If the entire string cannot be decoded in any valid way, return 0.

The test cases are generated so that the answer fits in a 32-bit integer.

```

## Solution
I struggled with this because it was confusing how to count the number of ways to decode a string. Here were the main insights that were needed to solve this question -
(1) The option split only comes from 1 or 2. If you only had the other non-zero digits, there would only be one way to decode the string. That's the base case.
(2) If you have a 1, then any digit following it works.
(3) If you have a 2, then only 0 to 6 can follow it. Otherwise, there is only one way to decode the 2.

The key thing here is the question asks ways to decode a string of some length. Whenever you encounter a question such as this, ask if we can figure out number of ways to decode smaller strings and then if there a relationship between those and our string.

Also, in this problem, it's easier to work from the end of the string, building up the number of ways to decode the string from smaller to larger length strings.

### Recursive
```python
class Solution:
    def numDecodings(self, s: str) -> int:
        if len(s) == 0:
            return 1
        if s[0] == '0':
            return 0
        if len(s) > 1 and (s[0] == '1' or s[0] == '2'):
            if s[1] == '0':
                return self.numDecodings(s[2:])
            if s[0] == '2' and int(s[1]) > 6:
                return self.numDecodings(s[1:])
            else:
                return self.numDecodings(s[1:]) + self.numDecodings(s[2:])
        return self.numDecodings(s[1:])
```
### Recursion with memoization
```python
class Solution:
    def numDecodings(self, s: str) -> int:
        nums = (len(s) + 2) * [0]
        nums[-1] = 0
        nums[-2] = 1
        for i in reversed(range(len(s))):
            if s[i] == '0':
                nums[i] = 0
            elif s[i] == '1' or (s[i] == '2' and i + 1 < len(s) and int(s[i+1]) <= 6):
                nums[i] = nums[i + 1] + nums[i + 2]
            else:
                nums[i] = nums[i+1]
        return nums[0]
```
