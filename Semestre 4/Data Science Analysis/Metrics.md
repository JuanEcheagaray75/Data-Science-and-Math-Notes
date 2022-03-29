# Metrics

1. [[#Confusion matrix|Confusion matrix]]
	1. [[#Derived metrics|Derived metrics]]
		1. [[#Sensitivity|Sensitivity]]
		1. [[#Specificity|Specificity]]
		1. [[#Accuracy|Accuracy]]
		1. [[#Precision|Precision]]
		1. [[#F1 Score|F1 Score]]
1. [[#ROC-AUC|ROC-AUC]]
1. [[#Cross-validation|Cross-validation]]
	1. [[#Cross-validation techniques|Cross-validation techniques]]
		1. [[#K-fold|K-fold]]
			1. [[#Implementation|Implementation]]
		1. [[#Leave P-out|Leave P-out]]
		1. [[#leave One-out|leave One-out]]
		1. [[#Repeated random sub-sampling|Repeated random sub-sampling]]
		1. [[#Holdout method|Holdout method]]
1. [[#Bias and Variance|Bias and Variance]]

---

## Confusion matrix

> A confusion matrix tells you what your machine learning algorithm did right and what it did wrong

Let's try to explain this through an example:

Say we have a dataset containing medical records of some patients, our variable of interest is whether or not the patient had heart disease or not, this information is encoded in a binary format, either the patient had it or not. Once that's established we can begin training different ML models in an attempt to predict whether or not a patient will develop said heart disease or not.

First of all, we split our data into 2 sets, to train and test our model. As crazy as it may sound, we will use the training set to train the ML model of our choosing, and then we will use the test set to measure the performance of the model.

After our model runs, we need a way to measure its performance, the confusion matrix is the first metric that we must observe (other metrics follow from this):

![[Pasted image 20220313204942.png]]

- Rows correspond to the predicted class by the ML method
- Columns correspond to the true data classes
- Values on the diagonal correspond to all the data points to which the algorithm correctly predicted their class
- False positives (FP)	would correspond to patients to which the algorithm predicted they would have heart disease, but in reality they do not, contrary to that, False negatives (FN) would correspond to patients that had heart disease but the algorithm predicted otherwise.

**Note:** The shape of the confusion matrix is determined by the number of classes the response variable has, on the case presented here, there are only 2 possibilities, that's why the confusion matrix is a $2\times 2$ matrix, if we had $N$ different classes, the confusion matrix's shape would be $N \times N$

### Derived metrics

#### Sensitivity

- True positive rate, also known as _recall_. The proportion of those that belong to the positive class that were labeled correctly. I know, it sounds pretty confusing, here is the math formula:

$$Sensitivity = \frac{TP}{TP + FN}$$

![[Pasted image 20220313210834.png]]

![[Pasted image 20220313210854.png]]

#### Specificity

- True negative rate. The proportion of those that belong to the negative class that were labeled correctly.

$$Specificity = \frac{TN}{FP + TN}$$

![[Pasted image 20220313211027.png]]

![[Pasted image 20220313211038.png]]


#### Accuracy

Ratio of correct predictions to the total sample size. It indicates how often is the classifier correct, it's defined as:

$$ACC = \frac{TP + TN}{TP + FN + TN + FP}$$

- Accuracy works best if the class labels are uniformly distributed. Hence, not a good measure of model performance on imbalanced datasets

#### Precision

Ratio of correct positive predictions out of all positive predictions made, or the accuracy of predicted positives. It's defined as follows:

$$PREC = \frac{TP}{TP + FP}$$

#### F1 Score

Also known as the harmonic mean of the model's precision and sensitivity, defined as follows:

$$F1 = 2 \cdot \frac{PREC \cdot Sensitivity}{PREC + Sensitivity}$$

We prefer the harmonic mean because it punishes extreme values

---

## ROC-AUC

Comparison between True Positive Rate (Sensitivity) and False Positive Rate (1 - Specificity). ROC-AUC curves are used when tuning the hyper-parameters of a model, it's based on the confusion matrix and it helps the researcher understand how both of the quantities previously mentioned behave given a particular set of hyper-parameters.

Let's take a Logistic Regression as an example. Given a particular dataset where information about whether a mouse is considered obese or not based upon its weight. The regression model will fit a logistic regression to the training data, errors will occur, and a confusion matrix must be created to assess it's overall performance.

ROC curves go a step beyond by analyzing the model's performance by tuning the hyper-parameters of a model, in this case, the hyper-parameter we can tune is the threshold used for determining whether a mouse would be labeled as obese or not. Both sensitivity and specificity can be calculated for each iteration, then the True Positive Rate and False Positive Rate can be plotted. The resulting plot may look like this:

![[Pasted image 20220314123214.png]]

In general, we want the model with the **highest True Positive Rate** and the **lowest False Positive Rate**, this occurs when TTR is 1, and FPR is 0.

Then, the AUC (Area Under the Curve) is a numeric measure of the overall performance of the model, an AUC for the _guessing model_ (the line in the middle from the last picture) is 0.5, AUC must at least be greater than this value to be considered above average. So, in general, we want models with AUC as close to 1 as possible.

---

## Cross-validation

Cross-validation is a technique for assessing how the statistical analysis generalizes to an independent dataset. It is a technique for evaluating machine learning models by training several models on subsets of the available input and evaluating them on the complementary subset of the data.

Using cross-validation there is a higher chance of detecting overfitting with ease.

### Cross-validation techniques

> For all of the following techniques I assume that you have already split your data into 2 subsets, one for training and another for testing.

#### K-fold

The entire training set is broken up in $k$ equal parts. The first part is kept as the _hold out_ set and the remaining $k-1$ parts are used to train the model. Then the trained model is tested on the holdout set. This process is then repeated $k$ times, changing the hold out set in each iteration.

![[Pasted image 20220314104632.png]]

$k$ usually stays between 3 and 5, but it can be expanded to higher values. Normally it's kept low because cross-validation is a computationally expensive task (you'll see when you implement it).

The method used will regularly return a list of $k$ accuracy values, it's a common practice to then use the mean to leverage the model performance.

##### Implementation

```python
import numpy as np
from sklearn.model_selection import cross_val_score

# Notice how we feed it the entire dataset, you should not pass X_train and y_train
cross_scores = cross_val_score(model, X, y, cv=5)
print(np.mean(cross_scores))
```

#### Leave P-out

Using $p$ observations as the _validation set_ (hold out set), the rest of the observations are used to train the model. This is then repeated in all possible ways to cut the original dataset on a validation set of $p$ observations and $N-p$ observations for the training set.

#### Leave One-out

Variant of Leave P-out, the process is the same but $p=1$. It's easy to see that this is even more computationally expensive, since the validation process will be repeated $N$ times.

#### Repeated random sub-sampling

Creates multiple random splits of the dataset into training and validation data. For each such split the model is fit to the training data, and predictive accuracy is assessed using the validation data, the results are then averaged over the splits. 

- The advantage of this method is that the proportion of the training/validation split is not dependent on the number of iterations.
- The disadvantage is that some observations may never be selected in the validation sub-sample, whereas others may be selected more than once, in other words, validation subsets may overlap

![[Pasted image 20220314113759.png]]

#### Holdout method

You already know this one, it looks like this: 

```python
from sklearn.model_selection import train_test_split

X_train, y_train, X_test, y_test = train_test_split(X, y)
```

The holdout method is the first step done towards training a model. You MUST always do this

---

## Bias and Variance

Say we have a dataset describing mouse sizes, in particular, we have info on the mouse's weights and heights; we then want to create a ML model that predicts height based on weight. A scatter-plot of said data may look like this:

![[Pasted image 20220313222155.png]]

First we will split the data into 2 sets, a training and a test set. The ML model will have access to the first set.

We can first attempt to fit a line to the data via a linear regression. We would end up with something that looks like this

![[Pasted image 20220313223056.png]]

This line cannot accurately represent the arc, it cannot represent the _true relationship_

> The inability for a machine learning method to capture the true relationship is called **bias**

A different ML method might fit a squiggly line to the training set, and it could look like this:

![[Pasted image 20220313223401.png]]

This model is super flexible, and it touches every single data point! This would mean that the model has _very low bias_

Now lets compare the models on the _testing set_:

![[Pasted image 20220313224211.png]]

If we calculated the square error for each of the models, the straight line would win! The straight line fits the test set better than the squiggly line.

- The squiggly line has **low bias** since it's flexible and can adapt to the curve in the relationship between weight and height, but it has a **very high** variance because the sum of squared errors would be pretty different for different datasets. Simply put, the squiggly line might perform with excellence on some datasets, but it could also perform very badly.
	- In ML terminology, the squiggly line is said to be ==overfitting==, it learned to well the training set that it fails to generalize to new unseen data

> The difference in fits between datasets is called **variance**

- The straight line is said to have **high bias** since it cannot adapt itself to the relationship of the variables, but it has **low variance**, since it's sum of squared errors is expected to be pretty similar across different datasets.
	- The straight line is said to be ==underfitting==, it failed to capture the inner distribution of the dataset, so it performs pretty bad on both the training and test sets

---

Add metrics for regression models