# Metrics

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

- True positive rate. The proportion of those that belong to the positive class that were labeled correctly. I know, it sounds pretty confusing, here is the math formula:

$$Sensitivity = \frac{TP}{TP + FN}$$

![[Pasted image 20220313210834.png]]

![[Pasted image 20220313210854.png]]

#### Specificity

- True negative rate. The proportion of those that belong to the negative class that were labeled correctly.

$$Specificity = \frac{TN}{FP + TN}$$

![[Pasted image 20220313211027.png]]

![[Pasted image 20220313211038.png]]

---

## Cross-validation

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