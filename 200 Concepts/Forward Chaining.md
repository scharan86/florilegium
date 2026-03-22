---
tags:
  - cs/ai/gofai
created: 2026-03-14
status: stable
type: concept
aliases:
  - Data-driven chaining
---
---
In forward chaining, [[Inference Engine]] starts from **known facts** and applies rules to **derive new facts** until a goal or conclusion is reached. 
```
Known Facts --> Conclusion (Goal)
```

- It is **exploratory** in nature.
- Forward chaining is an ==antecedent-driven== process, it starts with `if` and works towards the `then` portion of the rule.
- It employs a **bottom-up** approach: ==It begins with known facts and applies production rules to infer new facts until a goal or conclusion is reached or all the rules are exhausted.
- Once it produces a fact identified as "Goal", it stops.

>[!important] When do we use forward chaining? 
>It's used when the system has a set of observation (known facts) and all possible conclusions pertaining to the observations must be derived.
>e.g. classification, diagnosis, etc. It can be used to reach a conclusion (**Discovery**)

