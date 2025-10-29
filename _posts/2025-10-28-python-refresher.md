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
| Add element | <code>l.insert(i, x)</code> _insert at pos i_, <span style='font-size:12px'>$$O(N)$$</span><br><code>l.append(x)</code> _insert at end_, <span style='font-size:12px'>$$O(1)$$</span> | <code>d[key] = value</code><br><code>d.setdefault(key, value)</code> _sets key if absent, returns d[key] otherwise_ | <code>s.add(x)</code> |
| Remove element |  <code>l.remove(x)</code> _removes first item x from list, ValueError if absent_<br><code>l.pop(i)</code> _remove item at index i, IndexError if index out of bounds_<br><code>l.pop()</code> _removes last item_ | <code>d.pop(key, default)</code> _returns value when key present, KeyError if key absent and default not provided_<br><code>del d[key]</code> _KeyError if key absent_ | <code>s.remove(x)</code> _KeyError if x absent_<br><code>s.discard(x)</code> _removes x if present_|
| Looping |  <code>for x in l</code><br><br><code>for i in range(len(l))</code><br><br><code>for i, x in enumerate(l)</code> | <code>for k, v in d.items()</code><br><br><code>for key in d.keys()</code><br><br><code>for value in d.values()</code> | <code>for x in s</code>  |
| Size<br><br>_attribute of container, always <span style='font-size:12px'>$$O(1)$$</span>_ | <code>len(l)</code> | <code>len(d)</code> | <code>len(s)</code> |

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
