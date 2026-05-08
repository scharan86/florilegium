---
tags:
  - cs/ai
created: 2026-05-05
type: source
origin: clg-ppt
---
# Reasoning Under Uncertainty

[[Classical logic]] uses [[Monotonic Reasoning|monotonic reasoning]] (adding new premises doesn't invalidate previously derived conclusions). This makes it unsuitable for the real-world because the derived conclusions can never be retracted, even when new information is added. It assumes the world to be static. 

The real world has three core properties that make [[Non Monotonic Reasoning | NMR]] more suitable:
1. Incomplete Information
2. Noisy Information
3. Conflicting Evidence
4. Evolving ([[Monotonicity|Non-monotonicity]], derived conclusion may get overturned by a new fact)

> [!question] Why CWA doesn't work for reality? 
> [[Closed World Assumption| CWA]] doesn't work for the real world because the real world isn't a closed system. It eliminates ambiguity  (by treating unknowns as "false") when you don't have enough evidence to swing either way. [[OWA]] preserves ambiguity (unknowns remain unknowns).  

> *AI systems must perform inference under uncertainty while handling incomplete, inconsistent and evolving knowledge.*

[[Uncertain Reasoning|Uncertain reasoning]] acknowledges that the world is partially known and the [[KB]] is incomplete and quantifies the amount of known information through probability.

## Approaches
### Symbolic Reasoning 
- It represents (encodes) knowledge using symbols and relationships between them.
- It uses [[FOPL]] 
- It  assumes [[Principle of Bivalance| bivalance]] (predicates are either true or false)
- Incapable of representing uncertainty. 
 
>[!example]
>Classic example:
> - A: All spiders have eight legs.
> - B : Black widows are a type of spider.
> - C : Black widows have eight legs.
> - Conclusion: A $\wedge$ B $\implies$ C

## Statistical Reasoning (Probabilistic)
- Statistical Reasoning handles the uncertainty in a [[KB]] by assigning a probability to the propositions. 
- Unlike [[Classical Logic]], it handles the unknowns through probability.
- It becomes necessary for problems with **randomness and unpredictability**
- [[Bayesian Networks]] are used to represent the relationship between multiple events.

## Fuzzy Logic Reasoning


![[Pasted image 20260505210919.png]]



## Extracted to
