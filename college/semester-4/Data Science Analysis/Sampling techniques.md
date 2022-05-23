# Sampling techniques

1. [[#Probabilistic sampling|Probabilistic sampling]]
	1. [[#Simple random (SRS)|Simple random (SRS)]]
		1. [[#Example|Example]]
	1. [[#Stratified|Stratified]]
		1. [[#Example|Example]]
	1. [[#Systematic|Systematic]]
	1. [[#Clustering|Clustering]]
1. [[#Non-probabilistic sampling|Non-probabilistic sampling]]
	1. [[#Convenience|Convenience]]
	1. [[#Consecutive|Consecutive]]
	1. [[#Intentional|Intentional]]
1. [[#Sampling error|Sampling error]]

---

A **sample** is a subset of a population. It must be _unbiased_ and _representative_

> For demonstration purposes, I'll use the below code for reference, whenever you see "df", I'm talking about the dataframe that contains the data from a file

- In Python:
```python
import numpy as np
import pandas as pd

# Reading data
df = pd.read_csv('data.csv')
```

- In R:
```r
# Dependencies
library(dplyr)

# Reading the database
data <- read.csv('db_path')
```

## Probabilistic sampling
---

### Simple random (SRS)

Guarantees that all the observations have the same chance of being chosen.

- It's _unbiased_ and _representative_, but it can be hard to implement with people, imagine taking random samples from all around the world when a proper database does not exist.

#### Example

- In Python:
```python
# Get the size of the population and produce a smaller subset (the size of it must be determined by the researcher)
size = df.shape[0]
prop = 0.1
simple_sample = df.sample(n = int(size * prop))
```

- In R:
```r
# Get the size of the population and produce a smaller subset
size <- nrow(data)
prop_1 <- 0.1
simple_sample_1 <- sample_n(data, as.integer(size * prop_1))
```
---

### Stratified

First the data is divided into strata based on some property, should it be age, ethnicity, gender depends upon the researcher. After the data has been separated into these _subsets_, a random sample is taken from each of them; sometimes the original proportion is maintained. 

- It's _unbiased_ and _representative_
- It might be hard to implement, since there needs to be a very good documentation on the database to select a proper strata

Example:

![[Pasted image 20220224141919.png]]

#### Example

- In Python:
```python
def stratified_sample_gen(df: pd.DataFrame, key: str, n: int) -> pd.DataFrame:
	strat_sample = df.groupby(key, group_keys=False).apply(lambda x: x.sample(n))
	return strat_sample

stratified_sample = stratified_sample_gen(df, 'INTUBADO', 10)
```

- In R:
```r
library(sampling)

stratified_sample <- strata(data, stratanames=c('INTUBADO'), size=c(10, 10, 10, 10), method="srswor")
```
---

### Systematic

It systematically chooses the n-th case of the population.

- In Python:
```python
def systematic_sampling(df, step: int) -> pd.DataFrame:
 	i = np.arange(0, df.shape[0], step)
 	systematic_sample = df.iloc[i]
 	return systematic_sample

sys_sample = systematic_sampling(df, 27)
```

- In R:

---

### Clustering

First divide the population into clusters (no need to make the clusters based on some characteristic). Then, a random sample is made of $n$ clusters. So, say you divide a population into 10 clusters, you would then randomly select 2 clusters from those 10. And then, your sample will be all the individuals on those 2 selected clusters.

- In Python

```python
def cluster_sampling(df: pd.DataFrame, n: int) -> pd.DataFrame:
	clusters = np.random.choice(np.arange(1, df.shape[0]), size=n, replace=False)
	cluster_sample = df[df.isins(clusters)]
	return cluster_sample
```

---

## Non-probabilistic sampling

- Need further explanations from teacher
- 
---

### Convenience

As the title says, you just do what is easy! For example, you just survey the 10 first persons you come across. It's biased and not representative, but for a short and informal study, it might just be enough.

This classification also contains the case where people choose to participate because they have an interest on the topic.

![[Pasted image 20220225141541.png]]

---

### Consecutive

---

### Intentional

---

## Sampling error

Must investigate further

---