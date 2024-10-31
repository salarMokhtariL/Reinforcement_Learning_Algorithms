
# Multi-Armed Bandit (MAB) Problem

The Multi-Armed Bandit (MAB) problem is a foundational concept in decision-making, probability, and machine learning. It provides a way to tackle situations where you need to choose between multiple options (or "arms") to maximize rewards, without knowing which one will yield the best results from the start.

## Problem Overview

Imagine a casino with multiple slot machines (the "arms"). Each machine has a different, unknown payout probability, and the goal is to maximize your reward by strategically deciding which machine to play. However, each decision involves a trade-off:
- **Exploration**: Trying new machines to discover their rewards.
- **Exploitation**: Using the machine that currently gives the best-known reward to maximize returns.

The key challenge is finding the best balance between these two approaches.

## Key Concepts

- **Exploration vs. Exploitation**: 
  - **Exploration** involves testing different arms to gather information.
  - **Exploitation** involves using the arm with the highest known reward to maximize returns.
- **Regret**: The difference between the reward from always picking the best arm and the actual reward received. Good strategies minimize regret over time.

## Strategies

### 1. Epsilon-Greedy
   - With probability \\( \\epsilon \\), select an arm randomly (explore).
   - With probability \\( 1 - \\epsilon \\), select the arm with the highest estimated reward (exploit).
   - **Example**: Choose a random machine 10% of the time and the best-known machine 90% of the time.

### 2. Upper Confidence Bound (UCB)
   - This approach balances current reward estimates with the number of times each arm has been tried.
   - Encourages choosing less-tested arms when their payout is still uncertain.

### 3. Thompson Sampling
   - A probability-based method where each arm has a reward distribution that gets updated with each pull.
   - Naturally balances exploration and exploitation by choosing arms based on the probability of them having the highest reward.

## Applications

The MAB problem has various applications across fields:
- **Online Advertising**: Choosing which ad to display to maximize clicks or engagement.
- **Product Recommendations**: Selecting products or content that will interest the user the most.
- **A/B Testing**: Running controlled tests while minimizing losses from suboptimal choices.

## Getting Started

### Requirements
- Python 3.7+
- Libraries: `numpy`, `scipy` (if using specific sampling methods), `matplotlib` (for plotting results)

### Usage
```python
# Example code to run an epsilon-greedy MAB strategy

from mab import EpsilonGreedyBandit

# Initialize bandit with an epsilon value of 0.1
bandit = EpsilonGreedyBandit(epsilon=0.1)

# Run trials
rewards = bandit.run_trials(num_trials=1000)
