---
tags:
  - cs/ai/gofai
created: 2026-03-13
status: stable
type: concept
---
---
>[!definition]
>It's a reasoning mechanism used in [[AI Systems]], it applies logical rules to known facts to derive new conclusions.
>
> More specifically,
> **It determines the rules that can be applied on the facts in working memory by examining the rules in knowledge base**

![[inference-engine-diagram.png]]

- ==Interface engine is the mechanism that runs [[production system]].==
- It's the **control program** of [[Expert Systems|expert systems]], [[Production Systems In AI|production system]], [[Logic-based Systems]]. 
- It's kinda like CPU for reasoning
- It doesn't contain knowledge, it operates on knowledge.
## Inference Engine Execution Cycle
- It runs as a [[Production Cycle|recognize-act cycle]]
 - [[Rete Algorithm]] optimizes inference engine such that it doesn't have to match all rules against all facts on every recognize-act cycle. 
## Inference Strategies
1. [[Forward Chaining]]
2. [[Backward Chaining]]
3. [[Hybrid Chaining]]
