---
tags:
  - cs/ai/gofai
created: 2026-03-12
status: draft
type: concept
---
---
# Minimax Tree 
>[!definition]
>It's a game tree that is evaluated using the [[Minimax Algorithm|minimax algorithm]]. Every minimax tree is a game tree but every game tree isn't a minimax tree. 

## Assumptions
1. Players must take altering turns.
2. It needs two players because the alternative min/max logic breaks down with three or more players. 
3. The games are  complete information games because the evaluation function must see the full board before assigning a meaningful score.
4. Opponents have exactly opposite goals because that's what justifies using a single utility number and flipping between min and maxing it. 
5. It assumes [[Zero Sum Game |zero-sum]]. 

[[Game Tree | Game tree]] is a general representation and these are the assumptions under which the minimax algorithm is valid for searching a game tree.  

It begins with a root node which belongs to the player who is taking a move. I.e, it is a **max layer**. 
