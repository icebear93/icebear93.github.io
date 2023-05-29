---
layout: single
title:  "Coding Practice 1"
categories: coding


author_profile: false
typora-root-url: ../
---

# What is RL(Reinforcement Learning?)

Reinforcement learning is a type of machine learning where an **agent** learns to make decisions by interacting with its **environment**. It is inspired by how humans learn through trial and error. The agent receives feedback, called **rewards**, based on its **actions**, and its goal is to maximize the total reward it accumulates over time.

Here's a step-by-step breakdown of reinforcement learning:

1. The **agent** observes the current **state** of the **environment**.
2. Based on that state, the agent takes an **action**.
3. The environment responds to the action, transitioning to a new state and providing a **reward** to the agent.
4. The agent learns from this experience and **updates** its knowledge to improve future decision-making.
5. Steps 1-4 repeat until the agent achieves its **goal** or completes a specified number of interactions.

By using a trial-and-error approach, reinforcement learning enables the agent to discover the best actions to take in different situations. Over time, the agent learns to make more effective decisions that lead to higher rewards, allowing it to solve complex problems and optimize its behavior in dynamic environments.



## Dynamic Programming

Dynamic programming is a mathematical optimization technique used to solve problems by breaking them down into smaller overlapping subproblems. It involves solving each subproblem only once and storing the results, which allows for more efficient computations.

In the context of reinforcement learning, dynamic programming plays a crucial role in solving the Bellman equation. The Bellman equation expresses the relationship between the value of a state and the values of its neighboring states. It is a key concept in reinforcement learning, as it helps determine the optimal policy and value function.

Dynamic programming methods, such as value iteration and policy iteration, are important in reinforcement learning for the following reasons:

1. Optimal policy determination: Dynamic programming provides a systematic way to compute the optimal policy by solving the Bellman equation. It allows the agent to determine the best actions to take in different states, leading to an optimal decision-making strategy.
2. Value function estimation: Dynamic programming methods enable the estimation of the value function, which represents the expected cumulative rewards an agent can achieve from a particular state. Accurate value function estimation is crucial for understanding the quality of different states and guiding the agent's decision-making process.
3. Efficient computation: Dynamic programming helps in solving complex problems by decomposing them into smaller subproblems. By solving each subproblem once and storing the results, redundant computations are avoided, leading to more efficient and faster computations.
4. Convergence guarantee: Dynamic programming methods, such as value iteration and policy iteration, are proven to converge to the optimal solution under certain conditions. This convergence property ensures that the agent can reach an optimal policy and value function given enough iterations.

Overall, dynamic programming provides a solid foundation for solving reinforcement learning problems by breaking them down into manageable subproblems and efficiently computing optimal policies and value functions. It is an essential tool for understanding and optimizing an agent's decision-making process in complex environments.



## Q-Learning

<p align='center'><img src="/images/2023-05-25- Reinforcement Learning/Pasted Graphic 1.png" alt="Pasted Graphic 1" style="zoom: 33%;" /></p>

<p align='center'><img src="/images/2023-05-25- Reinforcement Learning/Pasted Graphic 2.png" alt="Pasted Graphic 2" style="zoom: 34.5%;" /></p>

Q-learning is a popular and fundamental algorithm in reinforcement learning used to find the optimal policy for an agent in an environment. It falls under the category of model-free learning, meaning it doesn't require prior knowledge about the environment's dynamics.

In Q-learning, the agent learns a Q-value function, often referred to as the Q-function or Q-table. The Q-function estimates the expected cumulative rewards the agent can achieve by taking a particular action in a specific state.

Here's how Q-learning works:

1. Initialization: The agent initializes a Q-table that represents the values for each state-action pair. Initially, these values are arbitrary or set to zero.

2. Exploration and Exploitation: The agent chooses an action to take in the current state based on an exploration-exploitation strategy. It balances between exploring new actions and exploiting the current knowledge.

3. Action and Reward: The agent takes the chosen action, and the environment transitions to a new state. The agent receives a reward for this action.

4. Updating Q-values: The agent updates the Q-value for the previous state-action pair based on the observed reward and the maximum Q-value achievable from the next state. This update is done using the Q-learning update equation:

   Q(s, a) = Q(s, a) + α * (r + γ * max(Q(s', a')) - Q(s, a))

   - Q(s, a) represents the Q-value of state s and action a.
   - α (alpha) is the learning rate, controlling the impact of the update on the Q-value.
   - r is the observed reward for taking action a in state s.
   - γ (gamma) is the discount factor, determining the importance of future rewards compared to immediate rewards.
   - max(Q(s', a')) represents the maximum Q-value achievable from the next state s' by selecting the best action a' based on the current Q-values.

