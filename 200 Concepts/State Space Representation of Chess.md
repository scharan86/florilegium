---
tags:
  - cs/ai/gofai
created: 2026-03-11
status: stable
type: concept
aliases:
---
---
# Chess
## Set of all possible states ($S$)
A state in chess is the complete config. of the board at any point in time. 
- The position of every piece on the board. 
- Whose turn it is to move.
- Information about castling rights or en passant availability.

## Set of all possible actions ($A$)
The global set of all possible moves in the game of chess.

## Applicable Actions in state $s$ ($Action(s)$)
For a specific board configuration $s$, it filters down $A$ to all the possible legal moves available in the state $s$.

 e.g. A pawn on the $7^{th}$ rank can promote, a king can't move into check, a piece that has been pinned cannot move. 
 
 On average, $Action(s)$ gives about $30$-$35$ legal moves per position. 

## Transition Function ($Result(s,a)$)
Given a board configuration $s$ and a **legal move** $a$ : $Result(s,a)$ returns the new board state after the move is made. 

e.g. $Result(starting position, e2 \to e4) = new \ board \ with \ pawn \ on \ e4$  

*This function defines the edge of the state space graph, where each edge is a legal move and the nodes are positions*

## Cost of an action ($Cost(s,a)$)
In chess, every move has a uniform cost of 1 but you want to checkmate in the fewest moves possible.

| **Property**             | **Chess**                     |
| ------------------------ | ----------------------------- |
| State space size         | $10^{47} \ legal \ positions$ |
| Average branching factor | $\approx 35$                  |
| Average game length      | $\approx 80 \ moves$          |
| Search tree nodes        | $\approx 10^{120}$            |

## Reflection 
