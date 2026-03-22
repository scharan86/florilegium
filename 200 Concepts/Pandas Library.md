---
tags:
  - cs/lang/python
created: 2026-03-18
status: draft
type: concept
---
---

>[!Definition]
>

## Components
1. [[Series]]
2. [[DataFrame]]
3. [[Function Application and Mapping]]
4. [[Sorting and Ranking in Pandas]]
5. [[Descriptive Statistics]]

## Concepts
### The fundamental design choice: labels over positions

The central idea in Pandas is that **data should be aligned by label, not by integer position**. Operations between two labeled objects automatically align on shared labels before computing. Labels in only one object produce `NaN`.

This prevents a whole class of bugs where data from different sources gets silently misaligned because rows happen to be in different orders. NumPy has no concept of labels and aligns everything by position only.

### Series is an ordered dict + array hybrid

A `Series` behaves like both a fixed-length ordered dict and a NumPy array simultaneously:

python

```python
s['label']   # dict-style: label lookup
s[0]         # array-style: positional lookup
s[1:3]       # array-style: positional slice — end EXCLUSIVE
s['b':'d']   # label slice — end INCLUSIVE
```

The end-inclusive behavior of label slices is deliberate — when you write `s['b':'d']`, you almost certainly want the row labeled `'d'` included.

### DataFrame is a dict of Series sharing an index

Internally a DataFrame stores columns as a dict of Series all sharing the same row index. This means:

- Each column can have a different dtype — unlike NumPy's homogeneous ndarray.
- `df['col']` is O(1) column lookup.
- The underlying storage groups same-dtype columns into NumPy arrays (called "blocks"), rather than one single 2D array.

---

### Alignment and the NaN contract

Whenever two labeled objects interact, Pandas computes the **union of their labels** and aligns both inputs to it. Any position missing a value in one input becomes `NaN`. This is explicit and predictable — no silent data corruption.

python

```python
s1 = pd.Series([1, 2, 3], index=['a', 'b', 'c'])
s2 = pd.Series([10, 20],  index=['b', 'd'])
s1 + s2
# a     NaN    <- 'a' only in s1
# b    12.0    <- both have 'b'
# c     NaN    <- 'c' only in s1
# d     NaN    <- 'd' only in s2
```

Use `fill_value` to substitute a number instead: `s1.add(s2, fill_value=0)`.

---

### Index objects are immutable and shareable

`Index` objects cannot be modified element-by-element — `df.index[0] = 'new'` raises a `TypeError`. This allows the same Index object to be safely shared across multiple DataFrames with zero copy overhead.

To change labels: use `df.index = new_list` (replaces the whole index) or `df.rename(index=mapping)` for specific labels.

---

### `reindex` vs direct index assignment

||`s.reindex(new_labels)`|`df.index = new_labels`|
|---|---|---|
|What it does|Rearranges/extends data to match new labels|Replaces labels without moving data|
|Missing labels|Filled with NaN (or fill_value)|Must be same length — no fill|
|Use when|You want to add, remove, or reorder labels with data alignment|Your labels are simply wrong but data order is correct|

---

### `loc` vs `iloc`

||`.loc`|`.iloc`|
|---|---|---|
|Indexing by|Label|Integer position|
|Slice end|**Inclusive**|**Exclusive** (Python convention)|
|Out-of-bounds|`KeyError`|`IndexError`|

python

```python
df.loc['a':'c']    # rows a, b, c — 'c' included
df.iloc[0:3]       # rows at positions 0, 1, 2 — position 3 excluded
```

---

### `apply` vs `applymap` / `map`

|Method|Applied to|Function receives|Use for|
|---|---|---|---|
|`df.apply(f, axis=0)`|Each column|A Series|Column-level aggregations|
|`df.apply(f, axis=1)`|Each row|A Series|Row-level aggregations|
|`df.map(f)` / `df.applymap(f)`|Each element|A scalar|Element-wise transformations|
|`s.apply(f)`|Each element|A scalar|Element-wise on a Series|
|`s.map(f_or_dict)`|Each element|A scalar|Lookup/substitution via dict|

`apply` is row/column-level (function gets a full Series). `map`/`applymap` is truly scalar-level (function gets one value at a time).

---

### Pandas `ddof=1` vs NumPy `ddof=0`

Pandas `std` and `var` default to **ddof=1** (sample statistics). NumPy defaults to **ddof=0** (population statistics). They give different results on the same data:

python

```python
s = pd.Series([2., 4., 6.])
s.std()                   # 2.0     — ddof=1 (pandas default)
np.std(s.values)          # 1.633   — ddof=0 (numpy default)
np.std(s.values, ddof=1)  # 2.0     — matches pandas
```

---

### Missing data: `NaN` vs `None`

Pandas uses `np.nan` (a float) to represent missing values in numeric columns, and may use `None` for object dtype. Both are caught by `isnull()` / `notnull()`:

python

```python
pd.isnull(np.nan)   # True
pd.isnull(None)     # True
pd.notnull(np.nan)  # False
```

Never use `== np.nan` or `== None` to test for missing values — always use `isnull()` / `notnull()` (or their aliases `isna()` / `notna()`).

### `value_counts` sort order

`s.value_counts()` returns counts sorted **descending** (most frequent first) by default — unlike `np.unique` which returns in sorted value order. Pass `sort=False` to preserve order of first appearance instead.