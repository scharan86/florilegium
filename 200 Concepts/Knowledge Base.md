---
tags:
  - cs/ai/gofai
created: 2026-03-13
status: stable
type: concept
aliases:
  - KB
---
---
>[!note] Knowledge Base
>It stores domain specific knowledge as **[[Production Rules|production rules]]** (if-then statements):
>```
>IF <condition>
THEN <conclusion or action>
>```

- ==Rules are declarative==, i.e. they express relationship not procedure. The system decides when and in what order rules are applied.
- Knowledge engineer converts the **domain-knowledge** into production rules.
- One of the [[Formal Knowledge Representation]] is used to incorporate the information into the system. 
- The domain-knowledge acquired from a human expert must be encoded such that the meaning and integrity of the knowledge is intact.
- [[Knowledge Acquisition Bottleneck]]

> *The performance of an expert system is primarily contingent on the quality and amount of knowledge present in the knowledge base pertaining to a specific domain.*

>[!example] Medical diagnosis system
>```
>Rule 12:
>	IF fever = true  // antecedent
>	AND cough = true
>	AND oxygen_saturation < 95
>	THEN suspect_pneumonia = true   // consequent
>	AND action = "order chest X-ray" 
>```
>Each rule has two parts:
>1. **Antecedent** (`IF` part), it can have multiple conditions joined by `AND/NOT/OR`
>2. **Consequent** (`THEN` part), it introduces new facts or modify existing ones or trigger actions.

## Questions

## Reflection 
