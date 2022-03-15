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

#### Linear SVM

Generalization of the _maximal margin classifier_. Originally this technique was developed for binary classification, it works by finding a hyperplane that is farthest from the training observations. In the next image we can see the maximal margin hyperplane that best separates 2 features (in this case it's just a solid line, we're working in 2D).

![[Pasted image 20220315120953.png]]

The margin is the distance from the solid line to either of the dashed lines. The dots that connect the hyperplane to the margin are the _support vectors_. Notice how the hyperplane and the margin are based solely on the dots that connect them, further reason to call them support vectors

![[Pasted image 20220315121215.png]]

In the image above we can see the effect of the regularization parameter $C$, as it increases, the model becomes more tolerant of allowing data to be misclassified.

In it's linear format, the method will work as long as there exists a hyperplane that can separate the data, and yes, as you can imagine, there is an even more OP SVM that can separate non-linearly separable data.

#### Kernelized SVM

Here comes the fun bit. Take a look at the next image, and attempt to draw a line that can accurately separate the data.

![[Pasted image 20220315121555.png]]

How did it go? Don't even answer, I know you could not find a proper line, that's because the data points in the image above were not suitable for a linear separation. Kernelized SVMs come to our rescue.

When the original data cannot be separated based solely on the input space, we can take the feature space to a higher dimension where the data can then be linearly separated.

![[Pasted image 20220315121919.png]]

The criteria for the transformation is encoded in the **Kernel**, they generally look like this: $\phi:X\to\mathbb{R}^n$, if $K:X\to\mathbb{R}$

$$K(y,z)=\langle\phi(y),\phi(z)\rangle,$$

As I've said, kernels transform the original feature space into a higher dimensional space, where we hope our data is linearly separable, once we are there, we calculate a dot product of a given pair of observations, there's still some black box magic occurring here, but in the end the kernel will help us find the hyperplane that best separates our data.

There are many types of kernels, but the most widely used (and those that can be used with `scikit-learn`) are the polynomial and the RBF. Here's how the decision boundaries would look like when taken back to the original feature space:

![[Pasted image 20220315122504.png]]

### Neural Networks

Mathematical model inspired on the biological behavior of neurons and how they organize to form the structure of the brain.

A neural network model is usually made of:

- Nodes, acting as input, output and as intermediate processors
- Synaptic weights, $w_1, w_2, w_n$
- The aggregation function $\Sigma$
- The activation function $f$
- An output $y$

Each node is connected to the next set (layer) via a series of weighted trajectories. After a prediction is made, the error is evaluated and it modifies the weights of the connections in order to improve the predictions. This cycle is repeated until the training set is exhausted.

- Once the model is trained, the test set is evaluated.

#### Types of neural networks

- Feed forward
- Radial Basis Function
- Multi-layer Perceptron
- Convolutional Neural Network
- Recurrent Neural Network
- Modular Neural Network

The multi-layer perceptron is composed of:

1. Input layer: each neuron of this layer is associated with each of the input variables of the network
2. Hidden layers: an agglomeration of layers in which each activation of an output is obtained by the weighed sum of the prior layer
3. Output layer: connects the hidden layers with the layer that produces the model's predictions