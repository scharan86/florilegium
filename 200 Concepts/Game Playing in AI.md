---
tags:
  - cs/ai/gofai
created: 2026-03-12
status: draft
type: concept
---
---
- Earliest and most studied domain in AI.
- Provides a well-defined environment to make decision against intelligent opponents.
- The environment is active, involving multiple agents with competing objectives. I.e, [[Multi Agent Environment]]
- **An agent must reason about its own actions and how the opponent might respond both.**
# Characteristics of a game
1. Finite state space 
2. Clearly defined rules
3. Observable outcomes
4. Well-defined objectives

These characteristics make it suitable for studying algorithms.
# Approaches to Game Playing
The game system makes decisions in competitive games using an approach mentioned below:
## Search-based approaches
- The system **explicitly explores** the [[Game Tree|game tree]] to determine the best move.
- [[Adversarial Search]] is a famous search-based approach. 
- e.g. Deep Blue 

## Simulation-based approaches
- The system simulates many random games and estimates which move leads to a better outcome instead of an exhaustive search of the game tree.
- [[Monte Carlo Tree Search]] is one such important algorithm here.
- e.g. AlphaGo

## Learning-based approaches 
- These systems **learn from experience** as opposed to learning from handcrafted heuristics.
- Techniques: [[Reinforcement Learning]], [[Neural Networks]], Self-play training.
- e.g. AlphaZero

>[!example] AlphaZero Architecture
>It uses neural networks (learning) and MCTS (searching).
## Questions

## Reflection 
