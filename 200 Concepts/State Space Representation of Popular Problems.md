---
tags:
  - cs/ai/gofai
created: 2026-03-11
status: stable
type: concept
---
---
# Popular Problems
## Missionaries and Cannibals

_(3 missionaries, 3 cannibals, 1 boat — goal is to move everyone to the right bank)_

|Component|Definition|
|---|---|
|**State (S)**|A triple (m, c, b) where m = missionaries on left bank, c = cannibals on left bank, b = boat side (0 = right, 1 = left). So m ∈ {0,1,2,3}, c ∈ {0,1,2,3}, b ∈ {0,1}|
|**Initial State**|(3, 3, 1) — everyone and the boat on the left bank|
|**Goal State**|(0, 0, 0) — everyone moved to the right bank|
|**Actions(s)**|Move 1 or 2 people across in the boat (at least 1 person must row). Possible combinations: (1M), (2M), (1C), (2C), (1M+1C)|
|**T(s, a)**|New (m, c, b) after moving the chosen people — subtract from the departure bank, add to the arrival bank, flip b|
|**C(s, a)**|1 per crossing (uniform cost)|

**Validity constraint** (what makes states legal): on neither bank should cannibals outnumber missionaries, unless there are zero missionaries on that bank.
## Tower of Hanoi

| Component         | Definition                                                                                                                  |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------- |
| **State (S)**     | A tuple describing which peg each disk is on. E.g., for 3 disks: (A, A, B) means disk 1 and 2 are on peg A, disk 3 on peg B |
| **Initial State** | All disks on peg A — (A, A, A)                                                                                              |
| **Goal State**    | All disks on peg C — (C, C, C)                                                                                              |
| **Actions(s)**    | Move the top disk from any peg X to any peg Y, provided Y is empty or its top disk is larger than the disk being moved      |
| **T(s, a)**       | The new state after moving the top disk from peg X to peg Y — all other disks stay the same                                 |
| **C(s, a)**       | 1 per move (uniform cost)                                                                                                   |

## Water Jug Problem

_(Classic version: 4-litre jug and 3-litre jug, goal is to get exactly 2 litres)_

| Component         | Definition                                                                                                                |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------- |
| **State (S)**     | A pair (x, y) where x = litres in the 4L jug, y = litres in the 3L jug. So x ∈ {0,1,2,3,4} and y ∈ {0,1,2,3}              |
| **Initial State** | (0, 0) — both jugs empty                                                                                                  |
| **Goal State**    | Any state where x = 2, i.e., (2, y) for any valid y                                                                       |
| **Actions(s)**    | Fill either jug fully, empty either jug completely, or pour from one jug into the other until one is full or one is empty |
| **T(s, a)**       | The new (x, y) after applying the action — water is conserved, and no jug overflows                                       |
| **C(s, a)**       | 1 per action (uniform cost)                                                                                               |
## 8 Puzzle

| Component         | Definition                                                                                                                                    |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **State (S)**     | A 3x3 grid arrangement of tiles 1–8 and one blank. Represented as a tuple of 9 values, e.g., (1, 2, 3, 4, 0, 6, 7, 5, 8) where 0 is the blank |
| **Initial State** | Any given scrambled configuration of the grid                                                                                                 |
| **Goal State**    | (1, 2, 3, 4, 5, 6, 7, 8, 0) — tiles in order, blank at bottom-right                                                                           |
| **Actions(s)**    | Slide a tile adjacent to the blank into the blank's position — Up, Down, Left, or Right (only valid directions depending on blank's position) |
| **T(s, a)**       | New grid after swapping the blank with the neighboring tile in the chosen direction                                                           |
| **C(s, a)**       | 1 per move (uniform cost)                                                                                                                     |

## N-Queens

| Component         | Definition                                                                                                                                                                                     |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **State (S)**     | A board configuration showing how many queens have been placed and in which columns, row by row. E.g., for N=4: (1, 3, —, —) means queen in col 1 on row 1, col 3 on row 2, rows 3 and 4 empty |
| **Initial State** | Empty board — no queens placed                                                                                                                                                                 |
| **Goal State**    | All N queens placed such that no two share a row, column, or diagonal                                                                                                                          |
| **Actions(s)**    | Place a queen in any column of the next empty row, provided it does not attack any already-placed queen                                                                                        |
| **T(s, a)**       | New board state with one additional queen placed in the chosen column of the next row                                                                                                          |
| **C(s, a)**       | Not typically defined — this is a constraint satisfaction problem, cost is usually irrelevant                                                                                                  |

## Tic-Tac-Toe

| Component         | Definition                                                                                                        |
| ----------------- | ----------------------------------------------------------------------------------------------------------------- |
| **State (S)**     | A 3x3 grid where each cell is X, O, or empty. E.g., (X, O, X, —, O, —, —, —, —)                                   |
| **Initial State** | All 9 cells empty                                                                                                 |
| **Goal State**    | Any state where one player has three marks in a row, column, or diagonal — or all cells filled (draw)             |
| **Actions(s)**    | Current player places their mark (X or O) in any empty cell                                                       |
| **T(s, a)**       | New board with the chosen cell filled by the current player's mark; turn switches to the other player             |
| **C(s, a)**       | Not typically defined — this is a two-player game, optimality is measured by win/lose/draw outcome, not path cost |
