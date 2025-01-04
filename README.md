# Generalized Gradient Bandit Algorithm (GGBA)

The Generalized Gradient Bandit Algorithm extends the Gradient Bandit algorithm to include a variety of smooth functions for preference updating.

## Algorithm Description

Given **k** unknown reward distributions \( P₁, P₂, …, Pₖ \) with true values \( qₐ = E[X \sim Pₐ] \), the algorithm updates preferences \( Hₜ = [Hₜ(a)] \) via:

Hₜ₊₁ = Hₜ + αgₜ

where

gₜ(a) = (Rₜ − R̄ₜ) ⋅ ψ′(Hₜ(a)) / ψ(Hₜ(a)) ⋅ (1[Aₜ = a] − πₜ(a))

and

πₜ(a) ∝ ψ(Hₜ(a)).

For **ψ(x) = exp(x)**, this reduces to the standard Gradient Bandit algorithm. In our project, we replace **exp(x)** with the following smooth functions:
1. ψ(x) = ln(1 + exp(x))
2. ψ(x) = ln²(1 + exp(x))
3. ψ(x) = ln³(1 + exp(x))

---

## Stages of the Project

### 1. Comparing Smooth Functions
- We compared the growth curves for exp(x), ln(1 + exp(x)), ln²(1 + exp(x)), and ln³(1 + exp(x)).
- Higher powers of ln(1 + exp(x)) steepen the growth rate, making the behavior closer to exp(x).

### 2. Running the Algorithm
- The algorithm was run for each ψ function over **10-armed bandits**.
- Learning rates (α) used: {1, 1/2, 1/4, 1/8, 1/16, 1/32}.
- Results include:
  1. **% Optimal actions vs. Time steps**
  2. **Average reward vs. Time steps**
- Observations: Intermediate α values (e.g., 1/4 or 1/8) balance exploration and exploitation best.

### 3. Consolidated Results
- Smaller α values under-learn.
- Larger α values destabilize the algorithm.
- Best performance is typically achieved at α = 1/4 or α = 1/8.

---

## Conclusion
- α = 1/4 achieves the **highest average reward** and **highest % of optimal actions**.
- ψ(x) functions (ln(1 + exp(x)), ln²(1 + exp(x)), ln³(1 + exp(x))) behave similarly but differ slightly in convergence speed and final performance.

