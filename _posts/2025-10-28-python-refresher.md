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
| Description | Mutable, ordered collection of arbitrary Python objects. Internally these are implemented as arrays, allowing <span style='font-size:12px'>$$O(1)$$</span> indexed access. Inserting or removing at the beginning of the list is <span style='font-size:12px'>$$O(N)$$</span> because all elements after that need to be moved. Insertions may also trigger array growth, resulting in re-allocation and copying all elements to the new location. Mutations at the end of the list are <span style='font-size:12px'>$$O(1)$$</span>.| Mutable, unordered collection of key-value pairs. Keys are unique and cannot be mutable. Represented internally as a hash table, using the open addressing with probing strategy for key allocation. The average time complexity for most operations is <span style='font-size:12px'>$$O(1)$$</span> and <span style='font-size:12px'>$$O(N)$$</span> in the worse case. | Mutable, unordered collection of unique Python objects. Support mathematical set operations such as union, intersection and difference. Cannot contain mutable objects. Implementation very similar to dictionaries. The average time complexity for most operations is <span style='font-size:12px'>$$O(1)$$</span> and <span style='font-size:12px'>$$O(N)$$</span> in the worse case. |
| Creation | <code>l = []</code><br><code>l = [1, 2, 3]</code> | <code>d = {}</code><br><code>d = {"k1": 1, "k2": 2}</code> | <code>s = set()</code><br><code>s = {1, 2, 3}</code> |
| Access | <code>l[i]</code> _index_,<br><code>l[-i]</code> _negative index_<br><code>l[i:j]</code> _range_ | <code>d[key]</code> _raises KeyError if key absent_<br><code>d.get(key)</code> _defaults to None if key absent, never raises KeyError_ | <code>x in s</code> |
| Add element | <code>l.append(x)</code> _insert at end_, <span style='font-size:12px'>$$O(1)$$</span><br><code>l.insert(i, x)</code> _insert at pos i_, <span style='font-size:12px'>$$O(N)$$</span> | <code>d[key] = value</code><br><code>d.setdefault(key, value)</code> _sets key if absent, returns d[key] otherwise_ | <code>s.add(x)</code> |
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
