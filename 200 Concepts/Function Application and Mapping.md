---
tags:
  - cs/lang/python
created: 2026-03-18
status: draft
type: concept
---
---
## Function Application and Mapping

| Method                               | Description                                                                                                 | Example                                                    |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| `np.ufunc(df)`                       | NumPy ufuncs apply element-wise                                                                             | `np.abs(df)` → absolute value of every element             |
| `df.apply(func, axis=0)`             | Apply function to each **column** (default) — function receives a Series                                    | `df.apply(lambda x: x.max() - x.min())` → range per column |
| `df.apply(func, axis=1)`             | Apply function to each **row** — function receives a Series                                                 | `df.apply(lambda x: x.max(), axis=1)` → max per row        |
| `s.apply(func)`                      | Apply function to each element of a Series                                                                  | `obj.apply(lambda x: '%.2f' % x)`                          |
| `df.applymap(func)` / `df.map(func)` | Apply function to each **scalar element** of a DataFrame (`applymap` deprecated in newer pandas, use `map`) | `df.map(lambda x: '%.2f' % x)`                             |
| `s.map(func_or_dict)`                | Element-wise map — also accepts a dict for lookup substitution                                              | `obj.map({'a': 'one', 'b': 'two'})`                        |

python

```python
f = lambda x: x.max() - x.min()
df.apply(f)           # range of each column
df.apply(f, axis=1)   # range of each row

# apply can return a Series — result becomes a DataFrame
def min_max(x):
    return pd.Series([x.min(), x.max()], index=['min', 'max'])

df.apply(min_max)     # returns 2-row DataFrame
```
