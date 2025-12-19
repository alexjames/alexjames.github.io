---
title:  "Blind 75: Two Pointers: Container With Most Water"
mathjax: true
layout: post
categories: programming
---

## Question
``Check if a string is a palindrome or not.

Extension: Make it case insensitive and ignore non-alphanumeric characters.``

## Solutions
### Using string reverse
```python
def isPalindrome(s: str) -> bool:
	return str == "".join(reversed(str))
```

### Pre-processing the string (stripping all non-alphanumeric characters)
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        stripped = "".join(c for c in s if c.isalnum())
        i = 0
        j = len(stripped) - 1
        while i < j:
            if stripped[i].lower() != stripped[j].lower():
                return False
            i = i + 1
            j = j - 1
        return True
```

### Without pre-processing
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        i = 0
        j = len(s) - 1
        while i < j:
            while not s[i].isalnum() and i < len(s):
                i = i + 1
            while not s[j].isalnum() and j >= 0:
                j = j - 1
            if s[i].lower() != s[j].lower():
                return False
            i = i + 1
            j = j - 1
        return True
```