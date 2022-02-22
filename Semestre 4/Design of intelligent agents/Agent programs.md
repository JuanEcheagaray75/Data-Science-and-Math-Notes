# Agent programs
---

In increasing flexibility/generality (and complexity):
1. [[#Simple reflex|Simple reflex]]
1. [[#Model-based|Model-based]]
1. [[#Goal-based|Goal-based]]
1. [[#Utility-based|Utility-based]]
1. [[#Learning agents|Learning agents]]

## Simple reflex

This type of agent selects its next action based solely on its current percept, it does not consider the rest of the percept history. This simple reflex gets encoded into _condition-action_ rules, for example: If when driving you see that the car in front is braking (through the brake lights or the change of distance between the vehicles), then, you must also brake.

![[Pasted image 20220219154305.png]]

One benefit/downside of simple reflex agents is their simplicity. They require a fairly straight-forward implementation, but this simplicity comes at the cost of the agent's intelligence. As soon as the environment becomes **partially observable** the original set of _condition-action_ rules becomes useless. 

For example: The rule _if the car in front is braking then initiate breaking_ only works if the agent can always determine that the car in front is braking. What will the agent do if the brake lights of the front car are located on a weird pattern or location?

When a simple reflex agent enters an infinite loop, _randomization_ might be its only way out. If we give the agent the ability to randomize its actions the infinite loop may be broken. Sometimes a randomized simple reflex agent might outperform a deterministic simple agent.

Simple reflex agents can only have a good performance if their next action can be determined based solely on their current percept, ie, if the environment is _fully observable_.

---

## Model-based

When an agent is placed in a partially observable environment, often the best way to handle its course of actions is to keep track of the environment. What do I mean by keeping track? The agent should keep an _internal state_ based upon its percept history, this will reflect at least some of the information the agent has no access to.

The act of updating the internal state retrieving:
- Information about how the world evolves independently of the agent
- Information about how the agent's own actions affect the world

This is what we call a _model_, agents that use a model are called _model-based_ agents.

![[Pasted image 20220219162826.png]]

Determining what the environment is like at a certain time and location on a partially observed environment is practically impossible for an agent, therefore, "what the world _is_ like now" is often just the best guess the agent can produce with the available data.

Uncertainty about the current state of the environment must not stop a model based agent from acting.

> This agent also has a set of condition-action rules

---

## Goal-based

Sometimes reacting to an environment and following a set of predetermined hard-coded rules is not enough to determine the best course of action, it's in those cases when a specific **goal** must be given to an agent to make him get to a desirable state.

Goal-based agents combine their model of their environment with their end goal to determine the actions that achieve said goal (so far we have not talked about how the goal is achieved).

Goal-based actions can sometimes be pretty straight-forward, when the goal is achieved through a single action. But goal-based agents shine the most when they have to consider different sequences of actions that satisfy their end goal. This type of decision making is different from the hard-coded rule set defined before, because goal-based agents look into the future.

![[Pasted image 20220220124725.png]]

---

## Utility-based

Useful when the agent must determine the best course of action, we want to achieve a certain goal, but we would like it to be achieved in the best possible manner.

Having a goal is nice, but goals are just a way for the agent to determine if it's on a _happy_ or _unhappy_ state. Since we want to get the best way to perform a task, a more specific measure of how good certain states are is needed, here is where **utility** comes in.

The ==utility function== is the agent's performance measure (more or less). If the utility function and the performance measure are in agreement, an agent that chooses the actions that maximize its utility will be rational according to the external performance measure.

An utility-based agent can still make rational decisions where a goal-based agent cannot, for example:
	- When there are conflicting goals, the utility function decides the appropiate tradeoff
	- When there are several goals that the agent can achieve, but there is no certainty of doing so, the utility function can determine a ranking for the goals (using more effort for more important goals?)

![[Pasted image 20220220141536.png]]

---

## Learning agents

Learning allows the agent to operate in initially unknown environments and to become more competent than its initial knowledge alone might allow. Learning agents can be divided into four components:

- Learning element: responsible for making improvements
- Performance element: responsible for selecting external actions
- Critic: determines how well the agent is doing according to a performance standard, and the feedback is used by the **learning element** to modify the **performance element**
- Problem generator: responsible for suggesting actions that will lead to ==new and informative== experiences. If the agent found a way to obtain good performance measures, it will only perform said actions; but if you give the agent the ability to choose suboptimal actions in the short run, it might find much better actions for the long run.

### Automated taxi example

> The performance element consists of whatever collection of knowledge and procedures the taxi has for selecting its driving actions. The taxi goes out on the road and drives, using this performance element. The critic observes the world and passes information along to the learning element. For example, after the taxi makes a quick left turn across three lanes of traffic, the critic observes the shocking language used by other drivers. From this experience, the learning element is able to formulate a rule saying this was a bad action, and the performance  element is modified by installation of the new rule. The problem generator might identify certain areas of behavior in need of improvement and suggest experiments, such as trying out the brakes on different road surfaces under different conditions.


---

## Extra stuff

In a sense, the performance standard distinguishes part of the incoming percept as a reward (or penalty) that provides direct feedback on the quality of the agent’s behavior.

## Questions

- Page 51-52, concept of internal state
- Preguntarle al profe como es que se resuelven los ejercicios del final del capítulo 2, cuál es el procedimiento y cómo es que debería de ser presentado.
	- En respuesta a esto, me dijo que básicamente se tiene qué resolver como si fuesen demostraciones matemáticas