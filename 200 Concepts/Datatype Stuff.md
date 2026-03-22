---
tags:
  - cs/lang/python
created: 2026-03-18
status: draft
type: concept
---
---

### Common dtypes

|dtype|Aliases|Size|Notes|
|---|---|---|---|
|`np.bool_`|`bool`|1 byte|Element-wise boolean|
|`np.int32`|`i4`|4 bytes|Default int on some platforms|
|`np.int64`|`i8`|8 bytes|Default int on 64-bit Linux/macOS|
|`np.float32`|`f4`|4 bytes|Single precision; halves memory vs float64; standard in ML/GPU|
|`np.float64`|`f8`, `float`|8 bytes|Default float; double precision|
|`np.complex64`|`c8`|8 bytes|Two float32s|
|`np.complex128`|`c16`|16 bytes|Two float64s|
|`np.string_`|—|fixed|Fixed-width byte strings|
## `dtype` Casting

| Operation                | Description                                        |
| ------------------------ | -------------------------------------------------- |
| `arr.dtype`              | Inspect the data type of an array                  |
| `arr.astype(np.float64)` | Cast array to a new dtype (always creates a copy)  |
| `arr.astype(float)`      | Cast an array of numeric strings to floating-point |
