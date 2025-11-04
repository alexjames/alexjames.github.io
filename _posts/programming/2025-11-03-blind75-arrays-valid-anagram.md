---
title:  "Blind 75: Arrays and Hashes: Valid Anagram"
mathjax: true
layout: post
categories: programming
---

## Question
``Given two strings s and t, return true if the two strings are anagrams of each other, otherwise return false.``

``An anagram is a string that contains the exact same characters as another string, but the order of the characters can be different.``

## Solutions
For the two strings to be anagrams, the character frequencies of both strings must be equal.

### Sorting
Sorting both strings should result in the same string.

```python
    def isAnagram(self, s: str, t: str) -> bool:
        return sorted(s) == sorted(t)
```

### Creating Character Frequency Arrays
```python
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False
        d1 = {}
        d2 = {}
        for c in s:
            d1[c] = d1.get(c, 0) + 1
        for c in t:
            d2[c] = d2.get(c, 0) + 1
        return d1 == d2
```

### Using Counter
```python
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False
    
        # Count characters in both strings
        from collections import Counter
        return Counter(s) == Counter(t)
```
