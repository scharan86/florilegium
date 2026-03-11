---
tags:
  - cs/ai/gofai
created: 2026-03-11
status: draft
type: concept
aliases:
  - Problem Formulation
---
---

 > [!definitions]
 > A *problem* is a **formal specification** of a task, typically defined as a tuple consisting of five components: initial state, actions, transition model, goal state and path cost.
 > 
> A *problem representation* is the specific data structure  and logic used to describe the problem to a computer.

- A search problem is a tuple consisting of five components: Initial State, Actions, Goal Test, Transition Model,  Goal Test, and Path Cost. It's defined using these 5 components.

*Transition model specifies the state that results from applying a particular action to a given state.*

>[!question]- Why do we need problem representation? 
> Informally, Problem representation translates real-world into code. 
> More formally, problem representation defines the following:
> 	- Storage of a **state** in memory  (`struct` or `BitVec`)
> 	- Possible legal actions from a particular state.
> 	- Results of those actions.
> Problem representation serves as a layer of abstraction that encapsulates the problem's logic, while [[State Space Search | state space search]] algorithms act as the computational engine.
> ==It defines how the environment behaves and what counts as a solution==

 