5. Repeat: Steps 2-4 are repeated until the agent reaches a terminal state or a specified number of iterations.

As the agent continues to interact with the environment and update its Q-values, the Q-table gradually converges towards the optimal Q-values. Once the learning process is complete, the agent can use the learned Q-table to determine the best action to take in any given state, leading to an optimal policy.

Q-learning is a powerful and versatile algorithm that has been successfully applied to various problems, including robotics, game-playing agents, and autonomous systems.

However, the Q-table tends to require a large amount of storage capacity, making it impractical for many applications. To address this issue, neural networks (NN) are commonly employed to approach reinforcement learning using the same underlying principles. One prominent approach is Deep Q-Networks (DQN), which leverages neural networks to approximate Q-values and overcome the limitations of the Q-table.



## Deep Q-Networks (DQN)

DQN is a reinforcement learning algorithm that combines deep neural networks with the Q-learning algorithm. Instead of storing Q-values in a table, DQN utilizes a neural network to estimate the Q-values for different state-action pairs. The neural network takes the state as input and outputs a Q-value for each possible action.

DQN introduces two main techniques to improve training stability and sample efficiency: experience replay and a target network. Experience replay involves storing agent experiences (consisting of state, action, reward, and next state) in a memory buffer. During training, a batch of experiences is randomly sampled from the buffer to break the temporal correlations between consecutive experiences. This helps to alleviate the issues caused by the sequential nature of the data and leads to more efficient learning.

The target network is a separate neural network that is periodically updated with the weights of the main network. The main network, also known as the online network, is used to select actions during training. By periodically updating the target network, which is used to compute the target Q-values, DQN stabilizes the learning process. This is because it reduces the potential for feedback loops and prevents the network from chasing a moving target.

Through these techniques, DQN can effectively learn and approximate the Q-values for large and complex state-action spaces. It can handle high-dimensional inputs, making it suitable for tasks such as image-based or continuous control problems. However, training DQN can still be computationally intensive and may require substantial computational resources and time.

---

# So what is Reinforcement Learning again?

Reinforcement learning is a type of machine learning that mimics how humans learn from their experiences. Just like a child learns to ride a bike by trying different actions and receiving feedback, an agent in reinforcement learning learns by interacting with its environment and receiving rewards.

Here's how it works:

1. The agent: Imagine the agent as a learner or a decision-maker. It's placed in an environment and its goal is to learn how to make the best decisions to maximize its rewards.
2. The environment: The environment is where the agent operates. It could be a simulated world or even a real-world scenario. The agent interacts with the environment by observing its current state and taking actions.
3. States: The state represents the current situation or condition of the environment. It could include information like the position of objects, the agent's location, or any relevant data that describes the context.
4. Actions: The agent takes actions based on the observed state. These actions can be a wide range of choices, such as moving in a particular direction, making a decision, or selecting from a set of available options.
5. Rewards: After the agent takes an action, the environment provides feedback in the form of rewards. Rewards indicate how good or bad the action was in achieving the agent's goal. The agent's objective is to accumulate as much reward as possible over time.
6. Learning: The agent uses a learning algorithm to analyze the observed states, actions, and rewards. It aims to understand the relationship between them to improve its decision-making strategy. This process involves trial and error, as the agent explores different actions and learns from their outcomes.
7. Policy: A policy is the strategy the agent employs to determine which actions to take in a given state. Reinforcement learning algorithms aim to optimize the agent's policy so that it selects actions that lead to higher rewards.
8. Exploration and Exploitation: During learning, the agent needs to balance exploration and exploitation. Exploration involves trying out new actions to discover potentially better strategies. Exploitation involves leveraging the agent's current knowledge to select actions that are known to be good. Striking the right balance is crucial for effective learning.
9. Iteration: The agent repeats this process over multiple iterations or episodes. It learns from its experiences, updates its knowledge, and gradually improves its decision-making abilities.

Through this iterative process of interaction, feedback, and learning, reinforcement learning enables the agent to develop intelligent behavior, make optimal decisions, and adapt to different environments.



---

# Reference

* [MIT Deep Learning lectures](https://deeplearning.mit.edu){:target='_blank'}



