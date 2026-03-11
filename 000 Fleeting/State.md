---
tags:
  - cs/ai/gofai
  - abstraction
created: 2026-03-11
status: draft
type: concept
---
---

>[!definition]
A *state* is a representation of the configuration of a problem at a given instant, containing all the information necessary to describe the situation **uniquely** and to determine applicability of **operators**. 

- Complete description of the world at a given point in time. 
- It captures all the information relevant to the problem that separates one situation from another.
- A state must contain enough information to determine the available actions and what the next state will be after an action is performed.
==A state is an abstraction that ignores the irrelevant details of the world and captures only what matters for the problem==.
## Reflection 
State is just the configuration of a problem at a given time. It contains info needed to identify a situation uniquely and the actions available.
