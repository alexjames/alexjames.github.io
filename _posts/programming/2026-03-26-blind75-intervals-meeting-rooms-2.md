---
title:  "Blind 75: Intervals: Meeting Rooms 2"
mathjax: true
layout: post
categories: programming
---

## Question
``
Given an array of meeting time interval objects consisting of start and end times [[start_1,end_1],[start_2,end_2],...] (start_i < end_i), find the minimum number of rooms required to schedule all meetings without any conflicts.

``

## Solutions
This is the classic interview room scheduling problem. This requires a couple of insights -
(1) The minimum number of rooms you need is the number of concurrent meetings in the busiest time block.
(2) We need an efficient way to find this time block.
(3) Iterating through intervals in some predefined order here is inefficient because you would have to go back to check each time block it intersects with and track counts of those blocks.
(4) If you imagine simulating a clock, moving from one time block to the next, you could track of the number of rooms required for the current time block. That would be the number of ongoing meetings. For any time T, this can be calculated as `meetings that started at or before T - meetings that ended by T`.
(5) This leads us to consider sorting the start and end times of all meetings. You can then use these to compute the number of ongoing meetings.

- Time complexity: <span style='font-size:16px'>$$O(nlogn)$$</span>
- Space complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
class Solution:
    def minMeetingRooms(self, intervals: List[Interval]) -> int:
        start_times = sorted([interval.start for interval in intervals])
        end_times = sorted([interval.end for interval in intervals])
        count = 0
        max_count = 0
        i = j = 0
        while i < len(start_times):
            if start_times[i] < end_times[j]:
                count += 1
                i += 1
            else:
                count -= 1
                j += 1
            max_count = max(max_count, count)
        return max_count
```
