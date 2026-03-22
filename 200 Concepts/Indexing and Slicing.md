---
tags:
  - cs/lang/python
created: 2026-03-18
status: draft
type: concept
---
---
## Basic Indexing and Slicing

| Operation                        | Description                                                 | Example                                     |
| -------------------------------- | ----------------------------------------------------------- | ------------------------------------------- |
| `arr[i]`                         | Element at index i (1D); returns a row array for 2D         | `arr[5]` → scalar `5`                       |
| `arr[i, j]`                      | Element at row i, col j — equivalent to `arr[i][j]`         | `arr[0, 2]` → element at row 0, col 2       |
| `arr[start:stop]`                | Slice — returns a **view**, mutations propagate to original | `arr[5:8]` → `array([5, 6, 7])`             |
| `arr[start:stop] = val`          | Assign scalar or array to a slice in-place                  | `arr[5:8] = 12` → positions 5,6,7 become 12 |
| `arr[:]` or `arr_slice[:] = val` | Bare slice — every element of the slice                     | `arr[:] = 0` → zero out entire array        |
| `arr[-1]`                        | Last element; negative indices count from end               | `arr[-1]` → last element                    |
| `arr[::2]`                       | Every second element (step slicing)                         | `arr[::2]` on `[0..9]` → `[0,2,4,6,8]`      |
| `arr2d[:2]`                      | First 2 rows of a 2D array                                  | `arr2d[:2]` → 2×n sub-array                 |
| `arr2d[:2, 1:]`                  | First 2 rows, columns from index 1 onward                   | `arr2d[:2, 1:]` → 2×(n-1) sub-array         |
| `arr3d[0]`                       | First 2D sub-array from a 3D array                          | `arr3d[0]` on shape (2,2,3) → shape (2,3)   |
| `arr.copy()`                     | Explicitly force a copy of an array or slice                | `arr[5:8].copy()` → independent copy        |

> **Key difference from Python lists:** NumPy slices are **views**, not copies. Changes to a slice modify the original array.

## Boolean Indexing

|Operation|Description|Example|
|---|---|---|
|`arr > val`|Element-wise comparison — returns boolean array|`arr > 0` → `array([False, True, True, ...])`|
|`arr[bool_arr]`|Select elements/rows where condition is True — returns a **copy**|`arr[arr > 0]` → all positive elements|
|`data[names == 'Bob']`|Use boolean array to select rows of another same-length array|`data[names == 'Bob']` → rows matching 'Bob'|
|`~condition`|Negate a boolean array|`data[~(names == 'Bob')]` → rows not 'Bob'|
|`(cond1) & (cond2)`|Element-wise AND — use `&`, not `and`|`data[(names == 'Bob') & (data[:, 0] > 0)]`|
|`(cond1) \| (cond2)`|Element-wise OR — use `\|`, not `or`|`data[(names == 'Bob') \| (names == 'Will')]`|

python

```python
names = np.array(['Bob', 'Joe', 'Will', 'Bob'])
data  = np.random.randn(4, 4)
data[names == 'Bob']          # rows 0 and 3
data[names != 'Bob']          # rows 1 and 2
data[data < 0] = 0            # zero out all negatives in-place
```

---

## Fancy Indexing

| Operation         | Description                                               | Example                                                  |
| ----------------- | --------------------------------------------------------- | -------------------------------------------------------- |
| `arr[[i, j, k]]`  | Select rows in a specific order — returns a **copy**      | `arr[[4, 3, 0]]` → rows 4, 3, 0 in that order            |
| `arr[[-1, -2]]`   | Negative indices select rows from the end                 | `arr[[-1, -2]]` → last two rows, reversed                |
| `arr[rows, cols]` | Select individual elements by paired row/col index arrays | `arr[[0,1,2], [0,1,0]]` → `arr[0,0], arr[1,1], arr[2,0]` |

```python
arr = np.empty((8, 4))
for i in range(8):
    arr[i] = i

arr[[4, 3, 0, 6]]                  # rows in custom order
arr[[-3, -5, -7]]                  # rows 5, 3, 1 from end
arr[[1, 5, 7, 2], [0, 3, 1, 2]]   # four specific (row, col) pairs
```

> **Fancy indexing always returns a copy** — unlike slicing. The selected elements may not be contiguous in memory so NumPy must allocate a new buffer.



