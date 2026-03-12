---
tags:
created: 2026-03-12
status: draft
type: concept
---
---
>[!concept]
>Greedy Best-first search expands the node the lowest $h(n)$. I.e, the one that looks closest to the goal. It's fast but not optimal as it ignores the cost already incurred to reach the current node.

- It evaluates the nodes just by the heuristic function. $f(n) = h(n)$ where $f(n)$ is the evaluation function.
- At each step, it uses the heuristic function and selects the most promising node generated so far.
- It always picks the node that looks closest to the goal according to the heuristic. 

>[!important] Comparison with DFS and BFS
>It behaves somewhat like DFS in spirit because it chases the most promising-looking path deeply rather spreading out level by level. This makes it fast in practice when the heuristic function is good. 
>
>It doesn't inherit BFS's guarantee of finding the shortest path and doesn't systematically explore breadth-first at any point.

## Algorithm
**Open list**: nodes discovered but unexplored.
**Closed list**: nodes already explored.

1. Initialize a tree with the root node (start node) in the open list.
2. If the open list is empty, the search has failed (no solution exists).
3. Select the node with the lowest $h(x)$ from the open list and move it to the closed list.  (**Priority Queue** makes this efficient)
4. Expand that node, for each child:
	- If it's the goal then return success.
	- If it hasn't been explored before, add it to the closed list.
5. Repeat from step 2

## Questions

## Reflection 
