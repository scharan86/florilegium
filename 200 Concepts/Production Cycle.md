---
tags:
  - cs/ai/gofai
created: 2026-03-14
status: stable
type: concept
aliases:
  - recognize-act cycle
  - match-select-execute cycle
---
---
>[!Production cycle]
>It's a control loop used by rule-based systems to **repeatedly apply rules to facts** until there are no more rules to fire.

# Operations in Production Cycle
It repeatedly performs three operations:
1. **Match**: find all the rules that satisfy the current facts in the [[Fact Database|working memory]]. 
2. **Select**: If multiple rules match, then select one. (*conflict resolution*)
3. **Execute**: Fire the selected rule, updating the working memory.
4. REPEAT till quiescence or halt condition is met.

