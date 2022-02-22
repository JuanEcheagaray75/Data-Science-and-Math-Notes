# Task environments

## The task environment
- Problems to which rational agents are the solutions
- PEAS: Performance, Environment, Actuators and Sensors, Example:

![[Pasted image 20220220154730.png]]

## Dimensions of the task environment

### Fully observable vs partially observable

If an agent's sensors give it access to the complete state of the environment at each point in time, then the environment is **fully observable**; it is also practically fully observable if the sensors detect all aspects that are relevant to the choice of action, the performance measure determines the relevance of the data to be collected.

If the agent has no sensors, then the task environment is **unobservable** (and no, sometimes agent CAN achieve their goal on those environments)

### Single agent vs multi-agent

As an example, a crossword solver is a single agent, on the other hand, chess is considered to be a multiagent environment (one does not play on its own after all).

How to determine if another entity must be seen as an agent? If the behavior of said entity is best described as maximizing a performance measure that depends on the actions of the agent, then the entity must be seen as an agent.

### Deterministic vs stochastic

If the next state of the environment is completely determined by the current state and the action executed by the agent, then we say the environment is **deterministic**, otherwise, it's **stochastic**.

Stochastic generally implies that uncertainty about outcomes is quantified in terms of probabilities

A **non-deterministic** environment is one in which actions are characterized by their possible outcomes, but no probabilities are attached to them

### Episodic vs sequential

In an **episodic** task environment, the agent's experience is divided into _atomic episodes_. During each episode the agent receives a percept and then performs an action, an **episodic** task environment is said to be when the actions from one episode do not affect the next episodes (they are independent). On the other hand, a **sequential** task environment is one in which the actions from an episode may affect those in the future, like taxi driving.

### Static vs dynamic

If the environment can change while the agent is deliberating, then the environment is **dynamic**, otherwise, it's **static**. For example:
- Taxi driving: dynamic, the environment is continuously asking the agent for a response
- Crossword puzzles: static, the environment remains the same while the agent is choosing a word
- Chess played with a clock: its **semi-dynamic**, the environment does not change while the agent deliberates, but its performance does.

### Discrete vs continuous

Applies to the state of the environment, to the way time is handled, and to the percepts and actions from the agent. Examples:
- Chess has a finite number of states (discrete)
- Chess also has a finite number of possible actions
- Taxi driving is a continuous-state, continuous-time problem
- Taxi driving also has a continuous range of actions, angles for steering, pressure on the brakes and so on

### Known vs unknown

