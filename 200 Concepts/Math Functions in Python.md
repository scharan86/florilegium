---
tags:
  - cs/lang/python
created: 2026-03-18
status: draft
type: concept
---
---


## Vectorized Arithmetic

All arithmetic between equal-size arrays is element-wise. Scalar operations broadcast to every element.

|Expression|Description|Example|
|---|---|---|
|`a + b`|Element-wise addition|`arr + arr` → each element doubled|
|`a - b`|Element-wise subtraction|`arr - arr` → all zeros|
|`a * b`|Element-wise multiplication|`arr * arr` → element-wise square|
|`a / b`|Element-wise division|`1 / arr` → reciprocal of each element|
|`a ** n`|Element-wise power|`arr ** 0.5` → element-wise square root|
|`scalar op arr`|Scalar propagates to every element|`arr * 10`, `arr + 5`, `2 ** arr`|
|`np.dot(A, B)`|Matrix multiplication (inner product)|`np.dot(arr.T, arr)` → AᵀA|

---

## Unary Universal Functions (ufuncs)

Functions that operate element-wise on a single array.

| Function                             | Description                                               | Example                                             |
| ------------------------------------ | --------------------------------------------------------- | --------------------------------------------------- |
| `np.abs(arr)` / `np.fabs(arr)`       | Absolute value; `fabs` skips complex overhead             | `np.abs([-1, 2, -3])` → `[1, 2, 3]`                 |
| `np.sqrt(arr)`                       | Square root — equivalent to `arr ** 0.5`                  | `np.sqrt([4., 9.])` → `[2., 3.]`                    |
| `np.square(arr)`                     | Square of each element — equivalent to `arr ** 2`         | `np.square([2., 3.])` → `[4., 9.]`                  |
| `np.exp(arr)`                        | eˣ for each element                                       | `np.exp([0, 1])` → `[1., 2.718]`                    |
| `np.log(arr)`                        | Natural log (base e)                                      | `np.log([1, np.e])` → `[0., 1.]`                    |
| `np.log10(arr)`                      | Log base 10                                               | `np.log10([1, 100])` → `[0., 2.]`                   |
| `np.log2(arr)`                       | Log base 2                                                | `np.log2([1, 8])` → `[0., 3.]`                      |
| `np.log1p(arr)`                      | log(1 + x) — numerically stable for small x               | `np.log1p(0)` → `0.0`                               |
| `np.sign(arr)`                       | 1 (positive), 0 (zero), −1 (negative)                     | `np.sign([-3, 0, 5])` → `[-1, 0, 1]`                |
| `np.ceil(arr)`                       | Smallest integer ≥ element                                | `np.ceil([1.2, 2.9])` → `[2., 3.]`                  |
| `np.floor(arr)`                      | Largest integer ≤ element                                 | `np.floor([1.7, 2.1])` → `[1., 2.]`                 |
| `np.rint(arr)`                       | Round to nearest integer, preserving dtype                | `np.rint([1.5, 2.5])` → `[2., 2.]`                  |
| `np.modf(arr)`                       | Return `(fractional_parts, integral_parts)` as two arrays | `np.modf([3.7, -1.2])` → `([0.7, -0.2], [3., -1.])` |
| `np.isnan(arr)`                      | True where element is NaN                                 | `np.isnan([1, np.nan])` → `[False, True]`           |
| `np.isfinite(arr)`                   | True where element is finite (not inf, not NaN)           | `np.isfinite([1, np.inf, np.nan])` → `[T, F, F]`    |
| `np.isinf(arr)`                      | True where element is ±inf                                | `np.isinf([1, np.inf])` → `[False, True]`           |
| `np.cos(arr)` / `np.cosh(arr)`       | Cosine / hyperbolic cosine                                | `np.cos([0, np.pi])` → `[1., -1.]`                  |
| `np.sin(arr)` / `np.sinh(arr)`       | Sine / hyperbolic sine                                    | `np.sin([0, np.pi/2])` → `[0., 1.]`                 |
| `np.tan(arr)` / `np.tanh(arr)`       | Tangent / hyperbolic tangent                              | `np.tanh([0., 1.])` → `[0., 0.762]`                 |
| `np.arccos(arr)` / `np.arccosh(arr)` | Inverse cosine / hyperbolic inverse                       | `np.arccos([1., 0.])` → `[0., π/2]`                 |
| `np.arcsin(arr)` / `np.arcsinh(arr)` | Inverse sine / hyperbolic inverse                         | `np.arcsin([0., 1.])` → `[0., π/2]`                 |
| `np.arctan(arr)` / `np.arctanh(arr)` | Inverse tangent / hyperbolic inverse                      | `np.arctan([0., 1.])` → `[0., π/4]`                 |
| `np.logical_not(arr)`                | Element-wise NOT — equivalent to `~arr`                   | `np.logical_not([True, False])` → `[False, True]`   |

