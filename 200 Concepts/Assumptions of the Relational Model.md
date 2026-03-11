---
tags:
  - cs/db
created: 2026-03-09
status: stable
type: concept
---
---

>[!important] Codd wanted to achieve the following things
>1. Store data
>2. ensure correctness
>3. allow powerful querying
>4. maintain logical independence from physical storage

To achieve these objectives, Codd imposed several strict assumptions:
1. All information in the database must be represented as values in tables.
2. Each attribute must contain atomic values (1NF) {because relational algebra assumes each field only contains exactly one value}
3. A table cannot contain duplicate rows {a relation is a set and a mathematical set can't have duplicates. To enforce this DBs use keys}
4. Row order doesn't matter {Relations are unordered sets} 
5. Column order is irrelevant
6. **Closed World Assumption** (It assumes what is not stored is *false*)
7. Relationship between tables must be valid.  This prevents dangling reference (every order must refer to an existing user)
8. Each attribute must draw values from a predefined domain (e.g. age). 
9. Applications must not depend on the physical storage layout. I.e, the database may store the tables as B-tree, LSM trees or heap files but the query must remain the same.
10. The model defines operations for manipulating relations (relational algebra operations).

These assumptions give modern relational databases three important properties: 
1. Data obeys math
2. Optimizer can rewrite queries safely because relational algebra has well defined laws.
3. Constraints prevent inconsistent state.
## Questions

## Reflection 
