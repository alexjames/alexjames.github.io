---
title:  "Blind 75: Two Pointers: Container With Most Water"
mathjax: true
layout: post
categories: programming
---

## Question
``You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).``

``Find two lines that together with the x-axis form a container, such that the container contains the most water``

## Solution
This is essentially an optimization problem. We are trying to maximie $$min(height[i], height[j]) * (j - i)$$.

We have two factors we are trying to maximize here. We have the heights of the container edges and the distance between them. To do this in $$O(n)$$, there is a greedy solution that works. Let's try and build the intuition for this.

Assume we start with the two edges furthest apart from one another i.e. (j - i) is the max. We only have one possibility for a container where (j - i) is the maximum value. If we try to take a step down, i.e. j - i - 1, we now have two possibilities. Container with i = 0, j = len(heights) - 2 and container with i = 1, j = len(heights) - 1. So we either pick a container with an edge we have already seen i.e. either the left container with i = 0 or the right container with j = len(heights) - 1. Which side we choose, the maximum value of the chosen container will be limited by the height of that side. Thus we are incentivized to keep the side with highest height value.

Once we pick the side with max(heights[0], heights[len(heights) - 1]), we now have an array of length = len(heights) - 1. We can now recursively apply the same logic until we consider the last container whose sides are next to one another.

With each step, we rule out a side (either to the left or the right) that "could" minimize the capacity of the container. It might still be the side which ultimately gives us the highest capacity, which would be the case if all subsequent heights were equal or lower in value.

### Greedy Approach using Two Pointers
- Time Complexity: <span style='font-size:16px'>$$O(n)$$</span>
- Space Complexity: <span style='font-size:16px'>$$O(1)$$</span>

```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        max_capacity = 0
        i = 0
        j = len(height) - 1
        while i < j:
            c = min(height[i], height[j]) * (j - i)
            max_capacity = max(max_capacity, c)
            if height[j] < height[i]:
                j = j - 1
            else:
                i = i + 1
        return max_capacity
```
