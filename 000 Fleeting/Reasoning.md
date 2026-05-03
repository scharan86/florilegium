---
tags: []
created: 2026-04-30
status: draft
type: concept
---
---

>[!Definition]
> Reasoning is the capability of a system to produce (generate) and use intermediate steps (structures) to **validly** transform inputs into outputs ==under constraints==. 
>
### Properties
1. Intermediate steps aren't generated arbitrarily, they're **constructed**. 
2. Validity of the structure is governed by rules ()
3. Reasoning is **flexible**, i.e. it contracts or expands depending on the task.
4. *[[Compositionality]] over steps*. (System derives the answer, not just recall).

## Components of Reason (ROCC)
1. **Representation**: Encodes the world ([[Symbolic Representation]], high-dimensional [[Vectors]] in modern systems)
2. **Operators**: Transformations applied on the representation to reach an outcome. In [[Neural Networks]], they are learned.
3. **Control (Search / Inference Strategy)**: describes the path from the possible transformations. 
4. **Constraints**: Defines what transformations or steps are valid. 

>[!note]
>If any one of these components are weak, reasoning degrades. 
## Keywords
1. Intermediate Structures
2. [[Compositionality]]
3. [[Constraints|constraint]]
## Summary

## Related Concepts
