---
layout: post
title: Machine Learning Definitions
date: 2025-03-30 11:59:00-0400
description: Notes from various different sources/material related to ML
tags: ml
categories: ml
giscus_comments: false
related_posts: false

toc:
  beginning: true
---

### Principal Component Analysis (PCA)

The Principal Component Analysis (PCA) is a tool that allows data scientists to reduce dimensionality of a large dataset using something called principal components (PC). PCA is not really a recent topic, it was created in 1901 by Karl Pearson. Modern machinery and algorithms enable us to use it today at scale. 

### Dimension Reduction

Some approaches to dimension reduction include consolidation and embedding, all-possible subsets, and the Principal Component Analysis (PCA). 

### Consolidation and Embedding

While economists use proxy variables: say we want data on some variable U, but we don't have data on it, we substitute another variable (let's call that one V) which is very similar to U. V is a proxy of U. 

In ML, the related technique is called consolidation and embedding. For dimension reduction, proxies can be used to help reduce dimensionality of categorical variables. 

Encoding: when you take data from outside the data set to replace a feature

### The All Possible Subsets Method
When we want to choose a solid feature set, we can look at all posssible subsets of features. You'd find the MAPE or OME for each one and select the subset that minimizes that value.

### Grid Search

Many ML packages include the functionality to complete a _grid search_. Grid search means evaluating all possible hyperparameter combinations. Unfortunately, the number of combinations can be so large that a full grid search would take an extraordinarily long time to run. 

Some grid search packages attempt to rectify this by evaluating only promising combinations. To achieve this, they'd have to iteratively search through narrow parts of the grid. For each iteration, the algorithm updates its guess on what to try. This can save time but can, as a result, have the algorithm go the wrong direction. 

Another name for hyperparameters is _tuning parameters_ -- a pun referencing the old radio days when you'd literally tune the frequency to a precise station, known as fine tuning.

### Confidence Intervals

Confidence intervals keep us honest, reminding us that values we see in certain ML functions are only approximate. When we construct a large # of CI's, the overall validity declines. For example, CIs set individually at 95% level have a lower overall confidence level. The reason being is that each time you're estimating something at 95% lowers the probability of it being 95% again, and so on. 

The __Bonferroni-Dunn__ CI is often seen as a column alongside the normal CI. This gives us alternative CIs that take into consideration us having many random CIs. For example, the highest discrepancy the Bonferroni-Dunn CI has with the normal CI, the greater risk there is (that it's not a valid number).


### Regularization (shrinkage)

Without going into the math details (to spare me from typing LaTeX [no offense to any mathematicians]), I'll type out most of the important bits. 

The __James-Stein__ theory says the best estimate of mew (the estimator representing a population's means) isn't actually X-bar (the estimator representing a sample's means), but a reduced version of X-bar. The reason is that samples can contain data that are outliers, so reducing it will actually take the outliers somewhat in account. __The higher the dimensions the more shrinking needs to be done__. 

In addition, different components of the vector can be shrunk by different amounts (including expansion), the reason being is that _shrinking_ refers to the size of the entire vector, not a specific component. How much shrinking is done is usually decided by __cross-validation__. 

An additional reason why shrinkage/regularization has had a huge impact on statistics and machine learning is because its a tool that can be used to avoid overfitting. This can be a double edged sword, for example:
1. We want to make the prediction sum of squares as small as possible (eliminating bias).
2. The sum of squares can be optimistic (the values are usually very high). This can lead to the sum having a large variance, partly because of extreme data points. Shrinkage reduces variance because smaller quantities usually vary less than larger ones (balancing out the outliers).

The hyperparameter lambda is used to control where we want to be between the aforementioned points. Overfitting may also occur if the hyperparameter is off.

__To recap: shrinkage usually reduces variance, and we'll accept the shrinkage if it can be done without increasing bias much. Regularization is used in not just linear models, but also in support vector machines, neural nets, PCA, etc.__