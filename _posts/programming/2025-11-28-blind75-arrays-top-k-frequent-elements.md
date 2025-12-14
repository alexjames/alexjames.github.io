---
title:  "Blind 75: Arrays and Hashes: Top k Frequent Elements"
mathjax: true
layout: post
categories: programming
---

## Question
``Given an integer array nums and an integer k, return the k most frequent elements within the array.``

## Solutions


### 
```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        d = {}
        for num in nums:
            d[num] = d.get(num, 0) + 1
        counts = list(d.items())
        counts.sort(key=lambda x: x[1], reverse=True)
        result = []
        for i in range(k):
            result.append(counts[i][0])
        return result
```

### 
```python
import heapq
class Solution:
    def test_function(self, nums, k):
        counts = {}
        for num in nums:
            counts[num] = counts.get(num, 0) + 1
        heap = [(-v, k) for k, v in counts.items()]
        heapq.heapify(heap)
        results = []
        for i in range(k):
            results.append(heapq.heappop(heap)[1])
        return r
```
#### 
```python
import heapq
from collections import Counter

class Solution:
    def test_function(self, nums, k):
        counts = Counter(nums) 
        heap = [(-v, k) for k, v in counts.items()]
        heapq.heapify(heap)
        results = []
        for i in range(k):
            results.append(heapq.heappop(heap)[1])
        return results
```

### Pythonic Way
```python
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        return [x[0] for x in Counter(nums).most_common(k)]    def getSignature(self, s: str) -> str:
        items = Counter(s).items()
        return "".join(f"{char}{count}" for char, count in sorted(items))
```