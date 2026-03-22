---
tags:
  - cs/lang/python
created: 2026-03-18
status: draft
type: concept
---
---
## Sorting

| Method                                              | Description                                                     | Example                           |
| --------------------------------------------------- | --------------------------------------------------------------- | --------------------------------- |
| `s.sort_index(ascending=True)`                      | Sort Series by index labels                                     | `obj.sort_index()` → alphabetical |
| `df.sort_index(axis=0, ascending=True)`             | Sort DataFrame by row labels                                    | `df.sort_index()`                 |
| `df.sort_index(axis=1, ascending=True)`             | Sort DataFrame by column labels                                 | `df.sort_index(axis=1)`           |
| `s.sort_values(ascending=True, na_position='last')` | Sort Series by values; NaN goes to end by default               | `obj.sort_values()`               |
| `df.sort_values(by='col')`                          | Sort rows by a single column's values                           | `df.sort_values(by='b')`          |
| `df.sort_values(by=['col1','col2'])`                | Sort by multiple columns — first is primary, second breaks ties | `df.sort_values(by=['a','b'])`    |
```python
obj = pd.Series([4, 7, -3, 2], index=['d', 'a', 'b', 'c'])
obj.sort_index()                         # a=-3, b=2, c=?, d=4 by label
obj.sort_values()                        # -3, 2, 4, 7 by value

df.sort_values(by='b')
df.sort_values(by=['a', 'b'])            # 'a' primary, 'b' secondary
df.sort_index(axis=1, ascending=False)   # columns Z→A
```

## Ranking

`rank()` assigns integer ranks (1 = smallest by default). Ties are broken according to `method`.

| Method                                     | Description                                       | Example                     |
| ------------------------------------------ | ------------------------------------------------- | --------------------------- |
| `s.rank(method='average', ascending=True)` | Ties get the average rank of the group (default)  | `obj.rank()`                |
| `s.rank(method='first')`                   | Ties broken by order of first appearance in data  | `obj.rank(method='first')`  |
| `s.rank(method='min')`                     | All tied values get the minimum rank of the group | `obj.rank(method='min')`    |
| `s.rank(method='max')`                     | All tied values get the maximum rank of the group | `obj.rank(method='max')`    |
| `s.rank(ascending=False)`                  | Rank largest as 1 (descending rank)               | `obj.rank(ascending=False)` |
| `df.rank(axis=0)`                          | Rank within each column                           | `df.rank()`                 |
| `df.rank(axis=1)`                          | Rank within each row                              | `df.rank(axis=1)`           |

```python
obj = pd.Series([7, -5, 7, 4, 2, 0, 4])
obj.rank()
# 0    6.5   <- both 7s share ranks 6 and 7, average = 6.5
# 1    1.0
# 2    6.5
# 3    4.5   <- both 4s share ranks 4 and 5, average = 4.5
# 4    3.0
# 5    2.0
# 6    4.5

obj.rank(method='first')
# 0    6.0   <- first occurrence of 7 gets rank 6
# 2    7.0   <- second occurrence gets rank 7
```
