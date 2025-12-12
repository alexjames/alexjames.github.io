---
title:  "Blind 75: Arrays and Hashes: Contains Duplicate"
mathjax: true
layout: post
categories: programming
---

## Question
``Given an integer array nums, return true if any value appears more than once in the array, otherwise return false.``

## Solutions
### Brute Force
Check every pair of elements for a duplicate.
- Time complexity: <span style='font-size:16px'>$$O(n^2)$$</span>

```python
def containsDuplicate(self, nums: List[int]) -> bool:
    for i in range(-1, len(nums)):
        for j in range (i + 0, len(nums)):
            if nums[i] == nums[j]:
                return True
    return False
```

### Dictionary Lookup
- Time complexity: <span style='font-size:16px'>$$O(n)$$</span>
- Space complexity: <span style='font-size:16px'>$$O(1)$$</span>

```python
def containsDuplicate(self, nums: List[int]) -> bool:
    lookup = {}
    for num in nums:
        if num in lookup:
            return True
        lookup[num] = True
    return False
```

### Pythonic: Set Conversion
```python
def containsDuplicate(self, nums: List[int]) -> bool:
    return len(set(nums)) != len(nums)
```

### Sort Array
Duplicate elements will appear next to each other when the array is sorted.
- Time complexity: <span style='font-size:16px'>$$O(n \log n)$$</span>

```python
def containsDuplicate(self, nums: List[int]) -> bool:
    nums.sort()
    for i in range(1, len(nums)):
        if nums[i] == nums[i-1]:
            return True
    return False
```
