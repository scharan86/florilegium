---
tags:
  - cs/lang/python
created: 2026-03-18
status: draft
type: concept
---
## Random Number Generation (`numpy.random`)

| Function                                       | Description                                          | Example                                                  |
| ---------------------------------------------- | ---------------------------------------------------- | -------------------------------------------------------- |
| `np.random.randn(d0, d1, ...)`                 | Samples from standard normal distribution (μ=0, σ=1) | `np.random.randn(3, 4)` → 3×4 float array                |
| `np.random.rand(d0, d1, ...)`                  | Uniform samples over [0, 1)                          | `np.random.rand(5)` → 5 values in [0,1)                  |
| `np.random.randint(low, high, size=None)`      | Random integers from `[low, high)`                   | `np.random.randint(0, 10, size=(3,))` → e.g. `[4, 7, 1]` |
| `np.random.normal(loc=0, scale=1, size=None)`  | Samples from N(loc, scale²)                          | `np.random.normal(5, 2, (2, 3))` → mean 5, std 2         |
| `np.random.uniform(low=0, high=1, size=None)`  | Samples from uniform [low, high)                     | `np.random.uniform(0, 5, 10)` → 10 values in [0,5)       |
| `np.random.seed(n)`                            | Set random seed for reproducibility                  | `np.random.seed(42)`                                     |
| `np.random.shuffle(arr)`                       | Shuffle array in-place along first axis              | `np.random.shuffle(arr)` → modifies arr, returns None    |
| `np.random.choice(a, size=None, replace=True)` | Random sample from 1D array                          | `np.random.choice([1,2,3,4], size=2)` → e.g. `[3, 1]`    |