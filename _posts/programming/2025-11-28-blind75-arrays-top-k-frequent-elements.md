---
title:  "Blind 75: Arrays and Hashes: Top k Frequent Elements"
mathjax: true
layout: post
categories: programming
---

## Question
``Given an integer array nums and an integer k, return the k most frequent elements within the array.``

## Solutions
For the two strings to be anagrams, their character frequencies must be equal. Our first intution in solving this problem would involve checking every pair of strings to see if they are anagrams and then group them. This is a reasonable brute-force approach.

The next thing that came to mind was sorting the array in some way so that anagrams appear next to each other. That works cause we could sort the characters of every string and then sort all the character-sorted strings. We then group those and map them to their original form.

The key insight for an optimal solution here is figuring out a way we can generate some sort of character frequency signature for every string. That way, we could just iterate through the list once and group all strings with matching signatures together. Counters or character lists won't work because they aren't hashable and can't be used a dictionary keys directly. What does work is converting those counters or character lists to strings. 


### Brute Force
```python
class Solution:
    def areAnagrams(self, stra: str, strb: str) -> bool:
        return sorted(stra) == sorted(strb)

    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        result = []
        done = [False] * len(strs)
        for i in range(0, len(strs)):
            if done[i] is not False:
                continue
            group = [strs[i]]
            done[i] = True
            for j in range(i+1, len(strs)):
                if done[j] is False and self.areAnagrams(group[0], strs[j]):
                    group.append(strs[j])
                    done[j] = True
            result.append(group)
        return result
```

### Map with sorted character list based signature
```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        sorted_strs = ["".join(sorted(x)) for x in strs]    ## join needed as sorted(x) returns a list of sorted characters
        d = {}
        for i in range(len(strs)):
            if sorted_strs[i] in d:
                d[sorted_strs[i]].append(strs[i])
            else:
                d[sorted_strs[i]] = [strs[i]]
        result = []
        for _, v in d.items():
            result.append(v)
        return result
```

### Map with character frequencies counter based signature
```python
class Solution:
    def getSignature(self, s: str) -> str:
        d = {}
        for c in s:
            d[c] = d.get(c, 0) + 1
        signature = ""
        for k in sorted(d.keys()):
            signature = signature + k + str(d[k])
        return signature

    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        d = {}
        for i in range(len(strs)):
            s = self.getSignature(strs[i])
            if s in d:
                d[s].append(strs[i])
            else:
                d[s] = [strs[i]]
        result = []
        for _, v in d.items():
            result.append(v)
        return result

### Alternative getSignature implementation
    def getSignature(self, s: str) -> str:
        items = Counter(s).items()
        return "".join(f"{char}{count}" for char, count in sorted(items))
```