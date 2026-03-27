---
title:  "Blind 75: Intervals: Insert Interval"
mathjax: true
layout: post
categories: programming
---

## Question
``
You are given an array of non-overlapping intervals intervals where intervals[i] = [starti, endi] represent the start and the end of the ith interval and intervals is sorted in ascending order by starti. You are also given an interval newInterval = [start, end] that represents the start and end of another interval.

Insert newInterval into intervals such that intervals is still sorted in ascending order by starti and intervals still does not have any overlapping intervals (merge overlapping intervals if necessary).

Return intervals after the insertion.
``

## Solutions
The key insight to simplify interval merges is to "grow" the merged interval as you iterate through the array.

- Time complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
class Solution:
    def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]:
        result = []
        i = 0
        start = 0
        end = 1
        if len(intervals) == 0:
            return [newInterval]
        while i < len(intervals):
            if intervals[i][end] < newInterval[start]:
                result.append(intervals[i])
                i = i + 1
            else:
                while i < len(intervals) and newInterval[end] >= intervals[i][start]:
                    newInterval = [min(newInterval[start], intervals[i][start]), max(newInterval[end], intervals[i][end])]
                    i = i + 1
                result.append(newInterval)
                break
        while i < len(intervals):
            result.append(intervals[i])
            i = i + 1
        if result[-1][end] < newInterval[start]:
            result.append(newInterval)
        return result
```