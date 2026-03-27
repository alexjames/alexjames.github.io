---
title:  "Blind 75: Intervals: Merge Interval"
mathjax: true
layout: post
categories: programming
---

## Question
``
Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.
``

## Solutions
The key insight to simplify interval merges is to "grow" the merged interval as you iterate through the array.

- Time complexity: <span style='font-size:16px'>$$O(nlogn)$$</span>

```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        sorted_intervals = sorted(intervals, key=lambda x: x[0])
        result = []
        start = 0
        end = 1
        merged_interval = sorted_intervals[0]
        for i in range(1, len(sorted_intervals)):
            if sorted_intervals[i][start] <= merged_interval[end]:
                merged_interval[end] = max(sorted_intervals[i][end], merged_interval[end])
            else:
                result.append(merged_interval)
                merged_interval = sorted_intervals[i]
        result.append(merged_interval)
        return result
```
