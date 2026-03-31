---
tags:
  - cs/ai/gofai
created: 2026-03-12
status: draft
type: concept
aliases:
  - Directed Search Control Strategy
  - Informed Search
  - Directed Search
---
---
>[!definition]
> *Informed search* is a class of search strategies uses additional information beyond the problem definition to find solutions more efficiently.

- The knowledge is encoded in a **[[Heuristic|heuristic function]]** $h(n)$ where:
$$ h(n) = estimated \ cost \ of \  the \ cheapest \ path \ from \ the \ state \ at \ node \ n \ to \ a \ goal \ state
 $$
- The algorithm doesn't know the true cost, only an estimate calculated using domain-specific knowledge.
- The quality of the estimate determines how efficient the search is.
- Node is selected based on an *evaluation function* $f(n)$ , which is construed as a cost estimate. 
- Most informed search algorithms include $h(n)$ as a component of $f(n)$.

>[!question] How's it better than uninformed search? 
>Uninformed search expands nodes based purely on structure, whereas, informed search uses $h(n)$ to prioritize promising nodes.

## Algorithms
1. [[Greedy Best First Search]]
2. [[Generate and Test Search|Heuristic-Assisted Generate and Test Search]]
3. [[Hill Climbing]]
4. [[Simulated Annealing]]
5. [[Local Beam Search]]
6. [[A* Algorithm]]
7. [[Problem Reduction]]
8. [[AND-OR Search]]
9. [[Constraint Search]]
10. [[Means-end Analysis]]
11. [[Ant Colony Optimization]]
12. [[Genetic Algorithms]]

## Questions

## Reflection 
