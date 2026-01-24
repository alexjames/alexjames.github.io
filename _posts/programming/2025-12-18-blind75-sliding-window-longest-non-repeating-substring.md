---
title:  "Blind 75: Sliding Window: Longest Substring Without Repeating Characters"
mathjax: true
layout: post
categories: programming
---

## Question
``Given a string s, find the length of the longest substring without duplicate characters.``

## Solution
How do you determine that a problem might be a good candidate for a sliding window sort of solution? One indication could be when the solution has to do with selecting some bounds within a sequence.

### Using string reverse
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        max_length = 0
        i = 0
        j = 0
        d = {}
        while j < len(s):
            if d.get(s[j]) is None:
                d[s[j]] = True
                max_length = max(max_length, j - i + 1)
                j = j + 1
            else:
                while i <= j and s[i] != s[j]:
                    d.pop(s[i])
                    i = i + 1
                i = i + 1
                j = j + 1
        return max_length
```
