---
tags:
  - cs/lang/python
created: 2026-05-02
status: draft
type: concept
aliases:
  - MultiIndex
---
g---

>[!Definition]
> Hierarchical index allows two us to use multiple index levels on a single axis.
>

**Allows us to represent higher dimensional data** in a single axis. 

```python
import pandas as pd
import numpy as np 

data = pd.Series(np.random.randn(9), index=[['a','a', 'a', 'b','b','b','c','c','c'], [1,2,3,1,4,2,3,5,6]])
print(data)
print("output of data.index")
data.index
```

```OUTPUT
OUTPUT:
a  1   -0.761768
   2   -0.790521
   3   -0.199081
b  1    2.096258
   4    1.011914
   2   -0.868187
c  3    0.328140
   5   -0.489420
   6    0.326423
dtype: float64

output of data.index
MultiIndex([('a', 1),
            ('a', 2),
            ('a', 3),
            ('b', 1),
            ('b', 4),
            ('b', 2),
            ('c', 3),
            ('c', 5),
            ('c', 6)],
           )
```

## `Stack()` and `Unstack()`

`Unstack()`  converts the inner index into a column (`DataFrame`)
`Stack()` reverses it back to `Series`. 

>[!note] It fills with `NaN` if the combination doesn't exist in original data.


![[Pasted image 20260502153724.png]]

# `MultiIndex` in `DataFrame`

```python
frame = pd.DataFrame(np.arange(12).reshape((4, 3)),

index=[['a','a','b','b'], [1,2,1,2]],

columns=[['Ohio','Ohio','Colorado'],

['Green','Red','Green']])
```
```OUTPUT
OUTPUT: 
     Ohio     Colorado
    Green Red    Green
a 1     0   1        2
  2     3   4        5
b 1     6   7        8
  2     9  10       11
```
## Summary
It lets you represent highly dimensional data within a single axis making it easy to understand and work with. 
## Related Concepts
