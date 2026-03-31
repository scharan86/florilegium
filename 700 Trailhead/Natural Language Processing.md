---
tags:
  - cs/ai/nlp
  - trail
created: 2026-03-13
type: trailhead
aliases:
  - NLP
---

# Natural Language Processing
>[!definition]
> *Natural Language Processing*  is a subfield of [[Artificial Intelligence|artificial intelligence]]  that enables computers to process, interpret, and generate human language. 
> 
> It refers to computational manipulation of language data.

## Foundations
1. [[Computational Linguistics]]
2. [[Features of Natural Language]]
## Core Concepts
1. [[NLP Preprocessing Pipeline]]


>[!question] What problem does NLP try to solve? 

# Steps in Natural Language Processing


## 1. Morphological Analysis

Study of the **internal structure of words** using the smallest meaningful units called **morphemes**.

Examines: word formation, prefixes/suffixes, root words, inflection, derivation.

| Word        | Analysis          | Meaning             |
| ----------- | ----------------- | ------------------- |
| Unhappiness | un + happy + ness | not + happy + state |
| Cats        | cat + s           | root + plural       |
| Played      | play + ed         | root + past tense   |

"running", "runs", "ran" → all reduced to base form **"run"**


## 2. Syntactic Analysis

Transforms a linear sequence of words into a **parse tree** showing how words relate.

Most English sentences follow **SVO** (Subject + Verb + Object).

**Example:** _"The student completed the assignment"_

- Subject → The student | Verb → completed | Object → the assignment


## 3. Semantic Analysis

Assigns **meaning** to the structures created by syntactic analysis. Studies meaning **independent of context**.

- Morphology → structure of words
- Syntax → structure of sentences
- **Semantics → meaning of sentences**

**Example:** _"I saw the man with a telescope"_ has two meanings:

1. I used a telescope to see the man.
2. The man had a telescope.


## 4. Discourse Integration

Connects meanings of **individual sentences** to understand the overall meaning of a larger text.

**Example:** _"Riya bought a laptop. She needed it for her research."_

- "She" → Riya | "it" → laptop
- Without integration, sentences remain isolated.

## 5. Pragmatic Analysis

Studies how language is used in **real-life situations** based on **context, speaker intention, and social interaction** — not just literal word meaning.

- Semantics = what words **mean**
- Pragmatics = what speaker **intends** to mean

**Example:** "Can you pass the salt?" is a request, not a yes/no question.

| Step          | Focus                  | Key Idea                           |
| ------------- | ---------------------- | ---------------------------------- |
| Morphological | Word structure         | Break words into morphemes         |
| Syntactic     | Sentence structure     | Parse tree, SVO order              |
| Semantic      | Meaning                | Word/sentence meaning, ambiguity   |
| Discourse     | Cross-sentence meaning | Pronoun references, text coherence |
| Pragmatic     | Context & intent       | Speaker's real intention           |

