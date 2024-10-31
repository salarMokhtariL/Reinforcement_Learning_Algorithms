# Chapter 2: Multi-Armed Bandit

## In this Chapter
- **Fundamentals of the Markov Property**
- **Understanding the Multi-Armed Bandit (MAB) Problem**
- **The Exploration-Exploitation Dilemma**
- **The ε-Greedy Algorithm**
- **Upper Confidence Bounds (UCB) Algorithm**
- **Thompson Sampling Algorithm**

## Aim of this Chapter
The aim of this chapter is to provide a comprehensive understanding of the Multi-Armed Bandit problem as a foundational concept in Reinforcement Learning (RL). We will explore various algorithms designed to navigate the challenges posed by the MAB problem, emphasizing the exploration-exploitation trade-off.

---

### 1. Fundamentals of the Markov Property
The **Markov property** is a foundational concept in stochastic processes that asserts that the future state of a system is independent of its past states given its present state. This can be mathematically expressed as:

$$
P(S_{t+1} | S_t, S_{t-1}, \ldots, S_0) = P(S_{t+1} | S_t)
$$

In the context of the Multi-Armed Bandit problem, this property simplifies decision-making by indicating that the choice of arm at time \( t \) should depend solely on the current estimates of the arms’ rewards, rather than on the history of past selections.

### 2. Understanding the Multi-Armed Bandit (MAB) Problem
The **Multi-Armed Bandit problem** is a classic dilemma faced by a decision-maker who must choose between \( K \) different actions (or arms), each associated with an unknown probability distribution of rewards. The challenge lies in maximizing the cumulative reward over a finite time horizon \( T \).

#### Mathematical Formulation:
Let \( X_{t,k} \) denote the reward received from arm \( k \) at time \( t \). The expected reward for each arm is given by:

$$ 
\mu_k = \mathbb{E}[X_{t,k}] 
$$

The goal is to maximize the total reward over \( T \) trials:

$$ 
R_T = \sum_{t=1}^{T} X_{t, A_t} 
$$

where \( A_t \) is the arm selected at time \( t \).

This problem is often framed as a trade-off between gathering information about the arms (exploration) and leveraging known information to maximize immediate rewards (exploitation).

### 3. The Exploration-Exploitation Dilemma
The **exploration-exploitation dilemma** encapsulates the fundamental challenge in the MAB problem.

- **Exploitation** refers to selecting the arm that currently appears to yield the highest expected reward:

$$ 
A_t = \arg\max_k \hat{\mu}_k 
$$

- **Exploration** involves trying arms that have not been selected frequently enough to gain more reliable estimates of their rewards. 

Finding an optimal balance between these two strategies is critical. Too much exploitation can lead to suboptimal rewards, while excessive exploration can hinder reward accumulation.

### 4. The ε-Greedy Algorithm
The **ε-greedy algorithm** is a simple yet effective strategy to address the exploration-exploitation dilemma.

#### Algorithm Description:
- With probability \( \epsilon \) (where \( 0 < \epsilon < 1 \)), a random arm is chosen:

$$ 
A_t \sim \text{Uniform}(1, K) 
$$

- With probability \( 1 - \epsilon \), the arm with the highest estimated reward is selected:

$$ 
A_t = \arg\max_k \hat{\mu}_k 
$$

The parameter \( \epsilon \) controls the degree of exploration. A smaller \( \epsilon \) favors exploitation, while a larger \( \epsilon \) promotes exploration.

#### Advantages and Disadvantages:
- **Advantages**: The ε-greedy approach is straightforward to implement and understand, making it suitable for various applications.
- **Disadvantages**: Choosing an appropriate \( \epsilon \) can be challenging, and the fixed exploration rate may not adapt well to changing environments.

### 5. Upper Confidence Bounds (UCB) Algorithm
The **UCB algorithm** offers a more sophisticated approach by incorporating uncertainty into the decision-making process. It selects arms based on a confidence interval that balances exploration and exploitation.

#### Mathematical Formulation:
The UCB for arm \( k \) at time \( t \) is defined as:

$$ 
UCB_k(t) = \hat{\mu}_k + \sqrt{\frac{2 \ln t}{n_k}} 
$$

where:
- \( \hat{\mu}_k \) is the empirical mean reward of arm \( k \).
- \( n_k \) is the count of how many times arm \( k \) has been selected.

The term \( \sqrt{\frac{2 \ln t}{n_k}} \) serves as a measure of uncertainty, encouraging selection of less-explored arms.

#### Performance:
The UCB algorithm adapts its exploration dynamically based on the uncertainty associated with each arm's estimated reward, effectively balancing the two competing objectives. It tends to perform well in a variety of scenarios, especially when the rewards are stationary.

### 6. Thompson Sampling Algorithm
**Thompson Sampling** is a Bayesian approach to solving the MAB problem that provides a robust framework for managing uncertainty.

#### Bayesian Model:
Each arm's reward distribution is modeled using a prior, typically a Beta distribution for binary outcomes:

$$ 
\theta_k \sim \text{Beta}(\alpha_k, \beta_k) 
$$

where \( \alpha_k \) and \( \beta_k \) are hyperparameters representing the number of successes and failures, respectively.

#### Sampling Process:
- At each time step \( t \), sample from the posterior distribution of each arm:

$$ 
\theta_k \sim \text{Beta}(\alpha_k, \beta_k) 
$$

- Select the arm with the highest sampled value:

$$ 
A_t = \arg\max_k \theta_k 
$$

#### Updating the Parameters:
After observing the reward \( X_{t,k} \):

$$ 
\begin{cases}
\alpha_k \leftarrow \alpha_k + 1, & \text{if } X_{t,k} = 1 \\
\beta_k \leftarrow \beta_k + 1, & \text{if } X_{t,k} = 0
\end{cases} 
$$

#### Comparison with Other Algorithms:
Thompson Sampling has been shown to outperform ε-greedy and UCB algorithms in many settings, particularly in non-stationary environments, due to its adaptive nature and ability to capture the uncertainty of rewards.

---

### Conclusion
This chapter provided a detailed examination of the Multi-Armed Bandit problem, highlighting its relevance in Reinforcement Learning. We explored various strategies—ε-greedy, UCB, and Thompson Sampling—each offering distinct advantages in addressing the exploration-exploitation trade-off. A thorough understanding of these algorithms lays the groundwork for tackling more complex RL challenges, demonstrating the foundational role of the MAB problem in the broader context of decision-making and learning.
