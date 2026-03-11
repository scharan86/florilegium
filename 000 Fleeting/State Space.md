---
tags:
  - cs/ai/gofai
  - abstraction
created: 2026-03-11
status: draft
type: concept
aliases:
  - state space graph
  - State space graph
---
---
# State Space (Problem Model)
 *It describes the structure of the problem and exists independently of any algorithm.*
 
> [!question]- How does state space differ from problem representation if they have the same components? 
> [[Problem formulation]] defines the rules of the problems, and these rules induce (lead to) a state space graph consisting of **states** (nodes) and **transitions** (edges). 
> 

>[!definition]
>The *state space* of a problem is a set of all [[State |states]] that are **reachable** from the initial state by applying any sequence of legal or valid operations (actions). 
>
>**Found a better definition:**
>The *state space* is the graph of all the states reachable from the initial state using the transition model.

It is important to note that the state space implicitly defines the problem: *find a path from the initial state to the goal state within this space.*

When you convert it into a formal model, it becomes [[State Space Representation]]. 

==State space is an abstraction. The entire state space is a simplified model of the problem environment. The problem becomes computationally intractable without this abstraction. ==
## Components
1. State
2. Actions or Operations
3. Transition model
4. Initial state 
5. Goal states
6. Path cost
## Types of State Space
1. [[Deterministic State Space]] (8 puzzle)
2. [[Non-deterministic State Space]] (robo nav)
3. [[Fully Observable State Space]] (chess, sudoku)
4. [[Partially Observable State Space]] (poker)
5. [[Explicit vs Implicit State Space]]



