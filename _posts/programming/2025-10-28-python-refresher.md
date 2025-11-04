---
title:  "Python Refresher"
mathjax: true
layout: post
categories: programming
---

Here is a quick Python refresher.

---

## Data Structures

| | List | Dictionary | Set |
|---|---|---|---|
| Description | Mutable, ordered collection of arbitrary Python objects. Internally these are implemented as arrays, allowing <span style='font-size:12px'>$$O(1)$$</span> indexed access. Inserting or removing at the beginning of the list is <span style='font-size:12px'>$$O(N)$$</span> because all elements after that need to be moved. Insertions may also trigger array growth, resulting in re-allocation and copying all elements to the new location. Mutations at the end of the list are <span style='font-size:12px'>$$O(1)$$</span>.| Mutable, unordered collection of key-value pairs. Keys are unique and cannot be mutable. Represented internally as a hash table, using the open addressing with probing strategy for key allocation. The average time complexity for most operations is <span style='font-size:12px'>$$O(1)$$</span> and <span style='font-size:12px'>$$O(N)$$</span> in the worse case. | Mutable, unordered collection of unique Python objects. Support mathematical set operations such as union, intersection and difference. Cannot contain mutable objects. Implementation very similar to dictionaries. The average time complexity for most operations is <span style='font-size:12px'>$$O(1)$$</span> and <span style='font-size:12px'>$$O(N)$$</span> in the worse case. |
| Creation | <code>l = []</code><br><code>l = [1, 2, 3]</code> | <code>d = {}</code><br><code>d = {"k1": 1, "k2": 2}</code><br><code>d = dict(foo=1, bar='nope')</code> | <code>s = set()</code><br><code>s = {1, 2, 3}</code><br><code>s = set([1, 2, 3])</code> |
| Access | <code>l[i]</code> _index_,<br><code>l[-i]</code> _negative index_<br><code>l[i:j]</code> _range_ | <code>d[key]</code> _raises KeyError if key absent_<br><code>d.get(key)</code> _defaults to None if key absent, never raises KeyError_ | <code>x in s</code> |
| Add element | <code>l.insert(i, x)</code> _insert at pos i_, <span style='font-size:12px'>$$O(N)$$</span><br><code>l.append(x)</code> _insert at end_, <span style='font-size:12px'>$$O(1)$$</span> | <code>d[key] = value</code><br><code>d.setdefault(key, value)</code> _sets key if absent, returns d[key] otherwise_ | <code>s.add(x)</code> |
| Remove element |  <code>l.remove(x)</code> _removes first item x from list, ValueError if absent_<br><code>l.pop(i)</code> _remove item at index i, IndexError if index out of bounds_<br><code>l.pop()</code> _removes last item_ | <code>d.pop(key, default)</code> _returns value when key present, KeyError if key absent and default not provided_<br><code>del d[key]</code> _KeyError if key absent_ | <code>s.remove(x)</code> _KeyError if x absent_<br><code>s.discard(x)</code> _removes x if present_ |
| Delete everything | <code>l.clear()</code> | <code>d.clear()</code> | <code>s.clear()</code> |
| Looping |  <code>for x in l</code><br><br><code>for i in range(len(l))</code><br><br><code>for i, x in enumerate(l)</code> | <code>for k, v in d.items()</code><br><br><code>for key in d.keys()</code><br><br><code>for value in d.values()</code> | <code>for x in s</code>  |
| Size<br><br>_attribute of container, always <span style='font-size:12px'>$$O(1)$$</span>_ | <code>len(l)</code> | <code>len(d)</code> | <code>len(s)</code> |
| Equality | <code>l1 == l2</code> | <code>d1 == d2</code> | <code>s1 == s2</code> |
| Combine | <code>l1 + l2</code><br><code>l1.extend(l2)</code> | <code>d1 | d2</code><br><code>d1 |= d2</code> | <code>s1 | s2</code><br><code>s1 |= s2</code> |
| Unique Operations | <code>l.sort()</code><br><br><code>l.reverse()</code><br><br><code>l.count(x)</code> _number of occurences of x_<br><br><code>l.index(x)</code> _index of first occurence of x_ | <code>d1 | d2</code> _union_<br><br><code>d1 & d2</code> _intersection_<br><br><code>d1 - d2</code> _difference_<br><br><code>d1 ^ d2</code> _symmetric difference_ |<code>s1 | s2</code> _union_<br><br><code>s1 & s2</code> _intersection_<br><br><code>s1 - s2</code> _difference_<br><br><code>s1 ^ s2</code> _symmetric difference_<br><br><code>s1 < s2</code> _True if s1 subset of s2_<br><br><code>s1 > s2</code> _True if s1 superset of s2_ |

All built-in containers support the functions `min`, `max`, `sum`, `sorted`, `reversed`, `enumerate` and `zip`.

Assignments using `=` sets the variable to point to the same location in memory, referencing the same object. Using a container's `copy()` function creates a shallow copy i.e. top-level immutable types like integers and strings will be copied over, while only references to nested objects such as lists will be copied.
To create a true (deep) copy of everything included nested objects, use the `deepcopy` function.

```python
import copy

### WRONG, new_dict references objects of old_dict
new_dict = old_dict

### CORRECT
new_dict = copy.deepcopy(old_dict)
```

### List Comprehensions
List comprehensions provide a concise way to create new lists.
```python
squares = [x**2 for x in range(10)]

even_nums = [x for x in range(-10, 10) if x % 2 == 0]
```

## References
- [Data Structures: The Python Tutorial](https://docs.python.org/3/tutorial/datastructures.html)
- [The Python Wiki](https://wiki.python.org/moin/TimeComplexity)
- [copy](https://docs.python.org/3/library/copy.html)
- [stdtypes](https://docs.python.org/3/library/stdtypes.html)
