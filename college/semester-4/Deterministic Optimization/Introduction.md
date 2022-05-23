 # Introduction to Linear Programming

---

> Optimization of a linear function that satisfies a set of linear constraints (equalities or inequalities).

---

## Basic definitions

Consider the following linear programming problem:

$$\begin{equation}
	 \begin{aligned}
		 \text{min } \quad & c_1 x_1 + c_2 x_2 + \dots + c_n x_n \\
		 \text{subject to }\quad &
		 \begin{array}{c}
			 a_{11} x_1 + a_{12} x_2 + \dots + a_{1n} x_n \geq b_1 \\
			 a_{21} x_1 + a_{22} x_2 + \dots + a_{2n} x_n \geq b_2 \\
			 \vdots \\
			 -a_{m1} x_1 + a_{m2} x_2 + \dots + a_{mn} x_n \geq b_m\\
			 x_1, x_2, \dots, x_m \geq 0
		 \end{array}
	 \end{aligned}
\end{equation}$$

Here $c_1 x_1 + c_2 x_2 + \dots + c_n x_n$ is the **objective function** to be _minimized_ (or _maximized_), it can be denoted by $z$ or $f(\vec{x})$, whatever suits you best, the coefficients $c_1, c_2, \dots, c_n$ are the known **cost coefficients** and $x_1, x_2, \dots, x_n$ are the **decision variables**. 

The inequality $\sum_{j=1}^{n} a_{ij} x_{j} \geq b_i$ is called the **ith constraint** (restriction, technological constraint). The coefficients $a_{ij} \text{ for } i = 1, \dots, m, j = 1, \dots, n$ are called the **technological coefficients**. The technological coefficients form the **constraint matrix**:

$$
\textbf{A} = \begin{bmatrix}
				a_{11} & a_{12} & \dots & a_{1n} \\
				a_{21} & a_{22} & \dots & a_{2n} \\
				\vdots & \vdots & {} & \vdots \\
				a_{m1} & a_{m2} & \dots & a_{mn}
			\end{bmatrix}$$

The constraints $x_1, x_2, \dots, x_n \geq 0$ are the **non-negativity constraints**. A set of values for the variables $x_1, \dots, x_n$ that satisfies all the constraints is called a **feasible point** or a **feasible solution**. The set of all such points is called the **feasible region** or the **feasible space**.

---

## Assumptions

1. **Proportionality:** given a variable $x_j$, its contribution to cost is $c_j x_j$ and its contribution to the ith constraint is $a_{ij}x_j$. This means that if $x_j$ is doubled, so is its contribution.
	1. No savings or extra costs are realized by using more of activity j, no discounts and such things, it is what it is.
2. **Additivity:** the total cost is the sum of the individual costs, and the total contribution to the ith constraint is the sum of the individual contributions of the individual activities. In nicer words there are no interaction effects among the activities
3. **Divisibility:** the decision variables can be divided into any fractional levels as to allow non-integer values for the decision variables
4. **Deterministic:** the coefficients $c_j, a_{ij}, b_{i}$ are **all known** deterministically, in other words, there is no place for random variables in the model, all the uncertainty is said to be approximated by the known coefficients

---

## Problem manipulation

### Inequalities and equations

> An inequality can be easily transformed into an equation.

Consider the constraint given by $\sum_{j=1}^{n}a_{ij}x_{j} \geq b_{i}$. We can always add a _slack_ or _surplus_ variable to compensate for the inequality.

- **slack** is reserved for $\leq$ constraints, it refers to the amount of resources that were not used
- **surplus** is reserved for $\geq$ constraints, refers to the amount by which the minimum resource was exceeded

#### Example

