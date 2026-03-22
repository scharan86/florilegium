---
tags:
  - cs/lang/python
created: 2026-03-18
status: draft
type: concept
---
---

>[!Definition]
>A `Series` is a one-dimensional array-like object with an associated array of **labels** called its **index**. It is the building block of a DataFrame — each column is a Series.

### Creating a Series

| Function                                             | Description                                  | Example                                          |
| ---------------------------------------------------- | -------------------------------------------- | ------------------------------------------------ |
| `pd.Series(data, index=None, dtype=None, name=None)` | Create from list, ndarray, dict, or scalar   | `pd.Series([4, 7, -5, 3])` → auto-index 0,1,2,3  |
| `pd.Series(data, index=[...])`                       | Create with explicit labels                  | `pd.Series([4,7,-5,3], index=['d','b','a','c'])` |
| `pd.Series(dict)`                                    | Keys become index labels, values become data | `pd.Series({'a': 1, 'b': 2})`                    |
| `pd.Series(scalar, index=[...])`                     | Scalar broadcast to every index label        | `pd.Series(5, index=['a','b','c'])` → all 5s     |

python

```python
import pandas as pd
import numpy as np

obj = pd.Series([4, 7, -5, 3])
# 0    4
# 1    7
# 2   -5
# 3    3

obj2 = pd.Series([4, 7, -5, 3], index=['d', 'b', 'a', 'c'])
obj2['a']              # -5
obj2[['a', 'b', 'c']] # select multiple labels
```

### Series Attributes

|Attribute|Description|Example|
|---|---|---|
|`s.values`|Underlying NumPy ndarray|`obj.values` → `array([4, 7, -5, 3])`|
|`s.index`|Index object (labels)|`obj.index` → `RangeIndex(start=0, stop=4)`|
|`s.name`|Name of the Series|`obj.name = 'population'`|
|`s.index.name`|Name of the index axis|`obj.index.name = 'state'`|
|`s.dtype`|Data type of values|`obj.dtype` → `dtype('int64')`|

### Series Operations

|Operation|Description|Example|
|---|---|---|
|`s[label]`|Select single element by label|`obj2['b']` → `7`|
|`s[s > 0]`|Boolean filter — returns Series of matching elements|`obj2[obj2 > 0]` → labels and values where > 0|
|`s * 2`|Scalar arithmetic applied element-wise|`obj2 * 2` → all values doubled|
|`np.exp(s)`|NumPy ufuncs work directly on a Series|`np.exp(obj2)` → eˣ per element|
|`'label' in s`|Check if a label exists in the index|`'b' in obj2` → `True`|
|`pd.isnull(s)` / `pd.notnull(s)`|Detect NaN — returns boolean Series|`pd.isnull(obj2)` → `True` where NaN|
|`s.isnull()` / `s.notnull()`|Same as above as instance methods|`obj2.isnull()`|

**Key property:** When doing arithmetic between two Series, values are **automatically aligned by index label**, not by position. Labels present in only one Series produce `NaN`.

python

```python
obj3 = pd.Series({'Ohio': 35000, 'Texas': 71000, 'Oregon': 16000})
obj4 = pd.Series({'California': np.nan, 'Ohio': 35000, 'Oregon': 16000, 'Texas': 71000})
obj3 + obj4
# California        NaN   <- only in obj4
# Ohio          70000.0
# Oregon        32000.0
# Texas        142000.0
```

## Related Concepts
