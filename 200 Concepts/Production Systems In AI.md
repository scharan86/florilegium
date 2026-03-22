---
tags:
  - cs/ai/gofai
created: 2026-03-11
status: stable
type: concept
aliases:
  - production system
---
---
# Production Systems
>[!definition] 
> A *production system* is a general computational model for **rule-based reasoning** and execution of search processes in artificial intelligence.

- It's the mechanism by which AI systems can reason. 
- It's a formal model used in AI for **problem solving** and **reasoning**
- [[Expert Systems]] is the real-world AI system that uses production system and domain-knowledge.
## Working 
The production system:
1. Looks at the current facts (working memory)
2. Finds rules that match the condition
3. Executes one of those rules
4.  Updates the facts 
5. Repeats
## Components of Production Systems
### Rules
```
if(condition) then(action)
```
The condition checks if the rule is applicable to the current state and action describes what it should do. 
### DB
Holds the current state of the problem and is updated when rules fire.
### Control Strategy (Conflict Resolution)
Decides which rule to apply when multiple rules are applicable.
### Rule Applier (Executor)
Mechanism that actually executes a rule against the database.

## Types (Characteristics) of Production Systems

| Type                  | Key Property                                                | Example                        |
| --------------------- | ----------------------------------------------------------- | ------------------------------ |
| Monotonic             | Applying a rule never blocks future rules                   | 8-puzzle, Water Jug            |
| Non-Monotonic         | Applying a rule can block future rules                      | Chess, Tic-Tac-Toe, Scheduling |
| Partially Commutative | Order of compatible rules doesn't matter                    | Sudoku, Smoothie mixing        |
| Commutative           | Both monotonic + partially commutative; order never matters | Shape matching                 |

>[!question] How does it connects to state space search?
> The production system is essentially the _engine_ that operates on the state space — rules are the operators, the database is the current state, and the control strategy is the search algorithm deciding which operator to apply next.

---
