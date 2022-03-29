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

### Non-negativity of the variables

### Min vs Max

---

## Standard and Canonical forms

## Matrix notation

---

## Geometric solution

---