---

## Binary Universal Functions (ufuncs)

Functions that operate element-wise on two arrays.

| Function                 | Description                         | Example                                            |
| ------------------------ | ----------------------------------- | -------------------------------------------------- |
| `np.add(x, y)`           | Add corresponding elements          | `np.add([1,2], [3,4])` → `[4, 6]`                  |
| `np.subtract(x, y)`      | Subtract y from x element-wise      | `np.subtract([5,6], [1,2])` → `[4, 4]`             |
| `np.multiply(x, y)`      | Multiply element-wise               | `np.multiply([2,3], [4,5])` → `[8, 15]`            |
| `np.divide(x, y)`        | Divide element-wise                 | `np.divide([6,8], [2,4])` → `[3., 2.]`             |
| `np.floor_divide(x, y)`  | Floor division — truncate remainder | `np.floor_divide([7,9], [2,4])` → `[3, 2]`         |
| `np.power(x, y)`         | Raise elements of x to powers in y  | `np.power([2,3], [3,2])` → `[8, 9]`                |
| `np.maximum(x, y)`       | Element-wise maximum                | `np.maximum([1,5], [3,2])` → `[3, 5]`              |
| `np.fmax(x, y)`          | Element-wise maximum, ignoring NaN  | `np.fmax([np.nan,5], [3,2])` → `[3., 5.]`          |
| `np.minimum(x, y)`       | Element-wise minimum                | `np.minimum([1,5], [3,2])` → `[1, 2]`              |
| `np.fmin(x, y)`          | Element-wise minimum, ignoring NaN  | `np.fmin([np.nan,5], [3,2])` → `[3., 2.]`          |
| `np.mod(x, y)`           | Element-wise modulus (remainder)    | `np.mod([7,9], [3,4])` → `[1, 1]`                  |
| `np.copysign(x, y)`      | Copy sign of y onto magnitudes of x | `np.copysign([3,-3], [-1,1])` → `[-3., 3.]`        |
| `np.greater(x, y)`       | Element-wise `x > y`                | `np.greater([3,1], [2,2])` → `[True, False]`       |
| `np.greater_equal(x, y)` | Element-wise `x >= y`               | `np.greater_equal([2,2], [2,3])` → `[True, False]` |
| `np.less(x, y)`          | Element-wise `x < y`                | `np.less([1,3], [2,2])` → `[True, False]`          |
| `np.less_equal(x, y)`    | Element-wise `x <= y`               | `np.less_equal([2,3], [2,2])` → `[True, False]`    |
| `np.equal(x, y)`         | Element-wise `x == y`               | `np.equal([1,2], [1,3])` → `[True, False]`         |
| `np.not_equal(x, y)`     | Element-wise `x != y`               | `np.not_equal([1,2], [1,3])` → `[False, True]`     |
| `np.logical_and(x, y)`   | Element-wise logical AND            | `np.logical_and([T,T], [T,F])` → `[T, F]`          |
| `np.logical_or(x, y)`    | Element-wise logical OR             | `np.logical_or([T,F], [F,F])` → `[T, F]`           |
| `np.logical_xor(x, y)`   | Element-wise logical XOR            | `np.logical_xor([T,F], [T,T])` → `[F, T]`          |

## Conditional Logic as Array Operations

|Function|Description|Example|
|---|---|---|
|`np.where(cond, x, y)`|Vectorized ternary — return `x` where `cond` is True, else `y`; `x` and `y` can be arrays or scalars|`np.where(arr > 0, 2, -2)` → `+2` for positives, `-2` for negatives|

python

```python
arr = np.random.randn(4, 4)

np.where(arr > 0, 2, -2)        # replace all values with +2 or -2 based on sign
np.where(arr > 0, arr, 0)       # keep positives, zero out negatives (ReLU)
np.where(arr > 0, arr, -arr)    # element-wise absolute value
np.where(np.isnan(arr), 0, arr) # replace NaN with 0
```

---

## Mathematical and Statistical Methods

All methods accept an optional `axis` argument. Without it, the statistic is computed over the entire array. `axis=0` reduces along rows (per column); `axis=1` reduces along columns (per row).

