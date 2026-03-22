---
tags:
  - cs/lang/python
created: 2026-03-18
status: draft
type: concept
---
---
## Reshaping and Transposing

| Operation                   | Description                                            | Example                                                      |
| --------------------------- | ------------------------------------------------------ | ------------------------------------------------------------ |
| `arr.reshape(shape)`        | Return view with new shape — total elements must match | `np.arange(12).reshape((3, 4))` → 3×4 array                  |
| `arr.ravel()`               | Return flattened 1D view (C-order by default)          | `arr.ravel()` → 1D array, usually a view                     |
| `arr.flatten()`             | Return flattened 1D **copy**                           | `arr.flatten()` → always a new array                         |
| `arr.T`                     | Transpose — returns a view, no data copied             | `arr.T` on shape (3,4) → shape (4,3)                         |
| `arr.transpose(axes)`       | Permute axes by tuple — generalization of `.T`         | `arr.transpose((1, 0, 2))` on (2,2,4) → swaps first two axes |
| `np.expand_dims(arr, axis)` | Insert a new axis of length 1 at given position        | `np.expand_dims(arr, 0)` on shape (3,) → (1,3)               |
| `np.squeeze(arr)`           | Remove all axes of length 1                            | `np.squeeze(arr)` on shape (1,3,1) → (3,)                    |
