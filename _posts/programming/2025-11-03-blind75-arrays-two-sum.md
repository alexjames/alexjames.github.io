---
title:  "Blind 75: Arrays and Hashes: Two Sum"
mathjax: true
layout: post
categories: programming
---

## Question
`Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.`

`You may assume that each input would have exactly one solution, and you may not use the same element twice.`

## Solutions
For the two strings to be anagrams, the character frequencies of both strings must be equal.

### Brute Force
- Time Complexity: <span style='font-size:16px'>$$O(n^2)$$</span>

```python
def twoSum(self, nums: List[int], target: int) -> List[int]:
    for i in range(0, len(nums)):
        for j in range(i+1, len(nums)):
            if nums[i] + nums[j] == target:
                return [i, j]
    return [-1, -1]
```

### Dictionary Lookup
- Time Complexity: <span style='font-size:16px'>$$O(n)$$</span>
- Space Complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        lookup = {}
        for i in range(0, len(nums)):
            if target - nums[i] in lookup:
                return [lookup[target - nums[i]], i]
            lookup[nums[i]] = i
        return [-1, -1]
```
