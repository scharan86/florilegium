---
tags:
  - cs/lang/python
created: 2026-03-18
status: draft
type: concept
aliases:
  - numpy
---
---

>[!Definition]
>
>NumPy (Numerical Python) is a Python library whose core is implemented in C. When you call `np.sqrt(arr)`, you are not running a Python loop — you are calling a compiled C function that iterates over a block of raw memory at native speed. Python is only involved in dispatching the call.
>
>This is the fundamental reason NumPy exists: Python's interpreter overhead per operation is expensive. For a million-element array, a Python `for` loop calls the interpreter a million times. A NumPy ufunc calls C once.

## Functions
1. [[Array Creation and Attributes]]
2. [[Datatype Stuff]]
3. [[Reshaping and Transposing]]
4. [[Indexing and Slicing]]
5. [[Math Functions in Python]]
6. [[Boolean Array Methods]]
7. [[Sorting in NumPy]]
8. [[Random Number Generation]]
9. [[NumPy Universal Functions]]

>[!note]
> `axis` refers to the **direction of operation**.
>- `axis = 0`  collapse rows or move vertically (top to bottom)
>- `axis = 1` collapse columns or move horizontally (left to right)
## Core Concepts
### The ndarray memory model

An ndarray is not a Python list of Python objects. It is a thin Python wrapper around a **contiguous block of raw memory** — a single flat buffer of bytes. All elements are the same fixed-size type (the dtype), stored back-to-back with no Python object overhead between them.

Three metadata fields describe how to interpret that buffer:

|Field|What it means|Example|
|---|---|---|
|`shape`|Logical dimensions|`(3, 4)`|
|`dtype`|Type and size of each element|`float64` = 8 bytes per element|
|`strides`|Bytes to step per dimension to reach the next element|`(32, 8)` — 32 bytes to step one row, 8 bytes one col|

Strides are what make reshape, transpose, and slicing essentially free — they just change the metadata, not the underlying buffer.


```python
arr = np.arange(12, dtype=np.float64).reshape((3, 4))
arr.strides    # (32, 8)
               # 4 columns × 8 bytes/element = 32 bytes to skip one row
               # 1 element  × 8 bytes/element = 8 bytes to skip one column
```

### Views vs copies — the most important practical distinction

**Slicing always returns a view.** The slice shares memory with the original array.

python

```python
arr = np.arange(10)
s = arr[5:8]
s[:] = 99       # modifies arr too — they share the same buffer
print(arr)      # [ 0  1  2  3  4 99 99 99  8  9]
```

**Fancy indexing always returns a copy.** Indexing with an integer array or boolean array cannot share memory (the selected elements may not be contiguous), so NumPy allocates a new buffer.

| Indexing type      | Returns        | Mutating the result affects original? |
| ------------------ | -------------- | ------------------------------------- |
| `arr[2:5]`         | View           | Yes                                   |
| `arr[[0, 2, 4]]`   | Copy           | No                                    |
| `arr[arr > 0]`     | Copy           | No                                    |
| `arr.T`            | View           | Yes                                   |
| `arr.reshape(...)` | View (usually) | Yes                                   |
| `arr.copy()`       | Copy           | No                                    |

```python
arr[[1, 3, 5]]        # copy — new array
arr[arr > 0]          # copy — new array
arr[1:4]              # view — same buffer
arr[1:4].copy()       # explicitly force a copy from a slice
```

### Homogeneity and dtype upcasting

All elements in an ndarray must be the **same type**. If you pass a mixed list, NumPy upcasts to the most general type that can represent all values:

```python
np.array([1, 2, 3])          # int64
np.array([1, 2.0, 3])        # float64  — int upcasted because of 2.0
np.array([1, 2, 'three'])    # <U21     — everything becomes a Unicode string
```

The dtype hierarchy for upcasting (roughly): `bool` → `int` → `float` → `complex` → `str`.

This is different from a Python list, which happily stores mixed types with no conversion.

### Vectorization and why it matters

**Vectorization** means expressing operations on whole arrays rather than writing explicit loops. It is not just a style preference — it is a performance contract.

```python
# Python loop: interpreter overhead on every iteration
result = [x * 2 for x in data]

# Vectorized: one C function call, no Python per element
result = data * 2
```

For a 10-million-element array, the vectorized version is typically 10–100× faster. The gains come from:

1. No Python interpreter overhead per element
2. CPU cache efficiency — contiguous memory is prefetched efficiently
3. SIMD instructions — modern CPUs can process multiple elements per clock cycle using vectorized hardware instructions

### Broadcasting

