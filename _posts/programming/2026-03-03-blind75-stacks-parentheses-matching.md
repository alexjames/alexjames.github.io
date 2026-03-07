---
title:  "Blind 75: Stacks: Valid Parentheses"
mathjax: true
layout: post
categories: programming
---

## Question
``Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.``

## Solutions
# Tracking open brackets with a stack
Put all the open braces on a stack and check for a match when you encounter closing braces.

- Space complexity: <span style='font-size:16px'>$$O(n)$$</span>
- Time complexity: <span style='font-size:16px'>$$O(n)$$</span>

```python
def isValid(self, s: str) -> bool:
    stack = []
    for c in s:
        if c in ['{', '(', '[']:
            stack.append(c)
        if c == ')': 
            if len(stack) > 0 and stack[-1] == '(':
                stack.pop()
            else:
                return False
        if c == ']':
            if len(stack) > 0 and stack[-1] == '[':
                stack.pop()

            else:
                return False
        if c == '}':
            if len(stack) > 0 and stack[-1] == '{':
                stack.pop()
            else:
                return False
    if len(stack) > 0:
        return False
    return True
```
