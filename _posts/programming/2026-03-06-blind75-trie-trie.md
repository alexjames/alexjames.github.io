---
title:  "Blind 75: Tries: Implement Trie (Prefix Tree)"
mathjax: true
layout: post
categories: programming
---

## Question
``A trie (pronounced as "try") or prefix tree is a tree data structure used to efficiently store and retrieve keys in a dataset of strings. There are various applications of this data structure, such as autocomplete and spellchecker.

Implement the Trie class:

Trie() Initializes the trie object.
void insert(String word) Inserts the string word into the trie.
boolean search(String word) Returns true if the string word is in the trie (i.e., was inserted before), and false otherwise.
boolean startsWith(String prefix) Returns true if there is a previously inserted string word that has the prefix prefix, and false otherwise.``

## Solutions
- Time complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
class TrieNode:
    def __init__(self):
        self.links = {}
        self.is_end = False

class Trie:
    def __init__(self):
        self.head = TrieNode()

    def insert(self, word: str) -> None:
        node = self.head
        for ch in word:
            if not ch in node.links:
                node.links[ch] = TrieNode()
            node = node.links[ch]
        node.is_end = True

    def search(self, word: str) -> bool:
        node = self.head
        for ch in word:
            if not ch in node.links:
                return False
            node = node.links[ch]
        return node.is_end

    def startsWith(self, prefix: str) -> bool:
        node = self.head
        for ch in prefix:
            if not ch in node.links:
                return False
            node = node.links[ch]
        return True
```
