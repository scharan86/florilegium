---
tags: []
created: 2026-03-13
status: draft
type: concept
aliases:
  - alpha-beta pruning
---
---

>[!definition] 
>*Alpha-beta pruning* is a search algorithm that seeks to reduce the number of nodes evaluated by the [[Minimax Algorithm|minimax algorithm]] by eliminating branches that don't have any meaningful effect on the final decision. 

- It improves the efficiency of minimax tree traversal by eliminating branches that can't influence the final decision.
- This reduces the **effective branching factor** without affecting the correctness.
- It's an optimization technique of the minimax algorithm. 
- It solves the exponential time and space complexity limitation of minimax algorithm by **pruning redundant branches of a game tree** 
- The final answer is identical to minimax.
## Algorithm 
```
function alphabeta(node, depth, alpha, beta, isMaximizingPlayer):

    if depth == 0 or node is terminal:
        return eval(node)

    if isMaximizingPlayer:
        best_value = -infinity
        for each child of node:
            value = alphabeta(child, depth-1, alpha, beta, false)
            best_value = max(best_value, value)
            alpha = max(alpha, best_value)

            if beta <= alpha:
                break
        return best_value

    else:
        best_value = +infinity
        for each child of node:
            value = alphabeta(child, depth-1, alpha, beta, true)
            best_value = min(best_value, value)
            beta = min(beta, best_value)

            if beta <= alpha:
                break
        return best_value
```

## Complexity
- **Worst case** — bad move ordering, no improvement. Still O(b^d)
- **Average case** — roughly O(b^(3d/4))
- **Best case** — perfect move ordering, reduces to O(b^(d/2))

That best case is significant. O(b^(d/2)) means the effective branching factor becomes √b. So if chess has branching factor 35, alpha-beta in the best case behaves like a tree with branching factor ~6. That effectively **doubles the search depth** for the same computational cost.

## Limitations


## Questions

## Reflection 
