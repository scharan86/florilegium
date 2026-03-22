---
tags:
  - cs/lang/python
created: 2026-03-18
status: draft
type: concept
---
---
## Array Creation Functions

| Function                                    | Description                                                                                              | Example                                                     |
| ------------------------------------------- | -------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------- |
| `np.array(data, dtype=None)`                | Convert input (list, tuple, array, or other sequence) to ndarray; infers dtype or accepts explicit dtype | `np.array([1, 2, 3])` → `array([1, 2, 3])`                  |
| `np.asarray(data, dtype=None)`              | Convert to ndarray, but does **not** copy if input is already an ndarray                                 | `np.asarray(existing_arr)` → same object, no copy           |
| `np.arange(start, stop, step)`              | Like `range` but returns an ndarray instead of a list                                                    | `np.arange(0, 10, 2)` → `array([0, 2, 4, 6, 8])`            |
| `np.zeros(shape, dtype=float)`              | Array of all 0s with given shape                                                                         | `np.zeros((2, 3))` → 2×3 array of 0.0                       |
| `np.zeros_like(arr)`                        | Array of 0s with same shape and dtype as `arr`                                                           | `np.zeros_like(arr)`                                        |
| `np.ones(shape, dtype=float)`               | Array of all 1s with given shape                                                                         | `np.ones((3,))` → `array([1., 1., 1.])`                     |
| `np.ones_like(arr)`                         | Array of 1s with same shape and dtype as `arr`                                                           | `np.ones_like(arr)`                                         |
| `np.empty(shape, dtype=float)`              | Allocate new array without initializing values (memory may contain garbage)                              | `np.empty((2, 2))` → uninitialized 2×2                      |
| `np.empty_like(arr)`                        | Allocate uninitialized array with same shape and dtype as `arr`                                          | `np.empty_like(arr)`                                        |
| `np.full(shape, fill_value, dtype=None)`    | Array of given shape with all values set to `fill_value`                                                 | `np.full((2, 3), 7)` → 2×3 array of 7                       |
| `np.full_like(arr, fill_value)`             | Filled array with same shape and dtype as `arr`                                                          | `np.full_like(arr, 0.5)`                                    |
| `np.eye(N, dtype=float)` / `np.identity(N)` | N×N identity matrix (1s on diagonal, 0s elsewhere)                                                       | `np.eye(3)` → 3×3 identity matrix                           |
| `np.linspace(start, stop, num)`             | `num` evenly spaced values over `[start, stop]` (inclusive)                                              | `np.linspace(0, 1, 5)` → `array([0., 0.25, 0.5, 0.75, 1.])` |
## Array Attributes
| Attribute     | Description                                               | Example                                           |
| ------------- | --------------------------------------------------------- | ------------------------------------------------- |
| `arr.shape`   | Tuple indicating the size of each dimension               | `arr.shape` → `(3, 4)`                            |
| `arr.ndim`    | Number of dimensions                                      | `arr.ndim` → `2`                                  |
| `arr.dtype`   | Data type of the array elements                           | `arr.dtype` → `dtype('float64')`                  |
| `arr.size`    | Total number of elements                                  | `arr.size` → `12` (for a 3×4 array)               |
| `arr.strides` | Bytes to step in each dimension to reach the next element | `arr.strides` → `(32, 8)` for float64 shape (3,4) |
| `arr.flags`   | Memory layout flags including C/Fortran contiguity        | `arr.flags['C_CONTIGUOUS']` → `True`              |