# Logistic Regression

- Formula for logistic regression:
$$
\begin{gather}
	\hat{y} = \text{logistic}(\hat{b}+\hat{w}_{0}x_{0}+\hat{w}_{1}x_{1}+\cdots+\hat{w}_{n}x_{n})\\
	\hat{y} = \frac{1}{1 + \exp(\hat{b}+\hat{w}_{0}x_{0}+\hat{w}_{1}x_{1}+\cdots+\hat{w}_{n}x_{n})}
\end{gather}
$$

This function has the effect of comprising $\hat{y}$ to only have values in $(0, 1)$. We interpret the output of this function as the probability of belonging to the positive class (1), if the probability is higher than or equal to $0.5$, we classify that data point as belonging to class 1, and otherwise if the probability is less than $0.5$

## Considerations

1. As with the linear models introduced in [[Linear Regression]], this classifier has a regularization parameter $C$, as Ridge regression, this classifier uses _L2_ regularization. By default $C$ it is set to 1. It is **important** to note that $C \propto \frac{1}{\alpha}$.
2. It's also a good idea to normalize all the features.

## Implementation

```python
# Dependencies
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
plt.style.use('ggplot')
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split

# Reading data and training the model
fruits = pd.read_table('data/fruit_data_with_colors.txt')
features = ['height', 'width']
target = 'fruit_label'
classes = ['not-apple', 'apple']
X = fruits[features]
y = fruits[target] == 1
C = 100
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=0)
clf = LogisticRegression(C=C).fit(X_train.values, y_train)

# Results
height, width = 6, 8
prediction = clf.predict([[height, width]])[0]
print(f'''Logistic regression, C={C}
(Train) Score: {clf.score(X_train.values, y_train):.4f}
(Test) Score: {clf.score(X_test.values, y_test):.4f}''')

# Visualization
plt.figure(figsize=(8,5))
sns.scatterplot(data=X_train, x='height', y='width', hue=y_train, style=y_train)
plt.title('Classification')

"""
Output:
Logistic regression, C=100
(Train) Score: 0.7955
(Test) Score: 0.7333
"""
```

![[Pasted image 20220126224048.png]]