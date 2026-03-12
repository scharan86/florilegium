---
tags:
  - cs/ai/gofai
created: 2026-03-12
status: draft
type: concept
aliases:
  - Blind Search Control Strategy
  - Blind Search
---
---
>[!definition] 
>*Uninformed Search* is a class of search strategies that explore a problem's state pace **without any additional information** about states other than what is provided in the problem's defintion.

- Uninformed search algorithms are aware of the following: 
	1. Initial State 
	2. Transition Model (How to generate successor states)
	3. Goal Test (How to test if a state is the goal state)
	
- It has no heuristics, no cost estimate, no preferences.

- It doesn't have any domain-specific knowledge about the goal.
   
- In simple terms, it explores the state space until the goal is found or the space is exhausted.

## Algorithms
1. [[BFS]]
2. [[DFS]]
3. [[Generate and Test Search|Uninformed Generate and Test Search]]
Neither algorithm uses any estimate  of distance, cost or relevance. 
## Key Features
1. They explore the search space systematically using BFS or DFS.
2. They don't use additional information (domain-specific knowledge) to guide the search process.
3. It's a **blind search process** since don't consider the cost of reaching the goal state or likelihood of finding a solution.
4. It's simple to implement and understand. 
5. Inefficient for complex problems with large search spaces.
## Questions
## Reflection 
