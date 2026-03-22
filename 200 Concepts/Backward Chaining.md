---
tags:
  - cs/ai/gofai
created: 2026-03-14
status: stable
type: concept
aliases:
  - Goal-driven chaining
---
---
In backward chaining, the [[Inference Engine|inference engine]] starts from the **goal (conclusion or hypothesis)** and works backwards **to find out if the known facts support it**. 
```
Goal (Hypothesis) --> Known facts
```

- It is **consequent-driven** process, it starts `then` and moves towards `if`. 
- It employs a **top-down** approach, it begin with a hypothesis (the goal) and **searches for rules that can conclude the goal**
- [[Prolog]] is a canonical language used for backward chaining.
## Recursive Sub Goaling
1. Inference engine identifies the rules that result in the desired goal. 
2. It treats the antecedent (`if`) of the identified rule as **sub-goals**. 
3. It searches the Knowledge base to see if these **sub-goals** are already known facts.
4. If not, it recursively tries to prove them using other rules.

>[!success] Intelligent behavior.
>When no rule can derive a needed fact, it prompts the user. This is why backward-chaining systems ask questions intelligently rather than demanding all facts upfront.

> [!important] Why do we need backward chaining? 
> Backward chaining is used when a specific hypothesis is to be verified (to check whether the available facts support it). It's the natural model for planning, designing and troubleshooting.  It can be used to explain why the expert system reached a specific conclusion (**Justification**).


