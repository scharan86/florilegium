---
tags: []
created: 2026-03-14
type: source
origin: Claude
reliability: trustworthy
---
## What knowledge representation actually does

Before the engine can reason over knowledge, that knowledge must be stored in a form the engine can manipulate — pattern-match against, traverse, compare, unify. The representation is not just storage. It determines:

- What kinds of facts can even be expressed
- How efficiently the engine can match and retrieve them
- How naturally the domain maps onto the formalism
- How easily a knowledge engineer can read, debug, and extend it

Different domains have fundamentally different _shapes_ of knowledge. A representation optimized for one shape is clumsy or outright incapable for another.

## Abstraction
A **knowledge representation method** is an abstraction over raw domain knowledge. It does exactly what any abstraction does:

**Hides irrelevant detail** — you do not care that "robin IS-A bird" is stored as a pointer in a graph, a row in a table, or a Prolog clause. The representation hides the storage mechanism and exposes only the relationship.

**Exposes a defined interface** — the representation defines what operations are valid. A semantic network exposes traversal and inheritance lookup. A production rule exposes pattern matching. A Bayesian network exposes probability propagation. The inference engine talks to these interfaces, not to raw data.

**Preserves essential structure** — the abstraction must capture the properties that matter for reasoning. IS-A transitivity, default inheritance, conditional independence — whatever the domain requires must survive the encoding. This is exactly the "meaning and integrity" requirement from the previous statement, now seen as a property of a good abstraction.

## Consequence of Abstraction
This is why different methods exist and why choosing the wrong one breaks things. Every abstraction has a **representation bias** — it makes some things easy to express and some things hard or impossible. Production rules make conditionals easy and hierarchies hard. Semantic networks make hierarchies easy and uncertainty hard. Fuzzy logic makes gradations easy and discrete categorical facts clumsy.

When the shape of the abstraction mismatches the shape of the knowledge, you either lose information (integrity breaks) or you contort the knowledge into an unnatural form (meaning breaks) — both of which are exactly the failure modes discussed earlier.

So the entire question of _"which representation method"_ is really the question of _"which abstraction fits the structure of this domain's knowledge best."_

## Methods

## Notes

## Extracted to
