---
title:  "Blind 75: 1D DP: Word Break"
mathjax: true
layout: post
categories: programming
---

## Question
```
Given a string s and a dictionary of strings wordDict, return true if s can be segmented into a space-separated sequence of one or more dictionary words.

Note that the same word in the dictionary may be reused multiple times in the segmentation.
```

### Solutions
First instinct is to just keep growing your window until you find a match.

```
// W R O N G //
    def wordBreak(self, s: str, wordDict: list[str]) -> bool:
        word = ""
        for c in s:
            word = word + c
            if word in wordDict:
                word = ""
        if len(word) > 0:
            return False
        return True
```

This turns out not to work when you have multiple options for a path where dictionary words may be sub-strings. Ex. "aaa" and "aaaa".

Essentially you need to do a depth first search through all options. Since this is a DFS, we can cache solutions of paths already explored and store that in an array.

```python
class Solution:
    def wordBreak(self, s: str, wordDict: list[str]) -> bool:
        dp = [False] * (len(s) + 1)
        dp[len(s)] = True
        for i in range(len(s) - 1, -1, -1):
            for word in wordDict:
                if len(word) + i <= len(s) and s[i:i+len(word)] == word:
                    dp[i] = dp[i+len(word)]
                if dp[i]:
                    break
        return dp[0]
```
