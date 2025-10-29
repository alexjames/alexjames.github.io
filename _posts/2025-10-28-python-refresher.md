---
title:  "Python Refresher"
mathjax: true
layout: post
categories: programming
---

Here is a quick Python refresher.

---

## Data Structures

| Operation | List | Dictionary | Set |
|---|---|---|---|
| Creation | <code>l = []</code><br><code>l = [1, 2, 3]</code> | <code>d = {}</code><br><code>d = {"k1": 1, "k2": 2}</code> | <code>s = set()</code><br><code>s = {1, 2, 3}</code> |
| Access | <code>l[1]</code> _index_,<br><code>l[-1]</code> _negative index_<br><code>l[2:5]</code> _range_<br><span style='font-size:12px'>$$O(1)$$</span> | <code>d[key]</code> _raises KeyError if key absent_, <span style='font-size:12px'>$$O(1)$$</span><br><code>d.get(key)</code> _defaults to None if key absent, never raises KeyError_ | <code>x in s</code><br>_average case_ <span style='font-size:12px'>$$O(1)$$</span>, _worse case_ <span style='font-size:12px'>$$O(N)$$</span> |
| Add element | <code>l.append(x)</code> _insert at end_, <span style='font-size:12px'>$$O(1)$$</span><br><code>l.insert(i, x)</code> _insert at pos i_, <span style='font-size:12px'>$$O(N)$$</span> | <code>d[key] = value</code><br><code>d.setdefault(key, value)</code> _sets key if absent, returns d[key] otherwise_ | <code>s.add(x)</code><br>_average case_ <span style='font-size:12px'>$$O(1)$$</span>, _worse case_ <span style='font-size:12px'>$$O(N)$$</span>  |
| Remove element | | |

## Code

Source code can be included by fencing the code with three backticks. Syntax highlighting works automatically when specifying the language after the backticks.

````
```javascript
function foo () {
    return "bar";
}
```
````

This would be rendered as:

```javascript
function foo () {
    return "bar";
}
```

## References
- [Data Structures: The Python Tutorial](https://docs.python.org/3/tutorial/datastructures.html)
- [The Python Wiki](https://wiki.python.org/moin/TimeComplexity)
