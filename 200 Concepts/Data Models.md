---
tags:
  - cs
  - cs/db
  - abstraction
created: 2026-03-08
status: draft
type: concept
aliases:
  - data models
---
---

> A data model is a formal description of how data is structured, how relationships are represented and how queries can access the data in an information system.

- It's important to note that different models make different assumptions about the shape of the information. 
- [[Relational Model]] is a dominant data model that used in various real world systems because of how well it can express business information.

 >[!important] Scope of Data Models
 >Data models aren't limited to [[Introduction to Databases|databases]], they are used in any system that stores or processes structured information. The only difference being that databases use explicit data models and other systems (programming languages, app design) use implicit or internal data models. 
 >
 >- `struct` is an internal data model for application memory.
 >- OO systems often use **object models** to represent domain entities, a.k.a domain modeling.
 >-  **Data models are used to define how systems exchange information**. e.g. API response uses `JSON`.
 >- Many file formats such as `JSON, CSV, XML` are data models that define how information is structured. 
 >- Knowledge representation systems such as `Neo4j` represent entities and relationships as graphs.

## Major Data Models 
1. [[Hierarchical Data Model]]
2. [[Network Data Model]]
3. [[Relational Model|Relational Data Model]] 
4. [[OO Data Model]]
5. [[Object-Relational Model]]
6. [[Document Data Model]]
7. [[Key-Value Model]]
8. [[Graph Data Model]]
9. [[Wide Column Model]]
## Questions

## Reflection 
