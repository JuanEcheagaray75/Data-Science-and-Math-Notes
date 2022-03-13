# Feature selection

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

### ANOVA

### Pearson correlation

### Variance thresh-holding

---

## Embedded methods

### Ridge

### Lasso

### Decision Trees

---

Further documentation:
- https://towardsdatascience.com/intro-to-feature-selection-methods-for-data-science-4cae2178a00a
- https://scikit-learn.org/stable/modules/feature_selection.html

![[Pasted image 20220221173121.png]]

![[Pasted image 20220221173539.png]]

![[Pasted image 20220221175147.png]]

![[Pasted image 20220221175756.png]]

![[Pasted image 20220221181057.png]]

![[Pasted image 20220222172256.png]]

![[Pasted image 20220222174454.png]]

![[Pasted image 20220222182626.png]]
