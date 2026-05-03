---
tags:
  - cs/lang/python
created: 2026-05-03
status: draft
type: concept
aliases:
  - ufuncs
  - Universal Functions
---
---

>[!Definition]
>`ufuncs` operate on `ndarrays` in an element-by-element fashion and is one of the core reasons behind NumPy's blazingly fast speed.
## Characteristics
1. [[Vectorization]]
2. [[Broadcasting]]
3. [[Type Dispatching]]

>[!note] Most mathematical operations in `NumPy` are `ufuncs` under the hood. 

| Ufunc            | Syntax                   | Description                                            |     |
| ---------------- | ------------------------ | ------------------------------------------------------ | --- |
| `np.add`         | `np.add(x1, x2)`         | Element-wise addition (`x1 + x2`).                     |     |
| `np.subtract`    | `np.subtract(x1, x2)`    | Element-wise subtraction (`x1 - x2`).                  |     |
| `np.multiply`    | `np.multiply(x1, x2)`    | Element-wise multiplication (`x1 * x2`).               |     |
| `np.divide`      | `np.divide(x1, x2)`      | Element-wise division (`x1 / x2`).                     |     |
| `np.power`       | `np.power(x1, x2)`       | Raise elements of `x1` to powers in `x2` (`x1 ** x2`). |     |
| `np.mod`         | `np.mod(x1, x2)`         | Element-wise remainder of division (`x1 % x2`).        |     |
| `np.sqrt`        | `np.sqrt(x)`             | Non-negative square root of each element.              |     |
| `np.exp`         | `np.exp(x)`              | Exponential (`e^x`) of each element.                   |     |
| `np.log`         | `np.log(x)`              | Natural logarithm (base `e`) of each element.          |     |
| `np.log10`       | `np.log10(x)`            | Base-10 logarithm of each element.                     |     |
| `np.sin`         | `np.sin(x)`              | Trigonometric sine (radians) of each element.          |     |
| `np.cos`         | `np.cos(x)`              | Trigonometric cosine (radians) of each element.        |     |
| `np.tan`         | `np.tan(x)`              | Trigonometric tangent (radians) of each element.       |     |
| `np.arcsin`      | `np.arcsin(x)`           | Inverse sine, returns in radians.                      |     |
| `np.arccos`      | `np.arccos(x)`           | Inverse cosine, returns in radians.                    |     |
| `np.arctan`      | `np.arctan(x)`           | Inverse tangent, returns in radians.                   |     |
| `np.greater`     | `np.greater(x1, x2)`     | Element-wise `x1 > x2`, returns Boolean array.         |     |
| `np.less`        | `np.less(x1, x2)`        | Element-wise `x1 < x2`, returns Boolean array.         |     |
| `np.equal`       | `np.equal(x1, x2)`       | Element-wise `x1 == x2`, returns Boolean array.        |     |
| `np.not_equal`   | `np.not_equal(x1, x2)`   | Element-wise `x1 != x2`, returns Boolean array.        |     |
| `np.logical_and` | `np.logical_and(x1, x2)` | Element-wise logical AND (`&`).                        |     |
| `np.logical_or`  | `np.logical_or(x1, x2)`  | Element-wise logical OR (`                             | `). |
| `np.logical_not` | `np.logical_not(x)`      | Element-wise logical NOT (`~`).                        |     |
| `np.maximum`     | `np.maximum(x1, x2)`     | Element-wise maximum of two arrays.                    |     |
| `np.minimum`     | `np.minimum(x1, x2)`     | Element-wise minimum of two arrays.                    |     |
| `np.absolute`    | `np.absolute(x)`         | Element-wise absolute value.                           |     |
| `np.negative`    | `np.negative(x)`         | Element-wise negative (`-x`).                          |     |
| `np.reciprocal`  | `np.reciprocal(x)`       | Element-wise reciprocal (`1/x`).                       |     |
| `np.sign`        | `np.sign(x)`             | Returns `-1, 0, 1` per element based on sign.          |     |
| `np.floor`       | `np.floor(x)`            | Largest integer ≤ each element (rounds down).          |     |
| `np.ceil`        | `np.ceil(x)`             | Smallest integer ≥ each element (rounds up).           |     |

These ufuncs work element-wise on NumPy arrays and support **broadcasting**, **type casting**, and **out‑of‑place** or **in‑place** operations.