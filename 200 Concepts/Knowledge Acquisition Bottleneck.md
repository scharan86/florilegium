---
tags:
  - cs/ai/gofai
created: 2026-03-13
status: stable
type: concept
---
---
Domain knowledge from a human expert must be converted into one of the [[Formal Knowledge Representation]] while ensuring:
1. **Semantic Integrity:** The encoded rule must mean exactly what the expert meant.
2. **Logical Integrity**: The rule must interact correctly with all other rules in the [[Knowledge Base|KB]]. 

> Transferring knowledge from a human expert to a computer without any loss of meaningful information is quite difficult.

## Problems associated with knowledge acquisition
1. **Tacit (unspoken) Knowledge**
   Experts generally can't fully articulate why they reach a particular conclusion. This is the primary reason why expert systems failed to scale beyond narrow domains in 1980s.
2. **Boundary Conditions**
   Experts tend to state the rules for the typical case. A knowledge engineer must encode the edge cases.
3. **Rule interaction at scale**
   Rules that are correct on an individual level can produce incorrect conclusions 

