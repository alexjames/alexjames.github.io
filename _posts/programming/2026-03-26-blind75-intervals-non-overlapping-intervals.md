---
title:  "Blind 75: Intervals: Non-overlapping Intervals"
mathjax: true
layout: post
categories: programming
---

## Question
``
Given an array of intervals intervals where intervals[i] = [starti, endi], return the minimum number of intervals you need to remove to make the rest of the intervals non-overlapping.

Note that intervals which only touch at a point are non-overlapping. For example, [1, 2] and [2, 3] are non-overlapping.
``

## Solutions
This is kind of tricky. This seems like an optimization problem and it's not clear what the optimal number is to remove.

In order to arrive at the right approach, it's important to have some insights - 
(1) You can fram this problem in two ways - "keep the maximum number of non-overlapping intervals" or "remove the minimum number of  intervals so none of rest overlap".
(2) We want non-overlapping intervals. Implying that for any unit distance, we can only permit one interval to remain in the final
solution. This means that we must pick only interval that overlaps with that unit distance.
(3) Between any two intervals, would you pick the longer or shorter interval? You might think the shorter one is more optimal. Turns out,
if you are looking at intervals in sorted order, it is optimal to pick the one that ends first. This is because it's always more advantageous to pick the interval that stretches the least into the future, leaving more room for other intervals. In every case where you might consider picking the later-ending interval, the earlier ending interval would also work. Hence, the greedy method of picking the earliest end-time is optimal.

- Time complexity: <span style='font-size:16px'>$$O(nlogn)$$</span>

### Sorting by start time 
```python
class Solution:
    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
        sorted_intervals = sorted(intervals)
        start = 0
        end = 1
        prev_end = sorted_intervals[0][end]
        remove = 0
        for i in range(1, len(sorted_intervals)):
            if sorted_intervals[i][start] >= prev_end:
                prev_end = sorted_intervals[i][end]
                continue
            else:
                prev_end = min(sorted_intervals[i][end], prev_end)
                remove += 1
        return remove
```


### Sorting by end time
```python
class Solution:
    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
        sorted_intervals = sorted(intervals, key=lambda x: x[1])
        start = 0
        end = 1
        remove = 0
        prev_interval = sorted_intervals[0]
        for i in range(1, len(sorted_intervals)):
            if sorted_intervals[i][start] < prev_interval[end]:
                remove += 1
            else:
                prev_interval = sorted_intervals[i]
        return remove
```