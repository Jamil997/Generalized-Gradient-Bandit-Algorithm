
# Generalized Gradient Bandit Algorithm (GGBA)

We aim to investigate how different smooth functions \(\psi\) (variants of Smooth ReLU) affect the performance of the Gradient Bandit algorithm on multi-armed bandits for various learning rates \(\alpha\). The goal is to identify which \(\alpha\) balances exploration and exploitation most effectively, and to see how \(\ln^n(1+e^x)\) compares with the standard \(e^x\) approach.

## Algorithm Description

Given **k** unknown reward distributions \( P_1, P_2, \ldots, P_k \) with true values \( q_*(a) = \mathbb{E}_{X \sim P_a}[X] \), the algorithm updates preferences \( H_t = [H_t(a)]_{a=1}^k \) via:

\[
H_{t+1} = H_t + \alpha \, g_t,
\]

where

\[
g_t(a) = (R_t - \bar{R}_t) \cdot \frac{\psi'(H_t(a))}{\psi(H_t(a))} \left( \mathbb{1}[A_t = a] - \pi_t(a) \right),
\]

and 

\[
\pi_t(a) \propto \psi(H_t(a)).
\]

For \( \psi(x) = e^x \), this reduces to the standard Gradient Bandit algorithm.

In our project, we replace \( e^x \) with alternative smooth functions:
1. \( \psi(x) = \ln(1 + e^x) \),
2. \( \psi(x) = \ln^2(1 + e^x) \),
3. \( \psi(x) = \ln^3(1 + e^x) \).

---

## Stages of the Project

### 1. Comparing Smooth Functions
- We compared the growth curves for \( e^x \), \( \ln(1 + e^x) \), \( \ln^2(1 + e^x) \), and \( \ln^3(1 + e^x) \).
- Higher powers of \( \ln(1 + e^x) \) steepen the growth rate, making the behavior closer to \( e^x \).

### 2. Running the Algorithm
- The algorithm was run for each \( \psi \) function over **10-armed bandits**.
- Learning rates \( \alpha \) used: \{1, 1/2, 1/4, 1/8, 1/16, 1/32\}.
- Plots generated:
  1. **% Optimal actions vs. Time steps**
  2. **Average reward vs. Time steps**
- Results reveal that intermediate \( \alpha \) (e.g., \( 1/4 \) or \( 1/8 \)) balances exploration and exploitation best.

### 3. Consolidated Results
- **Figures 4 and 5** show:
  - Average % of optimal actions.
  - Average reward over all time steps, plotted against \( \alpha \).
- Observations:
  - Smaller \( \alpha \) under-learns.
  - Larger \( \alpha \) destabilizes.
  - Best performance is typically achieved around \( \alpha = 1/4 \) or \( \alpha = 1/8 \).

---

## Conclusion
- \( \alpha = 1/4 \) achieves the **highest average reward** and **highest % of optimal actions**.
- Different \( \psi \) functions (\( \ln(1 + e^x) \), \( \ln^2(1 + e^x) \), \( \ln^3(1 + e^x) \)) perform similarly in overall behavior but differ slightly in convergence speed and final performance.
