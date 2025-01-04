# Generalized Gradient Bandit Algorithm (GGBA)

The Generalized Gradient Bandit Algorithm extends the Gradient Bandit approach by incorporating different smooth functions to update preferences more flexibly.

## Objective

The study investigates how different smooth functions, inspired by Smooth ReLU variants, impact the performance of the Gradient Bandit algorithm in multi-armed bandit problems. The focus is on finding the optimal balance between exploration (trying new actions) and exploitation (choosing the best-known action) across various learning rates. The study also compares alternative logarithmic-based functions to the standard exponential function.

## Algorithm Description

The algorithm updates action preferences based on observed rewards and feedback. Traditionally, an exponential function is used to determine action probabilities. This study replaces the exponential function with alternative smoothing methods:

1. A simple logarithmic function.
2. A squared logarithmic function.
3. A cubic logarithmic function.

These alternatives grow more gradually than the exponential function, potentially offering better control over the preference updates.

---

## Stages of the Study

### 1. Comparing Smooth Functions
- The smooth functions were plotted to compare their growth rates.
- Higher-order logarithmic functions exhibit steeper growth curves, behaving more like the exponential function.
- **(Refer to Figure 1 for a detailed comparison of these curves.)**

### 2. Running the Algorithm
- The algorithm was tested on a simulated 10-armed bandit environment.
- Various learning rates, such as 1, 1/2, 1/4, 1/8, 1/16, and 1/32, were evaluated for each smooth function.
- Performance was assessed using two key metrics:
  1. The percentage of optimal actions selected over time.
  2. The average reward obtained over time.
- **(Refer to Figures 2 and 3 for plots of performance trends across time steps.)**

### 3. Consolidated Results
- Smaller learning rates adapted too slowly, leading to underperformance.
- Larger learning rates destabilized the algorithm, causing erratic behavior.
- Intermediate learning rates, particularly 1/4 and 1/8, offered the best balance between exploration and exploitation.
- **(Refer to Figures 4 and 5 for visual summaries of average rewards and optimal action percentages across learning rates.)**

---

## Conclusion
- Learning rates of approximately 1/4 provided the best overall performance, achieving higher average rewards and a greater percentage of optimal actions.
- The alternative smooth functions performed similarly to the standard exponential function but differed slightly in how quickly they converged to the optimal solution and their final performance levels.
- These results suggest that logarithmic smoothing functions are viable alternatives to the exponential approach.

---

## Visual Results

Please refer to the following figures in the project repository for detailed visual results:

- **Figure 1:** Comparison of smooth functions' growth curves.
- **Figure 2:** Performance trends for the percentage of optimal actions over time.
- **Figure 3:** Performance trends for average rewards over time.
- **Figure 4:** Summary of average rewards across learning rates.
- **Figure 5:** Summary of optimal action percentages across learning rates.


