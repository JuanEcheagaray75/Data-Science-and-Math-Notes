# Machine Learning Models

## Regression

In order to represent the relationship between a variable $y$ with another variable (or a set of variables) $x$ we use regression models.

### Linear regression

Among all the regression models, a linear regression might be the simplest. It has the following form:

$$y = \beta_0 + \beta X + \epsilon$$

Where $\beta_0$ is the interception to the origin, $\beta$ represents the slope, and $\epsilon$ is the random error, we assume it follows a normal distribution $\epsilon \sim N(0, \sigma^2)$.

- The estimations for the parameters $\beta_0$ and $\beta$ must produce a line (plane, or hyperplane) that best fits the data. The usual way in which we find these parameters is through the _Least Squares Method_

See [[Linear Regression]] for a more detailed explanation

### Non-linear regression

A non-linear regression generates an equation that tries to describe the non-linear relationship between a continuous response variable and a set 	of predictor variables.

$$y = f(X, \Theta) + \epsilon$$

- Non-linear regression is used when the _least squares method_ cannot adequately model the relationship between the response variable and the predictor variables.
- Since we cannot rely on **OLS** to find a set of parameters for an equation, we have to rely on numerical methods that iteratively finds the best set of parameters, choosing the best set of parameters is based on the same criteria, the reduction of the sum of squared residuals.
	- This iterative process goes on until the algorithm converges, if the maximum number of iterations is reached before finding an optimal solution, we can try again using different starting values (or use a different model) 

## Classification

### Classification vs clustering

- **Classification** is a type of _supervised_ machine learning algorithm. For any given input, the classification algorithms help in the prediction of the class of the output variable.
- **Clustering** is a type of _unsupervised_ machine learning algorithm. It is used to group data points having similar characteristics as clusters. _Ideally_ the data points in the same cluster should exhibit similar properties and the data points in different clusters should be as dissimilar as possible.

### Logistic Regression



### K-nearest neighbors

### Decision Trees

### Support Vector Machines

### Neural Networks