# Linear regression

- General formula for linear models:
$$\hat{y} = w_{0} \cdot x_{0} + w_{1}\cdot x_{1}+ \cdots + w_{n}\cdot x_{n} + \hat{b}$$

In its vector form:
$$\hat{y} = \langle \hat{w}, \vec{x} \rangle + \hat{b}$$

> Hats are used for parameters that we estimate; the vector $x$ contains all the features that will be used to predict the target value $\hat{y}$. **b is NOT a vector**

Where $\hat{y}$ is the prediction for the ==target value==, each $x_{n}$ is a ==feature== in the dataset, and $w_{n}$ is the _weight_ associated with its feature, the term $b$ is often referred to as _bias_ or _intercept_.

> Linear models for regression can be characterized as regression models for which the prediction is a line for a single feature, a plane when using two features, or a hyper‐plane in higher dimensions

## OLS

### Principle of Least Squares

![[Pasted image 20220124230123.png]]

The height differences between the data points and the line are called *residuals*. The sum of the squares of all residuals is then:

$$f(\hat{w}, b) = \sum_{i=1}^{n} \left(y_{i} - (w_{n}\cdot x_{n}+b)\right)^2$$

We want to find the values $(\hat{w}, b)$ that minimize $f$.

#### Implementation
```python
# Dependencies
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.datasets import make_regression
plt.style.use('ggplot')

# Splittig data
X_R1, y_R1 = make_regression(n_samples = 500, n_features=1, n_informative=1, bias = 150.0, noise = 30, random_state=0)
X_train, X_test, y_train, y_test = train_test_split(X_R1, y_R1, random_state=0)

# Training the model
linreg = LinearRegression()
linreg.fit(X_train, y_train)

# Results
print(f'''Coefficients (w): {linreg.coef_}
Intercept (b): {linreg.intercept_:.4f}
(Training) R^2 score: {linreg.score(X_train, y_train):.4f}
(Test) R^2 score: {linreg.score(X_test, y_test):.4f}''')

plt.figure(figsize=(8,5))
plt.scatter(X_test, y_test, c='b', marker= 'o', s=50, alpha=0.8, label='Test data')
plt.plot(X_R1, linreg.coef_ * X_R1 + linreg.intercept_, 'r-', label='OLS line')
plt.title('Least-squares linear regression')
plt.xlabel('Feature value (x)')
plt.ylabel('Target value (y)')
plt.legend()
plt.show()

"""
OUTPUT:
Coefficients (w): [44.709613] 
Intercept (b): 148.3236 
(Training) R^2 score: 0.7118 
(Test) R^2 score: 0.6914
"""
```

![[Pasted image 20220124234951.png]]

## Ridge

Ridge is pretty similar to OLS, but it adds a penalty to high values of $\hat{w}$, this is called _L2 Regularization_, to minimize the sum of the squares of the entries of $\hat{w}$:

$$f(\hat{w}, b) = \sum_{i=1}^{n} \left(y_{i} - (w_{n}\cdot x_{n}+b)\right)^{2} + \alpha \sum_{j=1}^{p} w_{j}^{2}$$

The influence of the regularization is controlled by $\alpha$, higher values mean more regularization, which help reducing the complexity of the model, _prevents overfitting_.

### Implementation

```python
from sklearn.linear_model import Ridge

X, y = make_regression(n_samples=50, n_features=60, n_informative=20, bias=50, noise=42, random_state=0)
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=0)

ridge = Ridge(alpha=3)
ridge.fit(X_train, y_train)

print(f'''Ridge
Train score: {ridge.score(X_train, y_train):.4f}
Test score: {ridge.score(X_test, y_test):.4f}
Intercept (b): {ridge.intercept_:.4f}\n''')

# Ridge with feature normalization
scaler = MinMaxScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)
ridge_norm = Ridge(alpha=5).fit(X_train_scaled, y_train)

print(f'''Feature scaled Ridge
Train score: {ridge_norm.score(X_train_scaled, y_train):.4f}
Test score: {ridge_norm.score(X_test_scaled, y_test):.4f}
Intercept (b): {ridge_norm.intercept_:.4f}''')

# Note how it worsens the results, EDA is mandatory, always do it before implementing any model
plt.figure(figsize=(8,5))
plt.plot(ridge.coef_, 'o', label='Ridge alpha=3')
plt.plot(ridge_norm.coef_, '^', label='Norm. Ridge alpha=5')
plt.xlabel('Coefficient Index')
plt.ylabel('Coefficient value')
plt.title('Model comparison')
plt.legend()

"""
Output:

Ridge
Train score: 0.9961
Test score: 0.8093
Intercept (b): 25.9501

Feature scaled Ridge 
Train score: 0.7468 
Test score: 0.4719
Intercept (b): -374.5496
"""
```

![[Pasted image 20220125015648.png]]

## Lasso

