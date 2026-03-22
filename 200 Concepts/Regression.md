---
tags:
  - cs/ai/ml
created: 2026-03-14
status: stable
type: concept
aliases:
  - regression
---
---

>[!definition]
> Regression is [[Supervised Learning|supervised learning]] technique where the [[Output Space|output space]] $Y$ is [[Continuous|continuous]] and the goal is to find a function $h: X \to \mathbb{R}$  that approximates the true conditional expectation $E[Y| X=x]$ . 
## Intuition
Regression is an SL is a method used to predict **real-valued ($\mathbb{R}$) quantities** (not categories) based on the input values. It creates a model that estimates the relationship between input variables and the output variable. 
- Input (feature) is the independent variable (used to predict the dependent variable). 
- Output is the dependent variable.
- It's a task in [[Machine Learning|machine learning]].
## Mechanism
Regression tries to find the $y$ for a given $x$, but problem is that in real-world data, the same $x$ may not always give the same $y$ due to [[Noise|noise]], unmeasurable variables and inherent randomness ([[DGP]]). This means that at any fixed value of $x$, there is a whole distribution of possible $y$ values. The true relationship ($f(x)$) is clean and [[Deterministic|deterministic]] but noise distorts how we actually observe it, which makes it impossible for the regression model to directly find the true underlying function ($f(x)$) since every observation is already distorted by $\varepsilon$ . However, regression approximates the true relationship by **finding the center of the distribution of y values at each x**. This center is the [[Conditional Expectation|conditional expectation]] $E[Y|X=x]$, the average $y$ that is observed across all data points with that particular $x$. Therefore, regression doesn't actually learn the true $y$ per $x$, but an optimal estimate of true $f(x)$.

It's conditional because it's not the average of Y over everything — it's the average _conditioned on_ a specific input value. Different values of x give different conditional expectations, which is exactly what your model is trying to learn.
### Why conditional expectation specifically? 
The conditional expectation is provably the best prediction you can make to minimize the [[Squared Error Loss|squared error loss]] (to be as close to the true value as possible)
## Properties
1. Estimates the [[Conditional Mean|conditional mean]].
2. [[Parametric]] by default, it assumes a fixed functional form with a finite set of parameters. 
3. Sensitive to the [[Loss Functions|loss function]]. 
   Choice of loss function determines what the model converges to. [[Squared Error]] gives conditional mean, [[Absoloute Error]], gives conditional median, [[Huber Loss| Huber loss]] gives something in the between. It essentially changes what the model is learning.
4. It implicitly assumes a [[DGP]] ($y = f(x) + \varepsilon$)  and that noise is **additive** and has **mean zero**. 
## Objectives
1. [[Prediction]]
2. [[Trend Estimation]]
3. Understanding relationship
4. Quantifying impact.

## Types of Regression

| Type                           | What it does                                                                            |
| ------------------------------ | --------------------------------------------------------------------------------------- |
| [[Linear Regression]]          | Predicts a continuous output as a weighted sum of inputs                                |
| [[Multiple Linear Regression]] | Linear regression with more than one input feature                                      |
| [[Polynomial Regression]]      | Extends linear by adding powers of input as features                                    |
| [[Ridge Regression]]           | Linear + L2 penalty — shrinks weights toward zero                                       |
| [[Lasso Regression]]           | Linear + L1 penalty — drives some weights to exactly zero                               |
| Elastic net                    | Combines L1 and L2 penalties — sparsity with stability                                  |
| [[Logistic Regression]]        | Models P(y=1 \| x) via sigmoid — used for classification despite the name               |
| Bayesian                       | Places a prior over weights — outputs a distribution over predictions                   |
| Stepwise                       | Automatically selects features by adding or removing them based on statistical criteria |
| Quantile                       | Predicts a specific quantile of y (e.g. median) instead of the mean                     |
| Poisson                        | Models count data where y is a non-negative integer — e.g. number of events             |
| Support vector regression      | Fits a function within a margin of tolerance using kernel methods                       |
| Decision tree regression       | Predicts by partitioning input space into regions with constant output                  |
 SVR and decision tree regression are non-parametric and don't assume a fixed functional form, which puts them in a different category from the rest.
## Advantages
1. It's interpretable (especially linear regression as weights have direct meaning). 
2. It's computational cheap as it has a [[Closed Form Solution]]. 
3. It theoretically well understood.
4. Works well with small data as the hypothesis class is restricted, it doesn't need large datasets to generalize.
## Limitations
1. Cannot extrapolate (predictions far outside the range of training data) reliably.
2. Assumes a static data generating process.
3. Highly sensitive to the choice of loss.
4. Can never capture the full distribution of y.
5. [[Correlation vs Causation]] — regression learns statistical associations, not casual relationships.
## Related Concepts
1. [[Data Generating Process]]
2. [[Squared Error Loss]]
## Todo
- [ ] Check out squared error loss and its properties
- [ ] squared error vs squared error loss
- [ ] Proof of conditional expectation for minimize squared error loss.