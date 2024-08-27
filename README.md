# Comparison of Bandit Algorithms

## Overview
This repository includes implementations and performance analyses of several bandit algorithms. The study covers:

[1. Explore-then-Commit](#1-explore-then-commit)

[2. Upper Confidence Bound (UCB)](#2-upper-confidence-bound-ucb)

[3. Thompson Sampling](#3-thompson-sampling)

[4. Linear UCB (LinUCB)](#4-linear-ucb-linucb)

[5. Linear Thompson Sampling (LinTS)](#5-linear-thompson-sampling-lints)

[6. Generalized Linear Model Bandit (GLM)](#6-generalized-linear-model-glm-bandit-non-linear-bandit)


## 1. Explore-then-Commit
### Result
<div align="center">
  
| Hyperparameter (m) | Cumulative Regret |
|:------------------:|:-----------------:|
|         10         |      1001.40      |
|         20         |       214.90      |
|         30         |       334.02      |

<img src="https://github.com/kapshaul/OnlinLearning/blob/bandits-comparison-analysis/figures/fig1.png" alt="Explore then Commit accumulated regret" width="800">

**Figure 1**: Explore then Commit accumulated regret

</div>

## 2. Upper Confidence Bound (UCB)
### Reward Estimation + Confidence Bound
$$
\text{UCB} = \hat u_{t-1,i} + \sqrt{\frac{2 \ln t}{S_{t-1,i}}}
$$

### Result
<div align="center">
  
| Hyperparameter (α) | Cumulative Regret |
|:------------------:|:-----------------:|
| 0.1                | 256.50            |
| 0.5                | 977.03            |
| 1.0                | 1906.65           |

<img src="https://github.com/kapshaul/OnlinLearning/blob/bandits-comparison-analysis/figures/fig2.png" alt="UCB Bandit accumulated regret" width="800">

**Figure 2**: UCB Bandit accumulated regret

</div>

## 3. Thompson Sampling
### Posterior Distribution

$$
N \sim \left( \hat u_{t-1,i}, \frac{1}{S_{t-1,i} + 1} \right)
$$

### Result

<div align="center">

| Cumulative Regret |
|:------------------:|
|  100              |

<img src="https://github.com/kapshaul/OnlinLearning/blob/bandits-comparison-analysis/figures/fig3.png" alt="Thompson Sampling accumulated regret" width="400">

**Figure 3**: Thompson Sampling accumulated regret

</div>

## 4. Linear UCB (LinUCB)
### Parameter Estimation

$$
\hat \theta_{t+1} = A^{-1}_ {t+1} b_{t+1}
$$

### Reward Estimation + Confidence Bound

$$
\text{UCB} = x^T \hat \theta_t + \alpha \sqrt{x^T A^{-1} x}
$$

### Result

<div align="center">

| Hyperparameter (α) | Cumulative Regret |
|:------------------:|:-----------------:|
| 0.5                | 24.43             |
| 1.5                | 177.89            |
| 2.5                | 487.73            |

<img src="https://github.com/kapshaul/OnlinLearning/blob/bandits-comparison-analysis/figures/fig4.png" alt="Linear UCB accumulated regret" width="800">
<img src="https://github.com/kapshaul/OnlinLearning/blob/bandits-comparison-analysis/figures/fig5.png" alt="Linear UCB estimation error" width="800">

**Figure 4**: Linear UCB accumulated regret and estimation error

</div>

## 5. Linear Thompson Sampling (LinTS)
### Posterior Distribution
$$
N \sim (\hat{\theta}_t, A^{-1}_t)
$$

### Result

<div align="center">

| Cumulative Regret |
|:------------------:|
| 1098.24            |

<img src="https://github.com/kapshaul/OnlinLearning/blob/bandits-comparison-analysis/figures/fig6.png" alt="Linear Thompson Sampling accumulated regret" width="400">
<img src="https://github.com/kapshaul/OnlinLearning/blob/bandits-comparison-analysis/figures/fig7.png" alt="Linear Thompson Sampling estimation error" width="400">

**Figure 5**: Linear Thompson Sampling accumulated regret and estimation error

</div>

## 6. Generalized Linear Model (GLM) Bandit: Non-linear Bandit
### Modified Non-LinearReward Function For Testing

$$
R = (x^T \theta)^2 + \epsilon, \text{ where } \epsilon \sim N(\mu, \sigma^2)
$$

### GLM Parameter Estimation (MLE)

$$
\hat \theta_{t+1} = \max_{\theta} P(r|\theta) = A^{-1}_ {t+1} b_{t+1}
$$

### GLM UCB

$$
UCB_{GLM} = f(x^T \hat \theta_t) + \alpha \sqrt{x^T A^{-1} x} = (x^T \hat \theta_t)^2 + \alpha \sqrt{x^T A^{-1} x}
$$

### Result

<div align="center">

| Hyperparameter (α) | Cumulative Regret |
|:------------------:|:-----------------:|
| 0.1                | 62.16             |
| 0.5                | 727.63            |
| 1.5                | 5948.48           |

<img src="https://github.com/kapshaul/OnlinLearning/blob/bandits-comparison-analysis/figures/fig8.png" alt="GLM-UCB accumulated regret" width="800">
<img src="https://github.com/kapshaul/OnlinLearning/blob/bandits-comparison-analysis/figures/fig9.png" alt="GLM-UCB estimation error" width="800">

**Figure 5**: GLM-UCB accumulated regret and estimation error

</div>
