# Uninformed Search Algorithms

---

## Breadth-first search

Root node is expanded first, then all the successors of the root node are expanded, then their successors are expanded, and so on. In general, all the nodes are expanded at a given depth in the search tree before any nodes at the next level are expanded.

![[Pasted image 20220306162622.png]]

- The ==shallowest unexpanded== node is chosen for expansion, it uses a **FIFO** queue for the frontier.
	- New nodes go to the back of the queue, and old nodes, which are (by definition) shallower than the new ones, get expanded first.
	- The **goal test** is applied to every node at the moment of generation, not when its chosen for expansion, this will result in a smaller time complexity.
- Discards nodes which have already been visited 

### Rating

- It is complete, if the shallowest goal node is at some finite depth $d$, _BFS_ will eventually find it after generating all shallower nodes
- The shallowest goal node is not necessarily the optimal one
- Exponential time complexity: $O(b^d)$
- Exponential space complexity: $O(b^d)$

### Implementation

![[Pasted image 20220309102207.png]]

---

## Uniform cost

Breadth-first search is optimal when any action has the same cost, instead of expanding the shallowest node, **uniform cost search** expands the node _n_ with the lowest path cost $g(n)$. The frontier is stored as a priority queue ordered by $g$.

- The goal test is applied to a node when it is selected for expansion, the logic behind this is that said node might be on a sub-optimal path to the end goal, in other words, this type of testing helps find a better node in the frontier.

### Rating

- It is sort of optimal in general
- Uniform cost search expands nodes in order of their optimal path cost. Hence, the first **goal node** that is selected for expansion **must** be the optimal solution.
- It can get stuck on infinite loops. If it finds a sequence of actions with no cost at all, uniform cost search will just keep looping through  those actions. The completeness of uniform cost search can only be guaranteed if every action has a cost higher than some small positive constant $\epsilon$
- Since _uniform cost search_ is guided by path-costs rather than depths, its complexity cannot be easily determined solely by parameters $b$, $d$ and $m$.
	- First, lets call $C^{*}$ the cost of the optimal solution, and that every action costs at least $\epsilon$. Then, the algorithm's worst case scenario would be $O\left(b^{1 + \lfloor C^{*} / \epsilon \rfloor}\right)$
	- Uniform cost search might explore large trees of small steps before considering trees with big steps that could be useful.
	- If all costs are the same, uniform cost is similar to breadth first, the main difference is that breadth first will stop as soon as it generates a goal, but uniform cost will examine all the nodes on the lookout for a better path.

### Implementation

![[Pasted image 20220309102415.png]]

---

## Depth-first search

It always expands the deepest node in the current frontier of the search tree. The search proceeds immediately to the deepest level of the search tree, where the nodes have no successors. As those nodes are expanded, they are dropped from the frontier, so then, the search _backs up_ to the next deepest nodes that still has unexplored successors.

- It uses a **LIFO** queue, the most recently generated node is chosen for expansion
- It can be implemented with graph-search in mind, but it's also common to implement it with a recursive function that calls itself on each of its children

![[Pasted image 20220310090639.png]]

### Rating

It depends upon the version of search the algorithm is using:
- For graph search:
	- It's time complexity is bounded by the size of the state space, $O(b^{d})$
	- Space complexity does not improve from breadth first search
- For tree search:
	- It might generate all of the $O(b^{m})$ nodes in the tree, where $m$ is the maximum depth of any node. $m$ is much larger than $d$, and it's infinite if the tree is unbounded
	- Memory usage decreases tremendously. It needs to store only a single path from the root to a leaf node, along with the remaining unexpanded sibling nodes for each node on the path
	- For a state space with a branching factor $b$ and maximum depth $m$, depth first search requires to store only $O(bm)$ nodes

---

## Depth-limited search

The failure of depth first search on infinite state spaces can be _"solved"_ by supplying the algorithm a depth limit $l$. By depth limit we mean that nodes at a depth level of $l$ will be treated as nodes with no successors.

### Caveats

- The introduction of a depth limit makes depth limit search incomplete if the value of $l$ is smaller than $d$ (depth of the shallowest goal node).
- It will also be non-optimal if $l$ is greater than $d$
- The value of $l$ is hard to determine, sometimes knowledge of the problem might be the only way to make an _educated guess_
- The ==diameter== of the state space is the minimum number of actions needed to reach any node. Needs further investigation

### Rating

- Time complexity: $O(b^{l})$
- Space complexity: $O(bl)$

### Implementation

![[Pasted image 20220310093056.png]]

---

## Iterative deepening depth-first search

General strategy used in combination with depth first tree search that finds the best depth limit $l$. It achieves this by gradually increasing the depth limit

![[Pasted image 20220310093736.png]]

### Rating
- It combines the benefits of depth first and breadth first search. 
	- Like depth-first its memory requirements stay at a low $O(bd)$, and like breadth-first, it is complete when the branching factor $b$ is finite, and optimal when the path is a non decreasing function of the depth of the node
- At first glance, iterative deepening seems wasteful since it has to generate the same states multiple times, but keep in mind that most of the nodes of any graph are located in the bottom levels, in other words, we can give ourselves the luxury of generating the starting nodes multiple times

### Implementation

![[Pasted image 20220310093653.png]]

---

## Bidirectional search

Runs 2 simulation searches, one forward from the initial state and another backward from the goal state, hoping that the 2 encounter in the middle. The motivation is that $b^{\frac{d}{2}} + b^{\frac{d}{2}}$ is much less than $b^{d}$.

- It replaces the goal test to check if the 2 frontiers match, if they do, the problem is solved, the inconvenience here is that the solution found might not be optimal at all
- It requires a way to calculate predecessors; going forwards from the initial state on the lookout for the next node is easy, but, can you always determine what the previous state was given a particular state? If you can, then you can use bidirectional search
- If the goal is more of an abstract description, like the n-queen problem, bidirectional search is pretty hard to use

### Rating

- Time complexity: $O(b^{\frac{d}{2}})$
- Space complexity: $O(b^{\frac{d}{2}})$

---

## Comparing uninformed search algorithms

![[Pasted image 20220310101609.png]]