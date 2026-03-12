---
tags:
  - cs/ai/gofai
created: 2026-03-12
status: draft
type: concept
---
---
>[!summary]
>In *single-agent search*, you control every action. The environment responds deterministically to an action. The agent either tries to minimize cost or maximize profit. 
>In *adversarial search*, the environment includes other agents whose goal is the inverse of yours. Therefore, every plan you make must account for the fact that the opponent will try to defeat it.
> 
>And so, this transforms the problem from *finding the best path* $\to$ *finding the best strategy assuming that the opponent plays optimally* (requiring a different way to reason about the solution).

Most search problems in AI assume the follow:
1. The environment isn't hostile.
2. There is no other intelligent agent whose goals actively conflict with yours.
3. The world doesn't actively sabotage you.

However, games are different kind of problem and can't be "solved" with the above mentioned assumptions.

> A game generally has an environment where **another intelligent agent**'s objective conflicts with yours.

>[!definition] 
>*Adversarial search* is a branch of AI concerned with decision-making in **competitive** and **[[Multi Agent Environment|multi-agent environments]]**, specifically where two or more agents have opposing goals.

## Solving Adversarial Search
Adversarial search is the problem: 
*How does an agent choose its actions when another agent is actively working against it?*

To solve it, we need three things:
1. **A way to represent the problem**
   That's where [[game tree]] comes in: states $\to$ nodes, moves $\to$ edges, terminal outcomes $\to$ leaf values. It's just the search space.
2. **A way to traverse the space** 
   That's where [[Minimax Algorithm]] comes in. 
3. **A way to make decision** 
	The bubbled up value from the application of minimax algorithm tells MAX which move to make.
4. **A way to make that traversal efficient**
	That's the role of [[Alpha Beta Pruning]]
   
## Questions

## Reflection 
