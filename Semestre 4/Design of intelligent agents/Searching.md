# Searching agents
---

[[Uninformed Search Algorithms]]
[[Informed Search Algorithms]]

A search algorithm takes a problem as input, and returns a solution in the form of a sequence of actions

---

## Problem solving performance

1. **Completeness**: is the algorithm guaranteed to find a solution when there is one?
2. **Optimality**: Does the strategy find the optimal solution?
3. **Time complexity**: How long does it take to find a solution?
4. **Space complexity**: How much memory is needed to perform the search?

---
## Definition of a problem

A problem can be defined formally by **5** components:
1. The **initial state**: just what it says, the initial state the agent starts in.
2. A **description of the possible actions**: Given a particular state $S$, the function $ACTIONS(S)$ returns the set of actions that can be executed by the agent. Each action is ==applicable== in $S$
3. A **description of what each action does**: formal name is **transition model** since it returns the state which returns from performing action $A$ in state $S$
	- The term **successor** is reserved for any state that can be reached with a single action.
4. The **goal test**: determines whether a given state $S$ is a goal state $S_g$
5. **Path cost**: assigns a numeric cost to each path, see [[#State space|State space]]

---

### State space

The **initial state**, with the **description of the possible actions** and the **transition model** define the ==state space== of the problem. This state space forms a **graph** in which the nodes are states, and the links between nodes are actions, it follows that a _path_ in the state space is a sequence of actions.

---

### Abstraction

- Removing detail from the representation of a problem

> The choice of a good **abstraction** thus involve removing as much detail as possible while retaining validity and ensuring that the abstract actions are easy to carry out

---

### Complexity

It is expressed in terms of 3 quantities:

- $b$, the branching factor, or the maximum number of successors for any node
- $d$, the depth of the shallowest goal node
- $m$, the maximum length of any path in the state space.

To assess the effectiveness of a search algorithm one may use the **search cost** which is often just the time complexity (but can also include a term for memory usage aka. Space complexity) or **total cost**, which is a combination of the search cost and the **path cost** of the solution found.