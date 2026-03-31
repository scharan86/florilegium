---
tags:
  - cs/ai/gofai
  - trail
created: 2026-03-11
type: trailhead
aliases:
  - GOFAI
  - Classical AI
  - Logic-based AI
---
# Symbolic AI Trailhead
> It refers to collection of all the methods in artificial intelligence research that uses human-readable (high-level symbolic) representations of problems, logic and search.

It developed applications such as: knowledge-based systems like expert systems, symbolic mathematics, automated theorem provers, ontologies and etc.

>[!important]- How's it different from modern AI/ML? 
>Classical AI primarily relied on symbolic representations and search-based reasoning on top of explicitly encoded knowledge, with little to no learning from data. In contrast, modern AI systems (such as deep neural networks and LLMs) rely on statistical and probabilistic methods to learn patterns from large datasets, optimizing parametric models to approximate input–output relationships.
>
>It's important to note that most AI systems include some explicitly specified structure (such as action spaces, constraints, or input representations), but in classical AI, explicitly encoded knowledge—such as rules and symbolic representations—is the primary driver of reasoning and behavior.
## Foundations
1. [[Artificial Intelligence]]
2. [[Turing Test]]
## Core concepts
### Problem Representation and State Space Search
1. [[Problem Representation]]
2. [[Problem Solving Systems]]
3. [[State]]
4. [[State Space]]
5. [[State Space Representation]]
6. [[State Space Search]]
7. [[Production Systems]]
### Search Algorithms & Strategies
1. [[Search Strategy]]
2. [[Search Algorithms]]
3. [[Uninformed Search]]
4. [[Heuristic Search]]
### Adversarial Search
1. [[Game Playing in AI]]
2. [[Zero Sum Game]]
3. [[Multi Agent Environment]]
4. [[Game Tree]]
5. [[Adversarial Search]]
6. [[Minimax Tree]]
7. [[Minimax Algorithm]]
8. [[Alpha Beta Pruning]]

>[!note] 
>All classical knowledge-based systems relied on [[Symbolic Representation|symbolic representation]] to translate reality (real-world knowledge to be specific) into a format that could be processed by the inference engine.
### Expert Systems (Rule-based)
1. [[Knowledge Based Systems]]
2. [[Expert Systems]] (Components & features)
3. [[Inference]]
4. [[Knowledge Acquisition Bottleneck]] 
5. [[Knowledge Engineering]]
6. [[Formal Knowledge Representation]]
7. [[Expert System Shell]]
8. [[Advantages of Expert Systems]]
9. [[Limitations of Expert Systems]]
## Differences
1. [[State Space vs Search Space]]
2. [[Simple Hill Climbing vs Steepest-Ascent Hill Climbing]]
3. [[Classical Search vs Adversarial Search]]
4. [[State Space Search vs Expert System]]
## Strengths
- **Explainability** — you can always trace _why_ a conclusion was reached, step by step
- **Data efficiency** — rules can be hand-crafted; no training data needed
- **Precision** — logical inference is exact; no ambiguity
- **Knowledge transfer** — domain experts can directly encode their knowledge
## Weaknesses
- **Brittleness** — fails badly outside its defined rules; can't handle noise or ambiguity
- **Knowledge acquisition bottleneck** — encoding real-world knowledge manually is incredibly expensive
- **Combinatorial explosion** — search spaces grow impossibly large for complex problems
- **No learning** — classic symbolic systems don't improve from data on their own