Broadcasting is the rule NumPy uses to perform arithmetic between arrays of **different but compatible shapes**, without allocating extra memory.

**The rule:** Two dimensions are compatible if they are equal, or if one of them is 1. Dimensions are compared **trailing-first** (right to left).

```python
arr  = np.ones((3, 4))              # shape (3, 4)
row  = np.array([1, 2, 3, 4])       # shape    (4,) — treated as (1,4), broadcast to (3,4)
col  = np.array([[1], [2], [3]])    # shape (3, 1)  — broadcast to (3,4)

arr + row    # adds row to each of the 3 rows
arr + col    # adds col to each of the 4 columns

np.ones((3, 4)) + np.ones((3, 3))   # ValueError — 4 and 3 are incompatible
```

Broadcasting never actually copies the data to fill the shape — it is a virtual expansion. The memory footprint stays the same.

### `np.array` vs `np.asarray`

||`np.array(x)`|`np.asarray(x)`|
|-----------------------------|--------------------|---------------------------------------------------------------|
|Input is a list|allocates new array|allocates new array|
|Input is already an ndarray|**copies by default**|**no copy** — returns input as-is|
|Use case|when you want isolation from the original|when you want zero-copy passthrough|

`np.asarray` is the idiomatic choice inside functions that accept array-like input and just need to ensure they have an ndarray to work with.

---

### Contiguous memory: C-order vs Fortran-order

NumPy distinguishes between **C-contiguous** (row-major) and **Fortran-contiguous** (column-major) layouts.

|Layout|Also called|Adjacent in memory|Default for|
|---|---|---|---|
|C-contiguous|row-major|elements in the **last** axis|`np.array`, most NumPy ops|
|Fortran-contiguous|column-major|elements in the **first** axis|some `linalg` routines, MATLAB interop|

After `.T`, the array is typically no longer C-contiguous — strides are reordered but memory is not moved:

python

```python
arr = np.zeros((3, 4))
arr.flags['C_CONTIGUOUS']    # True
arr.T.flags['C_CONTIGUOUS']  # False — memory layout unchanged, only strides flipped

np.ascontiguousarray(arr.T)  # force a C-contiguous copy when needed
```

This matters when interfacing with C extensions, Cython, or numba — they often require C-contiguous input.

---

### NaN semantics

`NaN` (Not a Number) is a special float64 value. It propagates through all arithmetic, and critically, **it is not equal to itself** (IEEE 754 rule):

python

```python
np.nan + 1          # nan
np.nan == np.nan    # False  — never use == to check for NaN
np.isnan(np.nan)    # True   — correct way to check
```

Statistical methods propagate NaN by default. NaN-safe variants skip NaN values:

|Standard|NaN-safe equivalent|Behavior difference|
|---|---|---|
|`np.sum(arr)`|`np.nansum(arr)`|treats NaN as 0|
|`np.mean(arr)`|`np.nanmean(arr)`|excludes NaN from count|
|`np.min(arr)` / `np.max(arr)`|`np.nanmin(arr)` / `np.nanmax(arr)`|ignores NaN|
|`np.std(arr)`|`np.nanstd(arr)`|excludes NaN|

python

```python
a = np.array([1., 2., np.nan, 4.])
a.mean()          # nan   — propagated
np.nanmean(a)     # 2.333 — NaN excluded
```

### Integer vs float division

NumPy respects dtype when dividing:

python

```python
np.array([1, 2, 3]) / 2           # float64: [0.5, 1.0, 1.5]
np.array([1, 2, 3]) // 2          # int64:   [0, 1, 1]  (floor division)
np.array([1, 2, 3]) / 2.0         # float64: [0.5, 1.0, 1.5]  — float operand forces float result
np.array([1, 2, 3], dtype=float) / 2   # float64: same
```

When mixing integer arrays with division, be explicit about the intended dtype to avoid silent truncation.

---

### Why `astype` always copies

Unlike Python casts which may reuse memory, `arr.astype(new_dtype)` **always allocates a new array**, even if the dtype is already the target:

python

```python
arr = np.array([1, 2, 3], dtype=np.float64)
arr2 = arr.astype(np.float64)   # new array — even though dtype didn't change
arr2 is arr                      # False

# To avoid the copy when dtype already matches:
np.asarray(arr, dtype=np.float64)   # returns arr unchanged if dtype already matches
```


1. [[Array Creation and Attributes]]
2. [[Datatype Stuff]]
3. [[Reshaping and Transposing]]
4. [[Indexing and Slicing]]
5. [[Math Functions in Python]]
6. [[Boolean Array Methods]]
7. [[Sorting in NumPy]]
8. [[Random Number Generation]]



## Related Concepts
