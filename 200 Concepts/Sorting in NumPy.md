---
tags:
  - cs/lang
created: 2026-03-18
status: draft
type: concept
---
---
## Sorting

| Operation                  | Description                                         | Example                                            |
| -------------------------- | --------------------------------------------------- | -------------------------------------------------- |
| `arr.sort(axis=-1)`        | In-place sort along given axis (default: last axis) | `arr.sort()` → modifies arr directly, returns None |
| `np.sort(arr, axis=-1)`    | Return a sorted **copy** — original unchanged       | `np.sort(arr)` → new sorted array                  |
| `np.argsort(arr, axis=-1)` | Return integer indices that would sort the array    | `np.argsort([3,1,2])` → `[1, 2, 0]`                |

```python
arr = np.random.randn(6)
arr.sort()                  # in-place, ascending

arr2d = np.array([[3,1,2],[6,4,5]])
arr2d.sort(axis=0)          # sort each column independently
arr2d.sort(axis=1)          # sort each row independently

idx = np.argsort(arr)       # useful for reordering a paired array in the same or
```
