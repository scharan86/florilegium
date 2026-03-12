---
tags:
  - cs/ai/gofai
created: 2026-03-12
status: draft
type: concept
aliases:
  - British Museum Serach Algorithm
  - Heuristic-Assisted Generate and Test Search
  - Uninformed Generate and Test Search
---
---
>[!concept]  Generate and Test Search
>All the solutions are generated and tested for the best solution. It ensures that the best solution is checked against all possible generated solution.

> It is based on [[DFS]] with backtracking which guarantees to find a solution if done systematically and there exists one.
> 
- **Uninformed generate and test search** generates all the possible solutions to a problem blindly and tests them.
## Key Properties
1. It is essentially an exhaustive search in its simplest form.
2. The efficacy of this search primarily depends on the quality of the generator.
3. The tester is usually cheap and the generator is generally the bottleneck.
## Components
1. **Generator** produces the candidate states or solutions from the search space. 
2. **Tester** takes each candidate and checks whether it satisfies the goal condition. 
## Algorithm 
1. Generate a candidate solution. 
2. Test it against the goal (expected solution). 
3. If the solution has been found, then quit. 
4. Else go to step 1.
5. If all candidates exhausted, return failure.

## Heuristic-Assisted Generate and Test Search 
The basic version is purely bruteforce. However, heuristic can be used at the generator level to make it efficient:
-  The heuristic ranks candidate solutions before testing.`
- Paths that are unlikely to lead to the goal are deprioritized.
- It reduces wasted effort on the tester's side.
Here, heuristic shapes what gets generated.
## Questions

## Reflection 
