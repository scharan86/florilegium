---
tags:
  - abstraction
created: 2026-03-08
status: draft
type: concept
aliases:
  - Relational Data Model
---
---
# Relational Data Model 

> Relational model uses set theory to represent data as relations (sets of tuples) and express queries and constraints using first-order predicate logic and the database system executes the queries and enforces the constraints.

- It's a mathematical abstraction introduced by Edgar F. Codd. 
- It's the most influential and widely used mathematical theory of data representation. 
- [[Relational Databases]] is a specific implementation of the relational model and aren't purely relational. SQL is the language used to interact with that implementation.
-  It defines the logical structure of data using mathematics and doesn't define a storage system or langauge.

>[!question] How did relational models become the go-to data model for information systems? 
>- **It described data independently of how its stored** ([[Data Independence]])
>- Most business data can be expressed in terms of **entities and attributes** which maps directly to the relational model.
>- It introduced [[declarative querying | Declarative Querying]]
>- Its strong mathematical foundations allowed databases to perform query optimization (rewriting queries while preserving correctness). 

- The relational model is based on three mathematical ideas: Relations, Relational Algebra and Integrity Constraints.

- Key components in the relational model
	1. Relations
	2. Tuples
	3. Attributes
	4. Constraints

# Limitations
[[Assumptions of the Relational Model]] make it restrictive in certain domains:
1. Representing **highly nested data** in the form of normalized tables becomes complex.
2. Massive distributed systems
3. High write throughput systems
4. Relational transactions introduce coordination overhead.
## Questions

## Reflection 
I still don't understand the limitations properly.
## Connections
1. [[Relational Databases]]
2. [[Assumptions of the Relational Model]]