Convert the next optimization problem into its standard form (see [[#Standard and Canonical forms|Standard and Canonical forms]]):

$$\begin{equation}
	 \begin{aligned}
		 \text{max } \quad & 3x + 5y \\
		 \text{subject to }\quad &
		 \begin{array}{c}
			 x + 3y \leq 60 \\
			 3x + 4y \leq 120 \\
			 x \geq 10\\
			 x, y \geq 0
		 \end{array}
	 \end{aligned}
\end{equation}$$

We modify the first constraint by adding an **slack** variable:

$$x + 3y + s_1 = 60 $$

The second constraint will also need a **slack** variable:

$$3x + 4y + s_2 = 120$$

The third constraints needs a **surplus** variable:

$$x - s_3 = 10$$

The non-negativity constraint is then:

$$x, y, s_1, s_2, s_3 \geq 0$$

> An equality can be conversely transformed into 2 inequalities

Any constraint of the form $\sum_{j=1}^{n}a_{ij}x_{j} = b_{i}$ can be _split_ into the 2 inequalities $\sum_{j=1}^{n}a_{ij}x_{j} \geq b_{i}$ and $\sum_{j=1}^{n}a_{ij}x_{j} \leq b_{i}$, as you can imagine, the only thing that exists in between 2 constraints is the original equality. The book says this is not usually done in practice.

### Non-negativity of the variables

For most practical problems, the variables will represent physical quantities, so, they must be non-negative (show me an optimization problem where the number of items produced can be negative). Furthermore, the **simplex method** (which I hope will be the only one covered in class) is designed to work with non-negativity constraints.

### Min vs Max

A maximization problem can be converted into a minimization problem, and vice versa:

$$\text{max } \sum_{j=1}^{n}c_jx_{j} = - \text{min } \sum_{j=1}^{n} -c_jx_{j}$$

---

## Standard and Canonical forms

- A linear program is said to be in **standard format** if all restrictions are equalities and all variables are non-negative
- A _minimization_ problem is in **canonical form** if all variables are non-negative and all the constraints are of the $\geq$ type, conversely, a _maximization problem_ is in canonical form if all variables are non-negative and all the constraints are of the type $\leq$

> Note that the definition of _formats_ implies that an optimization problem needs not follow a predefined structure for it to exist, these formats exist because the available algorithms were designed around them

## Matrix notation

Following the ideas in [[#Basic definitions|Basic definitions]], a linear programming problem can be stated in a more convenient (and elegant) form using matrix notation. Consider the following problem:

$$\begin{equation}
	 \begin{aligned}
		 \text{min } \quad & \sum_{j=1}^{n} c_j x_j \\
		 \text{subject to }\quad &
		 \begin{array}{cc}
			 \sum_{j=1}^{n} a_{ij} x_j = b_i & i = 1, 2, \dots, m \\
			 x_j \geq 0 & j = 1, 2, \dots, n
		 \end{array}
	 \end{aligned}
\end{equation}$$

Denote the _row_ vector $\vec{c} = (c_1, c_2, \dots, c_n)$, and consider the following _column_ vectors $\vec{x}, \vec{b}$, and the $m \times n$ matrix $\mathbf{A}$

$$\begin{equation}
	\begin{array}{ccc}
		\vec{x} = \begin{bmatrix}
		x_1 \\
		x_2 \\
		\vdots \\
		x_n
		\end{bmatrix} & \vec{b} = \begin{bmatrix}
		b_1 \\
		b_2 \\
		\vdots \\
		b_m
		\end{bmatrix} & \mathbf{A} = \begin{bmatrix}
				a_{11} & a_{12} & \dots & a_{1n} \\
				a_{21} & a_{22} & \dots & a_{2n} \\
				\vdots & \vdots & {} & \vdots \\
				a_{m1} & a_{m2} & \dots & a_{mn}
			\end{bmatrix}
	\end{array}
\end{equation}$$

Then the problem can be written as follows:

$$\begin{equation}
	 \begin{aligned}
		 \text{min } \quad & \vec{c} \ \vec{x} \\
		 \text{subject to }\quad & \mathbf{A} \vec{x} = \vec{b} \\
		 & \vec{x} \geq 0
	 \end{aligned}
\end{equation}$$

---

## Geometric solution

### Feasible region and optimal solutions

#### Unique Finite Optimal Solution

If the optimal finite solution is unique

![[Pasted image 20220330163109.png]]

In figure a, the feasible region is bounded; that is, there is a _ball_ that encloses and defines a region in the space; in figure b, the region is unbounded, nevertheless, there's still an unique optimal solution

#### Alternative Finite Optimal Solutions

The feasible region is unbounded but the optimal objective is finite. Any point on the _ray_ with vertex $x^{*}$ is optimal. The optimal solution set is unbounded.

![[Pasted image 20220330163332.png]]

As in the previous example, the region may be bounded or not, but there may be more than one optimal value, as in figure a, there both $x_1^{*}$ and $x_2^{*}$ are optimal, and so is any point on the line segment that connects both points (why does the book say this is finite? Is it because the points do not lie in $\infty$?). In figure b we have the same situation, but the region is unbounded, any point in the ray with vertex $x^{*}$ is optimal, but since it's a ray, there are infinitely many optimal points, so, the _optimal solution set_ is **unbounded**. 

#### Unbounded Optimal Solution Value

This only occurs when both the feasible region and the optimal solution value are _unbounded_. By this we mean that we can keep on moving the optimal point in a certain direction (whilst respecting the set constraints) forever, and the optimal value keeps decreasing/increasing.

![[Pasted image 20220330164306.png]]

#### Empty Feasible Region

> The system of equations and/or inequalities defining the feasible regions is _inconsistent_

![[empty-feasible-region.png]]

There does not exist a feasible region, hence, no optimal value can be found.

### The requirement space

Ask professor Elizalde for further clarification, so far the topic seems pretty convoluted

---
