# Linear Support Vector Machines

- General formula for linear SVM:
$$f(x,w,b)=\text{sign}(\langle w, x \rangle + b)$$

The target's class will be defined based on whether $f$ is positive or negative (_binary classification_).

In general, this classification algorithm tries first to find a line that can separate the data points, then to choose the best model we measure the distance between the line and the closest data points. The area (taking the distance as sort of the side of a rectangle) is often called the _classifier margin_:

![[Pasted image 20220127003406.png]]

The best classifier is then that which has the maximum margin.

## Multi-class classification

The approach taken to solving this problem is quite similar to a binary classification task; the key insight to actually solving it is that a multi-class classification of $n$ different classes can be broken down into $n$ binary classification tasks.

For example, if we had a dataset with a target value with 4 possible classes, we would need to run the following tests:

- Class 1 vs Other
- Class 2 vs Other
- Class 3 vs Other
- Class 4 vs Other

By the end of this process we'll have a series of scores that can then be compared, the one with the highest is then the prediction for the data point.

> The sign function is still used to determine what class a certain sample will belong to.

## Considerations

- Regularization is on by default with the `C` parameter, it is also proportional to the inverse of `alpha`, so, larger values of c correspond to less regularization and vice versa
- There will be times when the data is not linearly separable, for those cases one may use [[Kernelized SVM]]

## Implementation

```python
# Dependencies
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.datasets import load_breast_cancer
from sklearn.svm import LinearSVC

# Reading data
X, y = load_breast_cancer(return_X_y=True)
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=0)

# Model training
svm = LinearSVC(max_iter=1e6)
svm.fit(X_train, y_train)

# Results
print(f'''Linear SVM
(Train) Score: {svm.score(X_train, y_train):.5f}
(Test) Score: {svm.score(X_test, y_test):.5f}
N of features: {svm.n_features_in_}
Coefficients (w): {svm.coef_}
Intercept (b): {svm.intercept_}''')

"""
Output:

Linear SVM 
(Train) Score: 0.96009 
(Test) Score: 0.95804 
N of features: 30 
Coefficients (w): [[ 1.04725243e+00 4.67440689e-02 -1.09147324e-01 -2.32554536e-05
					-1.76091816e-01 -2.05188597e-01 -2.80162771e-01 -2.87466803e-01 
					-3.05536186e-01 -6.74106977e-03 7.32607441e-02 5.64790894e-01 
					-2.05093867e-01 -2.26477477e-02 -6.46815838e-03 1.56163759e-01 
					2.52854068e-01 -7.65080045e-03 -1.59544139e-02 3.98550368e-02 
					3.63479797e-01 -1.15833649e-01 -3.31739414e-03 -8.60867011e-03 
					-2.74192688e-01 -6.06992500e-01 -9.21876560e-01 -5.59665504e-01 
					-6.98823255e-01 -6.63915482e-02]] 
Intercept (b): [0.29130887]
"""
```