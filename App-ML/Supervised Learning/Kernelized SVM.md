# Kernelized Support Vector Machines

Kernelized SVMs become useful when a linear SVM can't separate data points, as in the next example:

![[Pasted image 20220127151122.png]]

Kernelized SVMs solve this problem by transforming the original input space into a higher dimensional space where a linear classifier can easily separate the data.

### Example 1

In order to classify these data point we begin by applying a transformation to our data that maps it to 2-dimensional space, in this case, $v_i=(x_{i}) \to v_{i}^{'}=(x_{i}, x_{i}^2)$

![[Pasted image 20220127171155.png]]

Now that we are in a higher dimensional space we can easily apply a linear classifier to find a line that separates the data points. Note how said line is then converted to a parabola when applying the inverse of the transformation. The decision boundary in this case is represented by the 2 points where the parabola crosses the x-axis.

### Example 2

As with the previous example, the data points cannot be linearly separated (_without losing accuracy of course_). The next step is to map our data points to a 3-dimensional space, in this case the mapping used has the effect of shaping the original feature space into a paraboloid centered at 0.

![[Pasted image 20220127171420.png]]

Here we can find a plane that separates the data with ease. The decision boundary is then all the point that intersect the plane and the paraboloid. When we take the inverse of this mapping, the decision boundary becomes an ellipse in the original input space.

![[Pasted image 20220127171456.png]]

## The kernel

Measures the similarity between data points in a higher dimensional space, (_kind of like a dot product_). The most widely used kernel (default on sklearn's SVM) is the **Radial Basis Function Kernel**, she looks like this:

$$K(\vec{x}_{1}, \vec{x}_{2}) = \exp (-\gamma \cdot \|\vec{x}_{1} - \vec{x}_{2}\|^{2})$$

## Important parameters

In order to control model complexity we can modify this parameters:

1. Kernel: default is `rbf`, but there is also `poly` and `sigmoid`
2. `C`: regularization parameter
3. `gamma`: controls how far the influence of a data point reaches, larger values of gamma lead to a very small influence distance, and vice versa.

### Influence of gamma

![[Pasted image 20220127180206.png]]

## Considerations

- Performs well on a range of datasets, its efficiency decreases as the training set size increases.
- Versatile, different kernel functions can be applied.
- Works well with low and high dimensional datasets (even when they're sparse).
- Needs normalization and parameter tuning.
- Hard to interpret, not suited for cases when explainability is mandatory

## Implementation

```python
# Dependencies
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.datasets import load_breast_cancer
from sklearn.preprocessing import MinMaxScaler

# Reading data
X, y = load_breast_cancer(return_X_y=True)
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=5)

# Scaling the data (for better accuracy)
scaler = MinMaxScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# Creating and training the model
from sklearn.svm import SVC

svm = SVC()
svm.fit(X_train_scaled, y_train)

# Results
print(f'''SVM
(Train) Score: {svm.score(X_train_scaled, y_train):.5f}
(Test) Score: {svm.score(X_test_scaled, y_test):.5f}
N of features: {svm.n_features_in_}''')

"""
Output:

SVM 
(Train) Score: 0.98826 
(Test) Score: 0.97902 
N of features: 30
"""
```