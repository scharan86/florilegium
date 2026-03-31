---
tags:
  - cs/ai/gofai
created: 2026-03-26
status: draft
type: concept
aliases:
  - symbolic representation
---
---

>[!Definition]
> *Symbolic Representation* is the practice of encoding knowledge about the world using **discrete and structured symbols** like words, predicates, logic formulas or graph nodes instead of numeric vectors or probabilities.

>[!question]- Isn't everything a symbol? 
>At the hardware level, everything is a symbol as everything is ultimately bits. However, the distinction between symbolic and non-symbolic stuff is where the meaning lives and how the sturcture is encoded.

- Explicitly encoded knowledge used by [[Knowledge Based Systems|knowledge-based systems]] use symbolic representation as the bridge between the human expert's mind and the [[Knowledge Base|KB]], which the inference engine operates on. 

``` 
3-stage process (EXPERT KNOWLEDGE -> SYMBOLIC REPRESENTATION -> INFERENCE ENGINE)
----------------------------------------------------------------------------------
Human Expert's Mind
        |
        |  (knowledge acquisition / interviews)
        v
Symbolic Representation        <-- this is the bridge
        |
        |  (fed into)
        v
Inference Engine
        |
        v
Conclusions / Decisions
```

## Syntax vs Symbolic Representation
```
IF   patient.symptom = fever
AND  patient.wbc_count > 11000
THEN hypothesis = infection
```

There are **two separate things** present here:

| Part                                            | What it is                                                                        |
| ----------------------------------------------- | --------------------------------------------------------------------------------- |
| `fever`, `wbc_count`, `hypothesis`, `infection` | **Symbolic representation** — the discrete, named tokens that carry meaning       |
| `IF`, `AND`, `THEN`, `>`, `=`                   | **Rule syntax** — the logical scaffolding that defines _how_ those symbols relate |
## Properties
1. **Discreetness**: symbols are atomic, distinct units. E.g. the symbol `CAT` is either present or not. There is no half  `CAT`.
2. **Composability**: Simple symbols are used to compose complex meanings. `PARENT(tom, bob)`. 
3. Easily understood by humans
4. They can be processed by the inference engine.

## Forms of Symbolic Representation
1. [[Prepositional Logic]] 
2. [[Predicate Logic]]
3. [[Production Rules]]
4. [[Semantic Networks]]
## Summary
Symbolic representation is a method of reprsenting real world knowledge in way that knowledge based systems can process it using their inference engines. The way to do that is represent peices of information as discreet symbols to eliminate ambiguity and ensure simplicity. 
## Related Concepts
1. [[Knowledge Based Systems]] 
2. [[Inference Engine]]
3. [[Expert Systems]]