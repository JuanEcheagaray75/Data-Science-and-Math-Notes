# Feature space

- [Feature space](#feature-space)
  - [Target](#target)
  - [Variables](#variables)
  - [Mappings](#mappings)

Feature space refers to the n-dimensions where your variables live (not including a target variable, if it is present). The term is used often in ML literature because a task in ML is _feature extraction_, hence we view all variables as features. For example, consider the data set with:

## Target

1. Y $\equiv$ Thickness of car tires after some testing period

## Variables

1. $X_1$ $\equiv$  distance traveled in test
2. $X_2$ $\equiv$ time duration of test
3. $X_3$ $\equiv$ amount of chemical $C$ in tires

The feature space is $R^3$, or more accurately, the positive quadrant in $R^3$ as all the $X$ variables can only be positive quantities. Domain knowledge about tires might suggest that the _speed_ the vehicle was moving at is important, hence we generate another variable, $X_4$ (this is the feature extraction part):

- $X_4 = \frac{X_1}{X_2} \equiv$ the speed of the vehicle during testing.

This extends our old feature space into a new one, the positive part of $R^4$

## Mappings

Furthermore, a _mapping_ in our example is a function, $\phi$, from $R^3 \to R^4$:

$\phi(x_1,x_2,x_3)=(x_1,x_2,x_3,\frac{x_1}{x_2})$

Cam.Davidson.Pilon (<https://stats.stackexchange.com/users/11867/cam-davidson-pilon>), What is "feature space"?, URL (version: 2012-12-24): <https://stats.stackexchange.com/q/46441>
