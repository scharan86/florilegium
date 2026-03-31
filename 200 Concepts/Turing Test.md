---
tags:
  - cs/ai
created: 2026-03-26
status: stable
type: concept
aliases:
  - Imitation Game
  - Imitation game
  - turing test
  - Turing test
---
---

>[!Definition]
> A test proposed by Alan Turing to determine if a machine exhibits intelligent behavior equivalent to that of a human. 

Turing formalized the question "Can machines think?". The main problem with this question is the ambiguity that comes along with the world "think", its not quantifiable or concretely definable, making tests infeasible or incomplete. He reframed the question into something that's testable: "Can a machine imitate human conversational behavior to the point where it becomes indistinguishable from a human?" 

This framing is crucial because he essentially replaced an **unobservable internal property** (thinking) with **observable external behavior** (communicating in a conversation). However, it isn't a concrete test for intelligent behavior. 

>[!summary] 
>- Turing Test = **black-box behavioral indistinguishability test**
>- It evaluates = **observable interaction**
>- It ignores = **internal cognition, grounding, mechanism**
>- Passing it means = **you fooled the observer**
>- It does NOT mean = **you are intelligent in a strong sense**
## Imitation Game
### Components
1. Interrogator (human judge)
2. Machine Respondent
3. Human Respondent
### Goal
The judge must determine which entity is the human among the respondents.
### Constraints
1. Communication takes place in text-only (no voice or appearance).
2. The judge asks arbitrary questions. 
3. Both human and machine respond. 
### Check 
If the machine has consistently fooled the judge, then it passes the test.

>[!note] 
>OpenAI's GPT-4 (in 2023) and its subsequent versions passed the turing test. 

## Breaking Point
> indistinguishable behavior is not the same as equivalent intelligence. 

**Reasoning**: Two internally different systems can produce the output.




## Other Limitations
1. Acting like something isn't equivalent to being something. 
2. It measures **imitation** not intelligence.
3. Test is purely symbolic as the input and output are text and doesn't have any connection to the real world, action or perception.
4. It's purely linguistic. [[Total Turing Test]] extends it by adding vision, manipulation and physical world interaction to the equation.

## Summary 
If two entities are interacting, a human and a machine, and we can't reliably identify which one is the human and which one's the machine, then the machine is effectively functioning like a human mind. 

## Related Concepts
1. [[Total Turing Test]]
2. [[Langauge Game]]