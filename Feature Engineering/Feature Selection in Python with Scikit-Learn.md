# Feature Selection in Python with Scikit-Learn
　　Not all data attributes are created equal. More is not always better when it comes to attributes or columns in your dataset.

## Select Features

Feature selection is a process where you automatically select those features in your data that contribute most to the prediction variable or output in which you are interested.

Having too many irrelevant features in your data can decrease the accuracy of the models. Three benefits of performing feature selection before modeling your data are:

- **Reduces Overfitting**: Less redundant data means less opportunity to make decisions based on noise.
- **Improves Accuracy**: Less misleading data means modeling accuracy improves.
- **Reduces Training Time**: Less data means that algorithms train faster.

Two different feature selection methods provided by the scikit-learn Python library are **Recursive Feature Elimination** and **feature importance ranking**.

## Recursive Feature Elimination

The Recursive Feature Elimination (RFE) method is a feature selection approach. It works by **recursively removing attributes and building a model on those attributes that remain**. 
It uses the model accuracy to identify which attributes (and combination of attributes) contribute the most to predicting the target attribute.

This recipe shows the use of RFE on the Iris floweres dataset to select 3 attributes.

```
# Recursive Feature Elimination
from sklearn import datasets
from sklearn.feature_selection import RFE
from sklearn.linear_model import LogisticRegression
# load the iris datasets
dataset = datasets.load_iris()
# create a base classifier used to evaluate a subset of attributes
model = LogisticRegression()
# create the RFE model and select 3 attributes
rfe = RFE(model, 3)
rfe = rfe.fit(dataset.data, dataset.target)
# summarize the selection of the attributes
print(rfe.support_)
print(rfe.ranking_)
```

## Feature Importance

Methods that use ensembles of decision trees (like Random Forest or Extra Trees) can also compute **the relative importance of each attribute**. These importance values can be used to inform a feature selection process.

This recipe shows the construction of an Extra Trees ensemble of the iris flowers dataset and the display of the relative feature importance.

```
# Feature Importance
from sklearn import datasets
from sklearn import metrics
from sklearn.ensemble import ExtraTreesClassifier
# load the iris datasets
dataset = datasets.load_iris()
# fit an Extra Trees model to the data
model = ExtraTreesClassifier()
model.fit(dataset.data, dataset.target)
# display the relative importance of each attribute
print(model.feature_importances_)
```

## Summary

Feature selection methods can give you useful information on the relative importance or relevance of features for a given problem. You can use this information to create filtered versions of your dataset and increase the accuracy of your models.

In this post you discovered two feature selection methods you can apply in Python using the scikit-learn library.
