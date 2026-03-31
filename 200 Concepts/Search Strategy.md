---
tags:
  - cs/ai/gofai
created: 2026-03-12
status: draft
type: concept
---
---
> [!definition]
> *Search strategy* is a general rule that determines which node from the frontier should be expanded next during search. 
> ==*Frontier* refers to the set of nodes that have been generated (discovered and stored) but haven't been expanded (successors haven't been explored).==

- We use "haven't been expanded" instead of explored because the children haven't been generated yet.
- It defines the behavior of a search.
- Search strategies are principles, not procedures.
*All search strategies are distinguished by the order in which the nodes are expanded.*
## Types
1. [[Uninformed Search]]
2. [[Heuristic Search|Heuristic Search]]

## Questions

## Reflection 
It's a plan that decides how the state space graph is to be explored. 