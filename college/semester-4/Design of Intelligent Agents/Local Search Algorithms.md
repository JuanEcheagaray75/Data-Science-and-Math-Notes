# Local Search Algorithms

---

> Evaluating and modifying one or more current states rather than systematically exploring paths from an initial state. These algorithms are suitable for when the only thing that matters is the **solution state**, not the path taken to reach it.

**Local search** algorithms operate using a single current node and generally move only to neighbors of that node, these paths are not retained. Even though these algorithms are not systematic they have 2 key advantages:

1. They use very little memory
2. Can often find reasonable solutions in large (or infinite) state spaces

Local search algorithms are widely used for _optimization_ problems, for which the aim is to find the best state according to an _objective function_.

In order to understand the possible downsides and caveats of the search algorithms presented here, we must first consider how the _state-space landscape_ might look like:

![[Pasted image 20220317134944.png]]

A landscape has both **location** and **elevation**, if elevation corresponds to cost, then the aim is to find the lowest valley, the **global minimum**, if elevation corresponds to an objective function, then the aim is to find the highest peak, a **global maximum**. A **complete** local search algorithm is guaranteed to always find a goal if one exists, and an **optimal** one is guaranteed to find a global minimum/maximum

---

## Hill Climbing (Gradient descent)

It's simply a loop, that continually moves in the direction of increasing value. It terminates when it reaches a peak, when no neighbors have higher values. The algorithm does not maintain a search tree, so its data structure consists of only the current node, and its objective function value.

This algorithm is often called **greedy local search**, because it grabs a good neighbor without considering where to go next. Hill climbing is good on average, but it often gets stuck in:

- Local maxima: (you already know the definition of a local maximum). When Hill-Climbing gets to the vicinity of a local maximum, it will be drawn towards the peak, but then it will get stuck with nowhere to go, converging on that position	
- Ridges: sequence of local maximums that Hill-Climbing will find hard to navigate
- Plateaux: a flat area of the state-space landscape, it can either be a flat local maximum, or a **shoulder** where the possibility of progress is possible

![[Pasted image 20220317140109.png]]

### Variants of Hill-Climbing

1. Stochastic hill climbing: chooses at random from among the uphill moves, the probability of selection can be a function of the steepness of the uphill move
2. First-choice hill-climbing: further improves stochastic hill climbing by generating successors randomly until one is generated that is better than the current state. This a good strategy when a state has many successors
3. Random restart hill climbing: It conducts a series of hill climbing searches from randomly generated initial states until a goal is found 

---

## Simulated Annealing

> Result of the mix between a Hill-Climbing algorithm and a _Random Walk_ (exploring successors chosen uniformly from the set of possible successors)

In order to understand simulated annealing we must switch from _gradient ascent_ to _gradient descent_. Imagine you were given the task of getting a ping pong ball into the deepest crevice in a bumpy surface. If you just let the ball roll it will get stuck in a local minimum (_Hill Climbing-ish_), **but** if you shake the surface you can bounce out the ball from the local minimum. The sweet spot is shaking the surface just hard enough to get the ball out from the local minimum, but not hard enough to dislodge it from the global minimum.

- Simulated Annealing begins shaking the surface hard, and then gradually reducing the shake.

Instead of picking the best move, it picks a _random_ move. If the move improves the current state, it's always accepted, if it does not, the algorithm will accept it with a probability less than 1. Said probability keeps on decreasing depending on the badness of the move and as time goes by.

The probability function is called the _schedule_, if the schedule gives the algorithm time enough, it will find a global maximum with probability approaching 1.

![[Pasted image 20220317142045.png]]

## Local Beam Search

Local Beam Search tackles the problem of just keeping 1 state in memory,instead, local beam search keeps track of $k$ states. It begins with $k$ randomly generated states, and then at each step, all the successors of all $k$ states are generated, if any one of those is a goal state, the algorithm halts. Otherwise it selects the $k$ best successors from the generated pool, it then repeats.

> In a local beam search, useful information is passed among the parallel search threads. In effect, the states that generate the best successors say to the others, “Come over here, the grass is greener!” The algorithm quickly abandons unfruitful searches and moves its resources to where the most progress is being made

One caveat of Local Beam Search is that it can get too focused in a certain region of the landscape, making it a more expensive version of Hill-Climbing; however there is one variant, _Stochastic Beam Search_ that helps alleviating this issue.
- Instead of choosing the $k$ best successors,  it chooses $k$ successors at random from the generated pool, the probability of choosing any one successor is an increasing function of its value.
 
 ---
 
## Genetic Algorithms

It's a variant of Stochastic Beam Search in which successor states are generated by combining _two parents_ states rather than modifying a single state.

Like Beam Searches, genetic algorithms begin with a set of $k$ randomly generated states called the **population**. Each state or **individual**

![[Pasted image 20220317143053.png]]