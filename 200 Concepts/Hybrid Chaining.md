---
tags:
  - cs/ai/gofai
created: 2026-03-14
status: |
  stable
type: concept
aliases:
  - Integrated Reasoning
---
---
Modern expert systems use an [[Inference Engine|inference engine]] that switches between [[Forward Chaining|forward chaining]] and [[Backward Chaining|backward chaining]]  depending on the current goal or state of the data.

This is often referred as hybrid chaining or integrated reasoning.

>[!question] Why use both?
>Using only **forward chaining** can lead to "state space explosion," where the system derives thousands of useless facts that don't lead to a solution. Using only **backward chaining** can be inefficient if you don't have a clear goal in mind yet.