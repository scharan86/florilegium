---
tags:
  - cs/ai/ml
created: 2026-03-14
status: stable
type: concept
aliases:
  - SL
  - supervised learning
  - supervised
---
---

>[!Definition]
> Supervised learning is a [[Function Approximation Problem|function approximation problem]], where there exists a set of input-output pairs called the [[Training Dataset|training set]] and the goal is to find a function that maps the inputs to their corresponding outputs in way that is [[Generalization|generalized]] to unseen data.
> 

- It's an [[ML]] paradigm
- The word "supervised" is used to indicate that learning is guided by the labels (ground-truth output). 
- The labeled training set 
## Intuition

## Explanation
Formally, we assume that there exists a function:
$$ f: X \to Y$$ where $X$ is the [[Input Space|feature space]] and $Y$ is the [[Output Space|output space]] (labels or values or ground-truth) . Here, the tricky part is that we don't really know what the function $f$ is. However, we observe a **finite dataset**:  
$$D = \{(x_1,y_1), (x_2,y_2), (x_3, y_3)...(x_n,y_n)\}$$ where $y_i \approx f(x_i)$ with some noise. The task is to find a hypothesis $h$ from a Hypothesis class $H$ such that $h \approx f$.

## Properties
1. Supervised learning algorithms use a labeled dataset to train a model.
2. 

## Core Components of Supervised Learning Systems
![[Pasted image 20260315184042.png]]
1. **[[Hypothesis class]]** (set of all functions the model can possibly represent), kinda like [[State Space]]
2. **[[Loss Functions|Loss Function]]**: Measures how wrong the current hypothesis is on the training set, kinda similar to a [[Heuristic]]
3. **Optimization Procedure**: The algorithm that the hypothesis class to find the $h$ that minimizes the loss, kinda like [[State Space Search|state space search]] 
   
>[!question]- How are Supervised Learning Systems different from State Space Search Systems??
>They might seem very similar on the surface as the Hypothesis class is kinda similar in concept to [[State Space|state space]] and the loss function kinda acts as the [[Heuristic|heuristic]] here as the model tries to find a function that minimizes it the most during training and the optimization procedure is kinda similar [[state space search]] algorithms that iteratively search the state space to find a path to the goal state using some kinda heuristic if its informed search. 
>However, in state space search, the space is **a [[Discrete Space|discrete space]] and symbolic**. The search terminates when the target state is found. In supervised learning, the hypothesis space is continuous, high-dimensional [[manifold|manifold]] of numbers or [[Weights|weights]]. There is no single goal state. The optimizer doesn't explore by branching, it follows the gradient, which doesn't exist in classical search. In search, the [[Heuristic|heuristic function]] is defined over the states, whereas, in supervised learning, the loss function is defined over data — **it tells you how well the current function fits over the observations**. 
>The [[Successor Function|successor function]] for state space search is relatively inexpensive. In supervised learning, the successor function is gradient, which is expensive ([[Backpropagation|backprop]]) and approximate.

## Problems
Supervised learning mainly deals with two types of problems:
1. [[Classification]]
2. [[Regression]]
## Advantages
1. Ability to learn price **input-output** mapping.
2. **Clear objective during training** as it defines an explict loss function measuring prediction error.
3. Performance can be measured objectively as [[Ground Truth|ground-truth]] is available. 
4. Produces high predictive performance with enough labeled data. 
## Limitations
1. The primary limitation is that it requires **labeled data**. 
2. If the model is too complex relative to the size of the dataset, it may memorize the training samples instead of learning patterns, i.e. [[Overfitting]]
3. It can only learn relationships defined by the labels, cannot naturally discover underlying data distribution, hidden clusters, latent structures. 
## Application
1. [[Medical Diagnosis Models]]
2. [[Recommendation Systems]]
3. [[Speech Recognition]]

>[!question]- Why does SL not have a "goal function" like state space search has a goal state? 
>We almost never know what the "goal function" actually is for real problems. The true underlying function is unknown or unknowable, whereas in classical search, we have an explicitly defined target state. In SL, **zero training loss still doesn't mean that the model has has found the perfect function**, it just means that the current function fits the known observations perfectly. In serach, the heuristic function estimates the distance to a goal and in SL, loss function just estimates how badly the current function is performing on seen data. In SL, the primary goal is [[Generalization |generalization]] over a function that perfectly fits the known observations.
## Related Concepts