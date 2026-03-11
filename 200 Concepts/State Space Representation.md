---
tags:
  - cs/ai/gofai
created: 2026-03-11
status: draft
type: concept
---
---
>[!definition]
>*State Space Representation* is a formal model of a problem defined by a tuple consisting of: all possible configurations of a problem, the actions that transition between them, and the cost associated  with those transitions, such that a search algo can systematically explore the space to find a solution.

In [[State Space Search| state space search]], State space is formally represented as a tuple: 
$$ S \space : \space \langle S, \ A, \ Action(s) \ T(s,a), C(s,a) \ \rangle $$
where:
- $S$ is the set of all possible states. 
- $A$ is the set of all possible actions in a state space.
- $Action(s)$ is the function that determines which actions are applicable in state $s$. 
- $T(s,a)$ is the transition function that maps state-action pair to a new state. 
- $C(s,a)$ is the cost of performing the action $a$ in state $s$. 

>[!important] Why do we need a global set of all actions? 
>A can be redundant in practicality because the state space only contains legal positions, but it conceptually represents what the system can do in general and $Action(s)$ represents what the system is allowed to do in general.

## Examples
1. [[State Space Representation of Chess]]
2. [[State Space Representation of Problem Solving Agents]]
3. [[State Space Representation of Popular Problems]]
4. [[Missionaries and Cannibals]]

## Reflection 
It's just a formal way to describe / encapsulate state space.