This is yet another linear model that is similar to _OLS_ and _Ridge_, but the regularization applied on this model is called _L1 Regularization_, it also adds a penalty to high values of $\hat{w}$; this regularization minimizes the sum of the _absolute_ values of the entries of $\hat{w}$:

$$f(\hat{w}, b) = \sum_{i=1}^{n} \left(y_{i} - (w_{n}\cdot x_{n}+b)\right)^{2} + \alpha \sum_{j=1}^{p} \lvert w_{j}^{2}\rvert$$

### Implementation

```python
from sklearn.linear_model import Lasso

X, y = make_regression(n_samples=50, n_features=60, n_informative=20, bias=50, noise=42, random_state=0)
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=0)

lasso = Lasso(alpha=0.01, max_iter=1e7)
lasso.fit(X_train, y_train)

print(f'''Lasso
Train score: {lasso.score(X_train, y_train):.4f}
Test score: {lasso.score(X_test, y_test):.4f}
Intercept (b): {lasso.intercept_:.4f}
Non-zero features: {np.sum(lasso.coef_ != 0)}\n''')

# Lasso with feature normalization
scaler = MinMaxScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

lasso_norm = Lasso(alpha=0.01, max_iter=1e6).fit(X_train_scaled, y_train)

print(f'''Feature scaled Lasso
Train score: {lasso_norm.score(X_train, y_train):.4f}
Test score: {lasso_norm.score(X_test, y_test):.4f}
Intercept (b): {lasso_norm.intercept_:.4f}
Non-zero features: {np.sum(lasso_norm.coef_ != 0)}''')

plt.figure(figsize=(8,5))
plt.plot(lasso.coef_, 'o', label='Lasso alpha = 0.01')
plt.plot(lasso_norm.coef_, '^', label='Norm. Lasso alpha = 0.01')
plt.xlabel('Coefficient Index')
plt.ylabel('Coefficient value')
plt.title('Model comparison')
plt.legend()

"""
Output:
Lasso 
Train score: 1.0000 
Test score: 0.8327 
Intercept (b): 17.1992 
Non-zero features: 48 

Feature scaled Lasso 
Train score: -40.3372 
Test score: -69.9703 
Intercept (b): -1416.6852 
Non-zero features: 42
"""
```

## Polynomial

> This was a tricky one to implement at first

Let's say a data point is described with 2 features, so that $\vec{x}=(x_{0},x_{1})$; we can apply a non-linear transformation to raise this 2-dimensional vector into a 5-dimensional feature space of the form $\vec{x'}=(x_{0},x_{1},x_{0}^{2},x_{0}x_{1},x_{1}^{2})$, this is a _polynomial transformation_. It's useful when we encounter data that just can't be described with a line, plane or hyperplane, for example:

![[Pasted image 20220125235744.png]]

==**Note:**== Even if it doesn't seem to be a linear model, it is!, it's still a _linear_ combination of _**linearly** independent_ features. Since it's still a linear regression problem, we can still take the _OLS_ approach, and use some form of regularization (ridge, lasso, etc...)

### Considerations

1. This approach helps us to capture interactions between features, a linear model just can't do this
2. This approach can also make classification tasks easier, see [[LSVM]]
3. Other non-linear transformations can be applied, see [[Non-Linear Basis Functions]]
4. Almost always you will need to use some form of regularization when using higher degrees polynomials in order to avoid overfitting

### Implementation

This is a little _complex_ example of how you can implement this polynomial regression:

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split

  
np.random.seed(0)
n = 15
x = np.linspace(0, 10, n) + np.random.randn(n)/5
y = np.sin(x)+x/6 + np.random.randn(n)/10

X_train, X_test, y_train, y_test = train_test_split(x, y, random_state=0)


def answer_one():
	from sklearn.linear_model import LinearRegression
	from sklearn.preprocessing import PolynomialFeatures
	# Your code here

	degrees = [1, 3, 6, 9]
	results = []

	for i in degrees:

		poly = PolynomialFeatures(degree=i)
		X_train_poly = poly.fit_transform(X_train.reshape(-1, 1))

		lrg = LinearRegression()
		lrg.fit(X_train_poly, y_train)

		test = np.linspace(0, 10, 100).reshape(-1, 1)
		poly_test = poly.fit_transform(test)

		results.append(lrg.predict(poly_test))

	return np.array(results)



def plot_one(degree_predictions):

	import matplotlib.pyplot as plt
	plt.figure(figsize=(10, 5))
	plt.plot(X_train, y_train, 'o', label='training data', markersize=10)
	plt.plot(X_test, y_test, 'o', label='test data', markersize=10)
	
	for i, degree in enumerate([1, 3, 6, 9]):
		plt.plot(np.linspace(0, 10, 100), degree_predictions[i], alpha=0.8, lw=2, label='degree={}'.format(degree))
	plt.ylim(-1, 2.5)
	plt.legend(loc=4)
	plt.show()


plot_one(answer_one())
```

![[Pasted image 20220126002556.png]]