|Method|Description|Example|
|---|---|---|
|`arr.sum(axis=None)` / `np.sum(arr)`|Sum of all elements; zero-length → 0|`arr.sum(axis=0)` → column sums|
|`arr.mean(axis=None)` / `np.mean(arr)`|Arithmetic mean; zero-length → NaN|`arr.mean(axis=1)` → one mean per row|
|`arr.std(axis=None, ddof=0)`|Standard deviation (default denominator n)|`arr.std()` → scalar|
|`arr.var(axis=None, ddof=0)`|Variance (default denominator n)|`arr.var(axis=0)` → per-column variance|
|`arr.min(axis=None)`|Minimum element|`arr.min()` → global min|
|`arr.max(axis=None)`|Maximum element|`arr.max(axis=1)` → max of each row|
|`arr.argmin(axis=None)`|Index of minimum element (flat or along axis)|`arr.argmin()` → flat index of min|
|`arr.argmax(axis=None)`|Index of maximum element (flat or along axis)|`arr.argmax(axis=0)` → row index of max per column|
|`arr.cumsum(axis=None)`|Cumulative sum; without axis operates on flattened|`arr.cumsum(axis=0)` → running total down each column|
|`arr.cumprod(axis=None)`|Cumulative product; without axis operates on flattened|`arr.cumprod(axis=1)` → running product across each row|

python

```python
arr = np.array([[0, 1, 2],
                [3, 4, 5],
                [6, 7, 8]])

arr.sum()           # 36
arr.mean()          # 4.0
arr.sum(axis=0)     # array([ 9, 12, 15])  — sum each column
arr.sum(axis=1)     # array([ 3, 12, 21])  — sum each row
arr.cumsum(axis=0)  # array([[ 0,  1,  2], [ 3,  5,  7], [ 9, 12, 15]])
arr.cumprod(axis=1) # array([[  0,  0,  0], [  3, 12, 60], [  6, 42,336]])
```

## Unique and Set Logic

|Function|Description|Example|
|---|---|---|
|`np.unique(x)`|Sorted, deduplicated elements|`np.unique([3,1,2,1])` → `array([1, 2, 3])`|
|`np.intersect1d(x, y)`|Sorted common elements in x and y|`np.intersect1d([1,2,3],[2,3,4])` → `[2, 3]`|
|`np.union1d(x, y)`|Sorted union of all elements|`np.union1d([1,2],[2,3])` → `[1, 2, 3]`|
|`np.in1d(x, y)`|Boolean array — is each element of x in y?|`np.in1d([1,5,3],[1,3])` → `[True, False, True]`|
|`np.setdiff1d(x, y)`|Elements in x that are not in y|`np.setdiff1d([1,2,3],[2])` → `[1, 3]`|
|`np.setxor1d(x, y)`|Elements in either array but not both|`np.setxor1d([1,2,3],[2,3,4])` → `[1, 4]`|

---

## Linear Algebra (`numpy.linalg`)

| Function                               | Description                                                           | Example                                                |
| -------------------------------------- | --------------------------------------------------------------------- | ------------------------------------------------------ |
| `np.dot(A, B)`                         | Matrix multiplication                                                 | `np.dot(arr.T, arr)` → AᵀA                             |
| `np.linalg.diag(v)`                    | Extract diagonal from 2D matrix → 1D; or convert 1D → diagonal matrix | `np.linalg.diag(mat)` → `[m00, m11, m22]`              |
| `np.linalg.trace(A)`                   | Sum of diagonal elements                                              | `np.linalg.trace(mat)` → scalar                        |
| `np.linalg.det(A)`                     | Matrix determinant                                                    | `np.linalg.det(mat)` → scalar                          |
| `np.linalg.eig(A)`                     | Eigenvalues and eigenvectors of a square matrix                       | `vals, vecs = np.linalg.eig(mat)`                      |
| `np.linalg.inv(A)`                     | Inverse of a square matrix                                            | `np.linalg.inv(mat)` → A⁻¹                             |
| `np.linalg.pinv(A)`                    | Moore-Penrose pseudo-inverse — works for non-square                   | `np.linalg.pinv(mat)`                                  |
| `np.linalg.qr(A)`                      | QR decomposition                                                      | `Q, R = np.linalg.qr(mat)`                             |
| `np.linalg.svd(A, full_matrices=True)` | Singular value decomposition                                          | `U, S, Vt = np.linalg.svd(mat)`                        |
| `np.linalg.solve(A, b)`                | Solve Ax = b; A must be square and full rank                          | `x = np.linalg.solve(A, b)`                            |
| `np.linalg.lstsq(A, b, rcond=None)`    | Least-squares solution to Ax = b                                      | `x, res, rank, sv = np.linalg.lstsq(A, b, rcond=None)` |