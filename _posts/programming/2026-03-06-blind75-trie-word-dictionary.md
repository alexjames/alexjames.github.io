---
title:  "Blind 75: Tries: Design Add and Search Words Data Structure"
mathjax: true
layout: post
categories: programming
---

## Question
``Design a data structure that supports adding new words and finding if a string matches any previously added string.

Implement the WordDictionary class:

WordDictionary() Initializes the object.
void addWord(word) Adds word to the data structure, it can be matched later.
bool search(word) Returns true if there is any string in the data structure that matches word or false otherwise. word may contain dots '.' where dots can be matched with any letter.``

## Solutions
```python
class TrieNode:
    def __init__(self):
        self.links = {}
        self.is_end = False


class WordDictionary:
    def __init__(self):
        self.head = TrieNode()

    def addWord(self, word: str) -> None:
        node = self.head
        for ch in word:
            if not ch in node.links:
                node.links[ch] = TrieNode()
            node = node.links[ch]
        node.is_end = True    

    def search_helper(self, node: TrieNode, word: str) -> bool:
        for i in range(len(word)):
            if word[i] == '.':
                retval = False
                for k in node.links.keys():
                    retval = retval or self.search_helper(node.links[k], word[i+1:])
                return retval
            else:
                if not word[i] in node.links:
                    return False
                node = node.links[word[i]]
        return node.is_end

    def search(self, word: str) -> bool:
        return self.search_helper(self.head, word)
```
