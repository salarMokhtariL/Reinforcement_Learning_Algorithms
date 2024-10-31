# Multi-Armed Bandit

## Overview

The **Multi-Armed Bandit (MAB)** problem is a key concept in reinforcement learning and decision-making under uncertainty. It models scenarios where an agent must choose from multiple options (or "arms") to maximize cumulative reward over time. This document outlines the MAB problem, its formulation, strategies for solving it, and practical applications.

## Table of Contents

1. [Understanding the Multi-Armed Bandit Problem](#understanding-the-multi-armed-bandit-problem)
   - [Problem Formulation](#problem-formulation)
   - [Regret](#regret)
2. [Strategies for Solving the MAB Problem](#strategies-for-solving-the-mab-problem)
   - [ε-Greedy Algorithm](#ε-greedy-algorithm)
   - [Upper Confidence Bounds (UCB) Algorithm](#upper-confidence-bounds-ucb-algorithm)
   - [Thompson Sampling](#thompson-sampling)
3. [Performance Evaluation](#performance-evaluation)
4. [Applications of the Multi-Armed Bandit Problem](#applications-of-the-multi-armed-bandit-problem)
5. [Conclusion](#conclusion)

## Understanding the Multi-Armed Bandit Problem

The MAB problem can be illustrated using the analogy of a casino with multiple slot machines, each having a different probability of winning. The objective is to maximize winnings over several plays without knowing which machine offers the best odds.

### Problem Formulation

- Let \( k \): the number of arms (slot machines).
- Let \( X_i \): the reward obtained from arm \( i \) during a play.
- Let \( \mu_i \): the average reward of arm \( i \).

The total reward over \( T \) rounds can be expressed as:
```
R(T) = Σ (from t=1 to T) X_{A_t}
```
where \( A_t \) is the arm chosen at time \( t \).

### Regret

Regret quantifies the difference between the rewards obtained and the optimal rewards. It is defined as:
```
R(T) = T * max_i(μ_i) - Σ (from t=1 to T) X_{A_t}
```
The goal is to minimize this regret over time.

## Strategies for Solving the MAB Problem

To effectively address the MAB problem, several strategies are employed to balance exploration and exploitation:

### ε-Greedy Algorithm

The **ε-greedy algorithm** works by:
- Exploring with probability \( \epsilon \) (e.g., 0.1).
- Exploiting with probability \( 1 - \epsilon \).

This simple method allows the agent to try new arms while primarily selecting the best-known arm.

### Upper Confidence Bounds (UCB) Algorithm

The **UCB algorithm** selects arms based on both their estimated rewards and the uncertainty of those estimates, maximizing:
```
UCB_i(t) = Q_i(t) + c * sqrt(ln(t)/T_i(t))
```
This approach encourages exploration of less-frequented arms.

### Thompson Sampling

**Thompson Sampling** uses a Bayesian approach where the agent:
1. Maintains a distribution for each arm's expected reward.
2. Samples from these distributions to choose the arm with the highest expected reward.

This method automatically balances exploration and exploitation.

## Performance Evaluation

The performance of MAB algorithms is typically evaluated using regret. A good algorithm will achieve sublinear regret, indicating improved efficiency in selecting the best arm over time.

## Applications of the Multi-Armed Bandit Problem

MAB is applicable in various domains, including:

- **Online Advertising**: Optimizing ad placements to maximize clicks.
- **Clinical Trials**: Determining the most effective treatments.
- **A/B Testing**: Comparing product variants for better performance.

## Conclusion

The Multi-Armed Bandit problem illustrates the critical balance between exploration and exploitation in reinforcement learning. By leveraging strategies such as the ε-greedy algorithm, UCB, and Thompson Sampling, agents can make informed decisions in uncertain environments. The MAB framework remains vital for optimizing choices in numerous practical applications.
