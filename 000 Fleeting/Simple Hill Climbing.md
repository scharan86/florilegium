---
tags: []
created: 2026-03-12
status: draft
type: concept
---
---
>[!concept] Hill Climbing 
>It's a heuristic search that works like climbing a hill, always move upward towards better states. It iteratively improves the current state using an evaluation function till the goal state or local optimum is reached (peak).
# Simple Hill Climbing
## Core Idea
Take the first improvement you find and move there immediately.

## Algorithm
1. If the initial state is goal, then done.
2. Otherwise, loop:
	- Apply an unused operator (action) to generate a state. 
	- If it's goal, then done. 
	- If it's better than the current state, then make it the current state.
	- If it's not better than the current state, then continue the loop.
# Steepest-Ascent Hill Climbing
## Core idea
Don't move until you've seen all the neighbors and then move to the best one. 

## Algorithm
1. If the initial state is goal, then done. 
2. Otherwise, loop:
	- Generate all successors using every usable operator.
	- Find the best state and call it $S$. 
	- if $S$ is better than current state, set current state to $S$. 
	- If no improvement at all, then stop.

**It exhausts all options at each step before committing, whereas simple hill climbing algorithm commits early.** 
## Limitations of Hill Climbing Search 
1. It get's stuck at local maxima.
![[Pasted image 20260312155742.png]]
2. Backtracking must be used to overcome local max. 
3. It can hit plateau (same value for all neighboring states)
4. Random state selection can be used to overcome plateau
5. **Ridge**: A special kind of local maxima that is higher than surrounding areas. 
## Features
1. Uses heuristics. 
2. Considers only current state and its neighbors (local state algo)
3. Uses the greedy approach, i.e, follows direction of immediate improvement.
4. Memory efficient (stores only current state)
5. Simple to implement.
6. Iteratively improves the solution until no better neighbors are there.

## Applications
1. Optimization problem such as function maximization/minimization and parameter tuning.
2. Rearranging blocks using local improvements.
3. Scheduling problems like exam timetabling. 
4. Game playing problem like choosing the best move based on the evaluation function. 
5. Machine learning problems like feature selection and hyperparameter tuning. 
6. Path planning in robotics.
## Questions

## Reflection 
