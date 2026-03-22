---
tags:
  - cs/lang/python
created: 2026-03-18
status: draft
type: concept
---
---

>[!Definition]
>A `DataFrame` is a rectangular table — a dict of Series all sharing the same index. Each column can have a different dtype. It has both a **row index** and a **column index**.

### Creating a DataFrame

| Function                                         | Description                                                            | Example                                                                   |
| ------------------------------------------------ | ---------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `pd.DataFrame(dict_of_lists)`                    | Keys → column names, lists → column values                             | `pd.DataFrame({'pop': [1.5, 1.7], 'state': ['OH','TX']})`                 |
| `pd.DataFrame(data, columns=[...])`              | Specify column order explicitly                                        | `pd.DataFrame(data, columns=['year','state','pop'])`                      |
| `pd.DataFrame(data, columns=[...], index=[...])` | Specify both column and row labels                                     | `pd.DataFrame(data, columns=['year','state','pop'], index=['one','two'])` |
| `pd.DataFrame(dict_of_Series)`                   | Each Series becomes a column; row index is union of all Series indices | `pd.DataFrame({'col1': s1, 'col2': s2})`                                  |
| `pd.DataFrame(list_of_dicts)`                    | Each dict becomes a row; keys become column names                      | `pd.DataFrame([{'a':1,'b':2},{'a':3,'b':4}])`                             |

python

```python
data = {
    'state': ['Ohio', 'Ohio', 'Nevada'],
    'year':  [2000, 2001, 2002],
    'pop':   [1.5, 1.7, 3.6]
}
df = pd.DataFrame(data)
df = pd.DataFrame(data, columns=['year', 'state', 'pop'])
```

### DataFrame Attributes

|Attribute|Description|Example|
|---|---|---|
|`df.columns`|Column index object|`df.columns` → `Index(['year','state','pop'])`|
|`df.index`|Row index object|`df.index` → `RangeIndex(start=0, stop=3)`|
|`df.shape`|(rows, cols) tuple|`df.shape` → `(3, 3)`|
|`df.dtypes`|dtype of each column|`df.dtypes` → Series of dtypes|
|`df.values`|Underlying 2D NumPy array|`df.values` → ndarray|
|`df.T`|Transpose — swap rows and columns|`df.T`|

### Selecting Columns and Rows

| Operation             | Description                                                                              | Example                            |
| --------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------- |
| `df['col']`           | Select single column → returns **Series**                                                | `df['state']`                      |
| `df[['col1','col2']]` | Select multiple columns → returns **DataFrame**                                          | `df[['year','pop']]`               |
| `df.col`              | Attribute-style access (only if name is a valid Python identifier and not a method name) | `df.state` → same as `df['state']` |
| `df.loc['row_label']` | Select row by label → returns **Series**                                                 | `df.loc['one']`                    |
| `df.iloc[row_int]`    | Select row by integer position → returns **Series**                                      | `df.iloc[0]`                       |

### Adding and Deleting Columns

| Operation                | Description                                                           | Example                                |
| ------------------------ | --------------------------------------------------------------------- | -------------------------------------- |
| `df['new_col'] = scalar` | Assign scalar — broadcast to all rows                                 | `df['debt'] = 16.5`                    |
| `df['new_col'] = series` | Assign Series — auto-aligned to DataFrame index; missing labels → NaN | `df['eastern'] = (df.state == 'Ohio')` |
| `del df['col']`          | Delete column in-place                                                | `del df['eastern']`                    |
| `df.pop('col')`          | Remove and return a column                                            | `col = df.pop('debt')`                 |

---

## Index Objects

Index objects store axis labels and are **immutable** — you cannot modify individual labels. They can hold duplicate labels.

|Operation|Description|Example|
|---|---|---|
|`df.index`|Row index of a DataFrame|`df.index` → `Index(['a','b','c'])`|
|`df.columns`|Column index|`df.columns` → `Index(['one','two'])`|
|`'label' in index`|Membership test|`'Ohio' in df.index` → `True/False`|
|`index[slice]`|Slicing returns a new Index|`df.index[1:3]`|
|`df.index = new_labels`|Relabel the entire index (replaces, does not rearrange)|`df.index = ['x','y','z']`|
|`df.rename(index=dict, columns=dict)`|Rename specific labels via a mapping|`df.rename(columns={'one': 'ONE'})`|

### Reindexing

`reindex` creates a **new object** conforming to a specified set of labels. Missing labels get `NaN` by default.

|Method|Description|Example|
|---|---|---|
|`s.reindex(new_index, fill_value=np.nan)`|Rearrange to new labels; missing → NaN or fill_value|`obj.reindex(['a','b','c','d','e'])`|
|`s.reindex(new_index, method='ffill')`|Forward-fill missing values from the previous valid label|`obj.reindex(range(6), method='ffill')`|
|`s.reindex(new_index, method='bfill')`|Backward-fill missing values from the next valid label|`obj.reindex(range(6), method='bfill')`|
|`df.reindex(new_row_index)`|Reindex rows|`df.reindex(['a','b','c','d'])`|
|`df.reindex(columns=new_cols)`|Reindex columns|`df.reindex(columns=['Texas','Utah','California'])`|

python

