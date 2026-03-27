---
title:  "Blind 75: Intervals: Meeting Rooms"
mathjax: true
layout: post
categories: programming
---

## Question
``
Given an array of meeting time interval objects consisting of start and end times [[start_1,end_1],[start_2,end_2],...] (start_i < end_i), determine if a person could add all meetings to their schedule without any conflicts.

Note: (0,8),(8,10) is not considered a conflict at 8
``

## Solutions
This is straight forward. If you sort all the meeting intervals by start time, no adjacent meetings can overlap for there to be no conflicts.

```python
class Solution:
    def canAttendMeetings(self, intervals: List[Interval]) -> bool:
        sorted_meeting_times = sorted(intervals, key=lambda x: x.start)
        start = 0
        end = 1
        for i in range(1, len(sorted_meeting_times)):
            if sorted_meeting_times[i].start < sorted_meeting_times[i-1].end:
                return False
        return True
```
