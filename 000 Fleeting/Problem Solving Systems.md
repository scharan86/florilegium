---
tags:
  - cs/ai/gofai
created: 2026-03-11
status: draft
type: concept
aliases:
  - PSS
---
---

> *Problem solving* is the process of **generating solutions** from the observed data (i.e. initial state). 

Computers are incapable of solving a problem the way humans describe it in natural language. The task must be converted into a **formal search problem**. Therefore, building a problem solving system involves the **transformation of a vague task into a mathematical formulation that can be searched algorithmically**. 

>[!question] Why do we need a problem solving system? 
>Symbolic AI represents knowledge using **symbols and rules** instead of statistical patterns. Therefore, the system *needs a mechanism to reason with these symbols*. Problem Solving Systems provide the mechanism. 
>
>A *problem solving system* converts a vague goal into a structured search problem that a machine can compute. 

## Steps To Build a Problem Solving System

1. **Problem Definition**
	-  The task must be converted into a formal mathematical object before a machine can solve it.
	- This step defines: initial state, goal state, operations (actions) and state space.
	  
2. **Problem Analysis** 
	- Once the problem has been defined, its **computational properties** must be understood. 
	- Things like branching factor, depth of solution, state space size and constraints are analyzed.
	
3. **Knowledge Representation**
	- The system must represent the information in a format that can be manipulated by machines.
	- Since symbolic AI represents knowledge using symbols and rules. Absence of good representation makes reason impossible. 
	-  Common representations include state representation (arrays, graphs, objects) and logical representation (predicate logic).
	  
4. **Selection of Search Technique**
	- The system must decide how to explore the state space once problem is represented. However, different problems require different search strategies.
	- Common search methods include BFS, DFS, and Uniform Cost Search and A* search. 
   
---
## Questions

## Reflection 
