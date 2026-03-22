---
tags:
  - cs/ai/gofai
created: 2026-03-14
status: draft
type: stable
aliases:
  - Working Memory
---
---
>[!Working Memory] 
>It is the **dynamic** and impermanent store of everything known to be true. 

- It only stores the facts relevant to the current reasoning session. 
- It is seeded with initial facts provided by the user or the environment at startup. 
- At its final state, it contains:
	1. Original state
	2. All derived conclusions
- It grows as the [[Expert Systems |expert system]] keeps reasoning.
- It's data that is specific to a case.
- It's primarily used to derive conclusions.

# Working Memory Internals
The working memory is organized as a flat set of objects (facts) internally without any schema or hierarchy. 

## Properties of a fact 
1. **Fact Identifier** that the [[Inference Engine]] uses to refer to facts.
2. A **template or type** describing the kind of fact. 
3. A **slot-value** map with the attribute and its value.

## Lifecycle of a Fact
1. **Assert** 
   Operation that inserts a new fact into the working memory. It's triggered by [[Rete Algorithm]].  If a new fact complete's a rules antecedent, then the rule enters the conflict set.
2. **Retract**
   Operation that removes a fact through its identifier. It propagates through Rete. Rules that were in conflict set due to this fact are removed aswell.
3. **Modify**
   Equivalent to (Retract + Assert with updated **slot values**).