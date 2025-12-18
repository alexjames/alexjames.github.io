---
title:  "Blind 75: Arrays and Hashes: Products of Array Except Self"
mathjax: true
layout: post
categories: programming
---

## Question
``Given an array of integers nums, return the length of the longest consecutive sequence of elements that can be formed.``

``A consecutive sequence is a sequence of elements in which each element is exactly 1 greater than the previous element. The elements do not have to be consecutive in the original array.``

## Solution


###
- Time Complexity: <span style='font-size:16px'>$$O(n)$$</span>
- Space Complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        max_length = 0
        d = {}
        for num in nums:
            if num in d:
                continue
            before = d.get(num - 1, None)
            after = d.get(num + 1, None)

            start = -1
            end = 1
            if before == None and after == None:
                start = num
                end = num
                d[num] = (start, end)
            elif before == None: # num is start of seq
                start = num
                end = after[1]
                d[num] = (start, end)
                d[end] = (start, end)
            elif after == None: # num is end of seq
                start = before[0]
                end = num
                d[start] = (start, end)
                d[num] = (start, end)
            else: # if both before a set, join the two
                start = before[0]
                end = after[1]
                d[start] = (start, end)
                d[end] = (start, end)
                d[num] = (start, end)
            max_length = max(max_length, end-start+1)
        return max_length
```

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        max_length = 0
        num_set = set(nums)
        for num in nums:
            # check if start of sequence, if not, skip
            if num - 1 in num_set:
                continue
            i = num
            seq_len = 0
            while i in num_set:
                seq_len = seq_len + 1
                i = i + 1
            max_length = max(max_length, seq_len)
        return max_length
```
