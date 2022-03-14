# Feature selection

1. [[#Wrapper methods|Wrapper methods]]
	1. [[#Forward Selection|Forward Selection]]
	1. [[#Backward Selection|Backward Selection]]
	1. [[#Step-wise Selection|Step-wise Selection]]
1. [[#Filter methods|Filter methods]]
	1. [[#ANOVA|ANOVA]]
		1. [[#Implementation|Implementation]]
	1. [[#Pearson correlation|Pearson correlation]]
	1. [[#Variance thresh-holding|Variance thresh-holding]]
1. [[#Embedded methods|Embedded methods]]
	1. [[#Ridge|Ridge]]
	1. [[#Lasso|Lasso]]
	1. [[#Decision Trees|Decision Trees]]

- Reduces model complexity, aka. prevents overfitting
- Reduction of dimensionality and redundancy
- Helps find the most important variables
- Helps finding correlations between variables

---

## Wrapper methods

Compute models with a certain subset of features and evaluate the importance of each feature. Then they iterate and try a different subset of features until the optimal subset is found. It's pretty easy to see that one major drawback of this approach is the computation time and power needed for the method, wrappers are also pretty bad at preventing overfitting when there is not a large amount of data

### Forward Selection

Starts with zero features, then, for each individual feature, runs a model and determines the p-value associated with the t-test or F-test performed. It then selects the feature with the lowest p-value and adds it to the working model.

Next it takes the first feature selected and runs the model with a second feature added, it then chooses the feature with the lowest p-value. By this point you can see the pattern, by the end all features with significant p-values will be added to the model.

### Backward Selection

Starts with all features. It then runs a model and calculates a p-value of the model for each feature. The feature with the largest p-value (the most insignificant) will be removed from the model; then, the process starts again, and it will continue until only features with significant p-values remain.

### Step-wise Selection

An hybrid of forward and backward selection. It also starts with zero features and adds the one feature with the lowest p-value, then it finds the second feature with the lowest p-value, but by the third iteration it will then again look for the feature with the lowest p-value, **but** _it will also remove any features that were previously added that now have a high p-value_.

With this approach, all the features that remain are guaranteed to be significant.

---

## Filter methods

Rather than tuning a model, a subset of the features is selected through ranking them by a statistical measure. One benefit is that they are not computationally expensive and will not overfit the data.

One drawback is that filter methods are _blind_ to any interactions or correlations between features.

### ANOVA

Looks at the variation within the treatment of a feature and also between the treatments

- Helps determine whether a feature does a good job of accounting for variation in the dependent variable.
- If the variance within each specific treatment is larger than the variation between treatments, then the feature hasn't done a good job of accounting for the variation in the dependent variable.

To carry out an ANOVA test, an F-statistic is computed for each individual feature with the variation between treatments in the numerator (**SST**) and the variation within treatments in the denominator. This statistic is then tested against the null hypothesis, ($H0:$ Mean value is equal across all treatments) and the alternative ($Ha$: at least 2 treatments differ)

#### Implementation

```python
def ANOVA(X,y):
	'''Univariate linear regression tests
	Quick linear model for sequentially testing the effect of many regressors
	Using scikit learn's Feature selection toolbox
	Returns:
	F (array) = F-values for regressors
	pvalues (array) = p-values for F-scores'''
	
	from sklearn.feature_selection import f_regression
	
	(F,pvalues) = f_regression(X,y)
	return (F,pvalues)
```

### Pearson correlation

Measure of the similarity of 2 features that ranges between -1 and 1. A value close to 1 or -1 indicates that the 2 features have a high correlation and may be related.

- To create a model with reduced features using Pearson correlation, you can use a heat-map of all the correlations and pick the features that have the highest correlation with the response variable

### Variance thresh-holding

The variance of a feature determines how much predicting power it has. The lower the variance is, the less information contained in the feature, and the less value it has in predicting the response variable.

Variance thresh-holding is done by finding the variance of each feature, and then dropping all of the features below a certain variance thresh-hold.

```python
def variance_threshold_selector(data, threshold=0.5):
	from sklearn.feature_selection import VarianceThreshold
	
	selector = VarianceThreshold(threshold)
	selector.fit(data)
	
	return data[data.columns[selector.get_support(indices=True)]]
```

---

## Embedded methods

Perform feature selection as a part of the model creation process.

### Ridge

Ridge regression is useful when you want to keep all the variables in your dataset, but don't want your model to focus too much on any one coefficient. Ridge regression solves this problem by penalizing the $\beta$ coefficients for being too large.

- In simpler words, it scales back the strength of correlations with variables that may not be as important as others

$$f(\hat{w}, b) = \sum_{i=1}^{n} \left(y_{i} - (w_{n}\cdot x_{n}+b)\right)^{2} + \alpha \sum_{j=1}^{p} w_{j}^{2}$$

```python
import matplotlib.pyplot as plt
from sklearn.linear_model import RidgeCV

ridge = RidgeCV(cv=5, random_state=0).fit(X_train, y_train)
print(f'Model Score: {ridge.score(X_train, y_train)}')
print(f'Model Coeff: {ridge.get_params()}')

plt.figure(figsize=(8,5))
plt.plot(ridge.coef_, 'o', label='Ridge alpha=your alpha')
plt.xlabel('Coefficient Index')
plt.ylabel('Coefficient value')
plt.title('Model comparison')
plt.legend()

```

### Lasso

It's pretty similar to Ridge regression, but it differs in that Lasso can force a $\beta$ coefficient to be zero, effectively removing the feature from the model 

$$f(\hat{w}, b) = \sum_{i=1}^{n} \left(y_{i} - (w_{n}\cdot x_{n}+b)\right)^{2} + \alpha \sum_{j=1}^{p} \lvert w_{j}^{2}\rvert$$

```python
import matplolib.pyplot as plt
from sklearn.linear_model import LassoCV

lasso = LassoCV(cv=5, random_state=0).fit(X_train, y_train)

plt.figure(figsize=(8,5))
plt.plot(lasso.coef_, 'o', label='Lasso alpha = 0.01')
plt.xlabel('Coefficient Index')
plt.ylabel('Coefficient value')
plt.title('Model comparison')
plt.legend()
```

---

**IMPORTANT** All features must be standardized for both Lasso and Ridge, you don't want to punish a certain variable too much just because it's values lie on another scale

---

### Decision Trees

This method creates splits in the tree based on certain features to create an algorithm to find the correct response variable. It uses a _wrapper method inside an embedded method_.

When making the tree model, the function has several feature selection methods built into it. At each split, the function used to create the tree tries all possible splits for all the features and chooses the one that splits the data into the most homogeneous group (just means that it divides the data points well).

This is a wrapper method since it tries all possible combinations of features and then picks the best one.

After a tree has been made, there is an option to go back and 'prune' some of the nodes that do not provide any additional information to the model, this prevents overfitting, and it must be done through cross-validation.

---

Further documentation:
- https://towardsdatascience.com/intro-to-feature-selection-methods-for-data-science-4cae2178a00a
- https://scikit-learn.org/stable/modules/feature_selection.html


![[Pasted image 20220222182626.png]]