```python
obj = pd.Series([4.5, 7.2, -5.3, 3.6], index=['d', 'b', 'a', 'c'])
obj.reindex(['a', 'b', 'c', 'd', 'e'])
# a   -5.3
# b    7.2
# c    3.6
# d    4.5
# e    NaN   <- new label, filled with NaN

# Forward fill — useful for ordered/time-indexed data
obj2 = pd.Series(['blue', 'purple', 'yellow'], index=[0, 2, 4])
obj2.reindex(range(6), method='ffill')
# 0      blue
# 1      blue    <- filled from 0
# 2    purple
# 3    purple   <- filled from 2
# 4    yellow
# 5    yellow   <- filled from 4
```

---

## Dropping Entries

|Method|Description|Example|
|---|---|---|
|`s.drop(labels)`|Drop labels — returns **new** Series|`obj.drop('c')` or `obj.drop(['b','c'])`|
|`df.drop(labels, axis=0)`|Drop rows by label (axis=0 default)|`df.drop(['Colorado','Ohio'])`|
|`df.drop(labels, axis=1)`|Drop columns by label|`df.drop('two', axis=1)`|
|`df.drop(labels, axis='columns')`|Same with keyword alias|`df.drop(['two','four'], axis='columns')`|
|`df.drop(labels, inplace=True)`|Modify in-place — no return value|`df.drop('col', axis=1, inplace=True)`|

python

```python
obj = pd.Series(np.arange(5.), index=['a','b','c','d','e'])
obj.drop('c')             # array without 'c'
obj.drop(['d', 'c'])      # array without 'd' and 'c'

df.drop(['Colorado', 'Ohio'])     # drop rows
df.drop('two', axis=1)            # drop column 'two'
```

---

## Indexing, Selection, and Filtering

### Series Indexing

|Operation|Description|Example|
|---|---|---|
|`s['label']`|Select by label|`obj['b']` → scalar|
|`s[int]`|Select by integer position|`obj[1]` → scalar|
|`s['a':'c']`|Label-based slice — **end label is inclusive**|`obj['b':'d']` → labels b through d|
|`s[0:3]`|Integer slice — end is **exclusive** (like Python)|`obj[1:3]` → positions 1, 2|
|`s[bool_array]`|Boolean filtering|`obj[obj < 2]` → elements < 2|

### DataFrame Indexing

| Operation                       | Description                                      | Example                                    |
| ------------------------------- | ------------------------------------------------ | ------------------------------------------ |
| `df['col']`                     | Select column → Series                           | `df['one']`                                |
| `df[bool_series]`               | Boolean Series selects rows                      | `df[df['b'] > 5]` → rows where col 'b' > 5 |
| `df[bool_df]`                   | Boolean DataFrame → NaN where False, keeps shape | `df[df < 5]` → values >= 5 become NaN      |
| `df.loc[row, col]`              | Label-based selection for both axes              | `df.loc['Colorado', ['two','three']]`      |
| `df.loc[row_slice, col_slice]`  | Label-based slicing — both ends inclusive        | `df.loc[:'Utah', 'two':]`                  |
| `df.iloc[row_int, col_int]`     | Integer-position selection for both axes         | `df.iloc[2, [3, 0, 1]]`                    |
| `df.iloc[row_slice, col_slice]` | Integer slicing — end exclusive                  | `df.iloc[:3, :2]`                          |
| `df.at[row_label, col_label]`   | Fast scalar access by label                      | `df.at['Ohio', 'pop']`                     |
| `df.iat[row_int, col_int]`      | Fast scalar access by integer position           | `df.iat[0, 2]`                             |

```python
# .loc — label-based, slices are end-inclusive
df.loc['Colorado', ['two', 'three']]
df.loc[:'Utah', 'two':]

# .iloc — integer-based, slices are end-exclusive
df.iloc[2]
df.iloc[2, [3, 0, 1]]
df.iloc[:3, :2]

# Boolean selection
df[df < 5]           # values >= 5 become NaN, shape preserved
df[df['b'] > 5]      # entire rows where column 'b' > 5
```

---

## Arithmetic and Data Alignment

When adding two Series or DataFrames, Pandas **aligns on index labels** before operating. Labels present in only one object produce `NaN`.

|Operation|Description|Example|
|---|---|---|
|`s1 + s2`|Align by label, then add; missing → NaN|`s1 + s2`|
|`df1 + df2`|Align by row and column label, then add|`df1 + df2`|
|`s.add(other, fill_value=0)`|Addition — use fill_value instead of NaN for missing labels|`s1.add(s2, fill_value=0)`|
|`df.add(other, fill_value=0)`|Same for DataFrame|`df1.add(df2, fill_value=0)`|
|`df.sub(other, fill_value=v)`|Subtraction with fill|`df1.sub(df2, fill_value=0)`|
|`df.mul(other, fill_value=v)`|Multiplication with fill|`df1.mul(df2, fill_value=1)`|
|`df.div(other, fill_value=v)`|Division with fill|`df1.div(df2, fill_value=1)`|
|`df.radd(other)` / `df.rsub(other)`|Reversed operations: `other + df`, `other - df`|`df.rdiv(1)` → same as `1 / df`|

### DataFrame with Series — Broadcasting

By default, arithmetic between a DataFrame and a Series broadcasts along **axis=1** (matches Series index to column labels):

python

```python
df = pd.DataFrame(np.arange(12.).reshape((4, 3)),
                  columns=list('bde'),
                  index=['Utah', 'Ohio', 'Texas', 'Oregon'])
series = df.iloc[0]        # first row as Series: b=0, d=1, e=2

df - series                # subtracts series from every row (column labels matched)

# To broadcast along axis=0 (match index labels):
df.sub(df['d'], axis=0)    # subtract column 'd' from every column
```
