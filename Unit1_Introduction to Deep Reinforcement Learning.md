# Introduction to Deep Reinforcement Learning

## 1. What is Reinforcement Learning?

- The idea behind Reinforcement Learning is that an agent (an AI) will learn from the environment by interacting with it (through trial and error) and receiving rewards (negative or positive) as feedback for performing actions.
- Learning from interactions with the environment comes from our natural experiences.

>Reinforcement learning is a framework for solving control tasks (also called decision problems) by building agents that learn from the environment by interacting with it through trial and error and receiving rewards (positive or negative) as unique feedback.

## 2. The Reinforcement Learning Framework
### 2.1. **The RL Process**

<img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/RL_process.jpg'>

<img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/RL_process_game.jpg'>

### 2.2. RL loop
- This RL loop outputs a sequence of state, action, reward and next state.

<img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/sars.jpg'>

- The agent’s goal is to maximize its cumulative reward, called the expected return.

### 2.3. The reward hypothesis: the central idea of Reinforcement Learning
>The reward hypothesis: the central idea of Reinforcement Learning
⇒ Why is the goal of the agent to maximize the expected return?

>Because RL is based on the reward hypothesis, which is that all goals can be described as the maximization of the expected return (expected cumulative reward).

>That’s why in Reinforcement Learning, to have the best behavior, we aim to learn to take actions that maximize the expected cumulative reward.

### 2.4. Markov Property
> The Markov Property implies that our agent needs only the current state to decide what action to take and not the history of all the states and actions they took before

### 2.5. Observations/States Space

- Observations/States are the information our agent gets from the environment. In the case of a video game, it can be a frame (a screenshot). In the case of the trading agent, it can be the value of a certain stock, etc.
- There is a differentiation to make between observation and state, however:
    - State **s**: is a complete description of the state of the world (there is no hidden information). In a fully observed environment.

    - Observation **o**: is a partial description of the state. In a partially observed environment.

<img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/obs_space_recap.jpg'>

### 2.6. Action Space
- The Action space is the set of all possible actions in an environment.
- The actions can come from a discrete or continuous space:
    - Discrete space: the number of possible actions is finite.
    - Continuous space: the number of possible actions is infinite.

<img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/action_space.jpg'>

### 2.7. Rewards and the discounting
- The reward is fundamental in RL because it’s the only feedback for the agent. Thanks to it, our agent knows if the action taken was good or not.
- The cumulative reward at each time step t can be written as:
<img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/rewards_1.jpg'>
<img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/rewards_2.jpg'>
- However, in reality, we can’t just add them like that. The rewards that come sooner (at the beginning of the game) are more likely to happen since they are more predictable than the long-term future reward.To discount the rewards, we proceed like this:
    - We define a discount rate called gamma. It must be between 0 and 1. Most of the time between 0.99 and 0.95.
        - The larger the gamma, the smaller the discount. This means our agent cares more about the long-term reward.
        - On the other hand, the smaller the gamma, the bigger the discount. This means our agent cares more about the short term reward
    - Then, each reward will be discounted by gamma to the exponent of the time step. As the time step increases, the cat gets closer to us, so the future reward is less and less likely to happen.

<img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/rewards_4.jpg'>

## 3. Type of tasks
- A task is an instance of a Reinforcement Learning problem. We can have two types of tasks: episodic and continuing.
<img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/tasks.jpg'>

## 4. The Exploration/Exploitation trade-off
- Before looking at the different methods to solve Reinforcement Learning problems, we must cover one more very important topic: the exploration/exploitation trade-off.
    - Exploration is exploring the environment by trying random actions in order to **find more information about the environment.**
    - Exploitation is **exploiting known information to maximize the reward.**
<img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/expexpltradeoff.jpg'>

- If it’s still confusing, think of a real problem: the choice of picking a restaurant:
    - Exploitation: You go every day to the same one that you know is good and take the risk to miss another better restaurant.
    - Exploration: Try restaurants you never went to before, with the risk of having a bad experience but the probable opportunity of a fantastic experience.
<img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/exp_2.jpg'>

## 5. Two main approaches for solving RL problems
- In other terms, how to build an RL agent that can **select the actions that maximize its expected cumulative reward?**
### 5.1. The Policy π: the agent’s brain
- The Policy π is the brain of our Agent, it’s the function that tells us what action to take given the state we are in. So it defines the agent’s behavior at a given time.
<img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/policy_1.jpg'>
- This Policy is the function we want to learn, our goal is to find the optimal policy π*, the policy that maximizes expected return when the agent acts according to it. We find this π* through training.
- There are two approaches to train our agent to find this optimal policy π*:
    - Directly, by teaching the agent to learn which action to take, given the current state: Policy-Based Methods.
    - Indirectly, teach the agent to learn which state is more valuable and then take the action that leads to the more valuable states: Value-Based Methods.

### 5.2. Policy-Based Methods
- In Policy-Based methods, **we learn a policy function directly.**
- This function will define a mapping between each state and the best corresponding action. We can also say that it’ll define **a probability distribution over the set of possible actions at that state**
<img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/policy_2.jpg'>
- We have two types of policies:
    - Deterministic: a policy at a given state **will always return the same action.**
    <img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/policy_3.jpg'>
    <img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/policy_4.jpg'>
    - Stochastic: outputs a probability distribution over actions.
    <img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/policy_5.jpg'>
    - Recap:
    <img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/pbm_1.jpg'>
    <img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/pbm_2.jpg'>

### 5.3. Value-based methods
- In value-based methods, instead of learning a policy function, we learn a value function that maps a state to the expected value of being at that state.
- The value of a state is the expected discounted return the agent can get if it starts in that state, and then act according to our policy.
- “Act according to our policy” just means that our policy is “going to the state with the highest value”.
<img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/value_1.jpg'>
- Here we see that our value function defined value for each possible state.
<img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/value_2.jpg'>
- Recap:
<img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/vbm_1.jpg'>
<img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/vbm_2.jpg'>

## 6. The “Deep” in Reinforcement Learning
<img src = 'https://huggingface.co/datasets/huggingface-deep-rl-course/course-images/resolve/main/en/unit1/deep.jpg'>