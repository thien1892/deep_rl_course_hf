# Deep Reinforcement Learning Course

Link: https://huggingface.co/deep-rl-course/

## 1. What to expect?
**In this course, you will:**

>📖 Study Deep Reinforcement Learning in theory and practice.

>🧑‍💻 Learn to use famous Deep RL libraries such as Stable Baselines3, RL Baselines3 Zoo, Sample Factory and CleanRL.

>🤖 Train agents in unique environments such as SnowballFight, Huggy the Doggo 🐶, VizDoom (Doom) and classical ones such as Space Invaders, PyBullet and more.

>💾 Share your trained agents with one line of code to the Hub and also download powerful agents from the community.

>🏆 Participate in challenges where you will evaluate your agents against other teams. You’ll also get to play against the agents you’ll train.

>And more!

>At the end of this course, you’ll get a solid foundation from the basics to the SOTA (state-of-the-art) methods.

## Lecture:

### Unit1: [Introduction to Deep Reinforcement Learning ](https://github.com/thien1892/deep_rl_course_hf/blob/master/Unit1_Introduction%20to%20Deep%20Reinforcement%20Learning.md)
#### 1.1. Summary
- Reinforcement Learning is a computational approach of learning from action. We build an agent that learns from the environment by interacting with it through trial and error and receiving rewards (negative or positive) as feedback.

- The goal of any RL agent is to maximize its expected cumulative reward (also called expected return) because RL is based on the reward hypothesis, which is that all goals can be described as the maximization of the expected cumulative reward.

- The RL process is a loop that outputs a sequence of state, action, reward and next state.

- To calculate the expected cumulative reward (expected return), we discount the rewards: the rewards that come sooner (at the beginning of the game) are more probable to happen since they are more predictable than the long term future reward.

- To solve an RL problem, you want to find an optimal policy. The policy is the “brain” of your agent, which will tell us what action to take given a state. The optimal policy is the one which gives you the actions that maximize the expected return.

- There are two ways to find your optimal policy:

    - By training your policy directly: policy-based methods.
    - By training a value function that tells us the expected return the agent will get at each state and use this function to define our policy: value-based methods.

- Finally, we speak about Deep RL because we introduce deep neural networks to estimate the action to take (policy-based) or to estimate the value of a state (value-based) hence the name “deep”.

#### 1.2. Glossary
- **Markov Property**: It implies that the action taken by our agent is conditional solely on the present state and independent of the past states and actions.
- **Observations/State**: 
    - **State**: Complete description of the state of the world.
    - **Observation**: Partial description of the state of the environment/world.
- **Actions**:
    - **Discrete Actions**: Finite number of actions, such as left, right, up, and down.
    - **Continuous Actions**: Infinite possibility of actions; for example, in the case of self-driving cars, the driving scenario has an infinite possibility of actions occurring.
- **Rewards and Discounting**:
    - **Rewards**: Fundamental factor in RL. Tells the agent whether the action taken is good/bad.
    - RL algorithms are focused on maximizing the **cumulative reward.**
    - **Reward Hypothesis**: RL problems can be formulated as a maximisation of (cumulative) return.
    - **Discounting** is performed because rewards obtained at the start are more likely to happen as they are more predictable than long-term rewards.
- **Tasks**:
    - **Episodic**: Has a starting point and an ending point.
    - **Continuous**: Has a starting point but no ending point.
- **Exploration v/s Exploitation Trade-Off**:
    - **Exploration**: It’s all about exploring the environment by trying random actions and receiving feedback/returns/rewards from the environment.
    - **Exploitation**: It’s about exploiting what we know about the environment to gain maximum rewards.
    - **Exploration-Exploitation Trade-Off**: It balances how much we want to explore the environment and how much we want to exploit what we know about the environment.
- **Policy**:
    - **Policy**: It is called the agent’s brain. It tells us what action to take, given the state.
    - **Optimal Policy**: Policy that maximizes the expected return when an agent acts according to it. It is learned through training.
- **Policy-based Methods**:
    - An approach to solving RL problems.
    - In this method, the Policy is learned directly.
    - Will map each state to the best corresponding action at that state. Or a probability distribution over the set of possible actions at that state.
- **Value-based Methods**:
    - Another approach to solving RL problems.
    - Here, instead of training a policy, we train a value function that maps each state to the expected value of being in that state.