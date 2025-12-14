---
title:  "Blind 75: Arrays and Hashes: Encode and Decode Strings"
mathjax: true
layout: post
categories: programming
---

## Question
``Design an algorithm to encode a list of strings to a single string. The encoded string is then decoded back to the original list of strings.``

## Solution
First instinct was to preprend the string length to the string. So "test" becomes "4test". This breaks when the string starts with a number. Example "4test" -> "54test" and this creates ambiguity, breaking the solution. The trick is to add a separator/terminating character after the length, signaling the end of the length.

###
- Time Complexity: <span style='font-size:16px'>$$O(n)$$</span>
- Space Complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
class Solution:
    def encode(self, strs: List[str]) -> str:
        encoded = ""
        for s in strs:
            encoded = encoded + str(len(s)) + '#' + s
        return encoded

    def decode(self, s: str) -> List[str]:
        result = [] 
        i = 0
        while i < len(s):
            j = s.find('#', i)
            slen = int(s[i:j])
            result.append(s[j + 1: j + 1 + slen])
            i = j + slen + 1
        return result
```

