---
tags:
  - cs/ai/gofai
created: 2026-03-12
status: draft
type: concept
aliases:
  - minimax algorithm
---
---
# Minimax 
It's a **recursive**, [[DFS|depth-first search]] algorithm that computes the optimal move for MAX assuming both players play perfectly.

Formally, minimax value of node $n$ is defined as: 
$$
\text{minimax}(n) =
\begin{cases}
\text{utility}(n) & \text{if } n \text{ is a terminal node} \\
\max\limits_{c \in \text{children}(n)} \text{minimax}(c) & \text{if } n \text{ is a MAX node} \\
\min\limits_{c \in \text{children}(n)} \text{minimax}(c) & \text{if } n \text{ is a MIN node}
\end{cases}
$$
## Algorithm
```
function minimax(node, is_maximizing_player):
	if node is terminal:
		return utility(node)
	if is_maximizing_player:
		best_value = -infinity
		for each child of node:
			value = minimax(child, false)
			best_value = max(best_value, value)
		return best_value
	else:
		best_value = +infinity
		for each child of node:
			value = minimax(child, true)
			best_value = min(best_value, value)
		return best_value 
```
- MAX nodes take the maximum of children.
- MIN nodes take the minimum of children. 
- Terminal nodes return the true utility.

##  Complexity 
1. Time: $O(b^d)$ 
2. Space: $O(bd)$ 
where  $b$ is the branching factor and $d$ is the depth.

## Evaluation Function
- Real games like Chess, Go are too deep to reach to the terminal node in reasonable time. 
- Therefore, pure minimax generally doesn't work for these games.
- So we cut off search at a fixed depth and apply an **evaluation function** (heuristic function or static evaluator) to estimate the value of non-terminal nodes. 
- In short, it estimates the state quality when the terminal nodes are too deep to reach within the time constraints.
Formally, 
```
eval(s) > 0  →  state favors MAX
eval(s) < 0  →  state favors MIN
eval(s) = 0  →  state is neutral
```

## Limitations  
>[!question]- How do you assign a non-terminal state a value in [[Adversarial Search|adversarial search]]?
> Assigning values to leaf nodes is easy as we can directly read the score. There is where minimax algorithm comes into play. Minimax says that a node's value is determined by what the opponent would do from there.
> 
> You can't assign a value to the current state without knowing what future states are worth. And you can't know what future states are worth without knowing what states come after _them_. So you have to go all the way to the end first, get the terminal values, and then work your way back to the present.
>  
>So the question becomes: **how far ahead do you look, and how do you collapse all those future possibilities into a single decision right now?** 
>
  Minimax answers this with one simple rule:
>	*At every step, assume the current player plays as well as they possibly can*
>	
>Practically,
>- You reach a leaf node. It has a score. Done, no reasoning needed.
> - You reach a MIN node. You don't know which child MIN will pick — but you know MIN will pick the _worst one for you_. So the value of this node is the minimum of its children's values. That's MIN's optimal play, by definition.
> - You reach a MAX node. Same logic — you'll pick the best one for you. So the value is the maximum of its children's values.

- Minimax algorithm is complete and optimal
- The two players are called: **maximizer and minimizer**. 
- If the maximizer has an upper hand, then score will be positive.
- It traverses the game tree assuming that MAX always maximizes and MIN always minimizes.
- [[Alpha Beta Pruning]] can be used to improve minimax algorithm's efficiency.

## Reflection 
I don't really understand recursion that well. I need to learn it.
