---
tags:
  - cs
created: 2026-03-14
status: stable
type: concept
aliases:
  - nominal data
---
---

>[!Definition]
> *Nominal data* is *purely categorical* in nature.
## Intuition
It is a type of [[Qualitative Data|qualitative data]], where categorical labels don't have any order and the categories encode the meaning.

- If numbers are used, then they are only for labels with no quantitative meaning.
- Originates from the Latin word *nomen* — name.
- In [[ML]], nominal data is [[One-hot Encoding|one-hot encoded]]
## Properties
1. Categories are mutually exclusive.
2. There is no natural order between categories.
3. Arithmetic is completely meaningless.

>[!example]
>Disease Classes: CNV, DME, DRUSEN, Normal
>Blood Type: O, A, B, AB, etc
