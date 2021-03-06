# Introduction to Scikit-learn (supervised learning)

## Glance at machine learning

__Machine learning (ML)__ is a kind of artificial intelligence (AI) algorithms which improve their behavior automatically with experience from interaction with the real world. Machine learning algorithm constructs a model with sample data, or more commonly, training data. The model makes predictions with no dependence on explicit programming. The machine learning technology has been widely applied today, include but not limit to computer vision and natural language processing.

## Types of machine learning
- Supervised learning: have labeled examples of the correct behavior, i.e. ground truth input/output response
- Reinforcement learning: learning system receives a reward signal, tries to learn to maximize the reward signal
- Unsupervised learning: no labeled examples – instead, looking for interesting patterns in the data

We will introduce packages Scikit-learn modules on supervised and unsupervised learning.

## Scikit-learn
<div align="center">
  <img src="./logo.png" alt="figure 1: logo" width=50% height=50%/>
</div>


Scikit-learn is a free machine learning library in Python. This library works well with NumPy and SciPy. It supports various kinds of ML algorithms, including:
- Classification: Identifying which category an object belongs to.
  - __Applications__: Spam detection, image recognition.
  - __Algorithms__: SVM, nearest neighbors, random forest, and more
- Regression: Predicting a continuous-valued attribute associated with an object.
  - __Applications__: Drug response, Stock prices.
  - __Algorithms__: SVR, nearest neighbors, random forest, and more...
- Clustering: Automatic grouping of similar objects into sets.
  - __Applications__: Customer segmentation, Grouping experiment outcomes
  - __Algorithms__: k-Means, spectral clustering, mean-shift, and more...
- Dimensionality reduction: Reducing the number of random variables to consider.
  - __Applications__: Visualization, Increased efficiency
  - __Algorithms__: k-Means, feature selection, non-negative matrix factorization, and more...
- Model selection: Comparing, validating and choosing parameters and models.
  - __Applications__: Improved accuracy via parameter tuning
  - __Algorithms__: grid search, cross validation, metrics, and more...
- Preprocessing: Feature extraction and normalization.
  - __Applications__: Transforming input data such as text for use with machine learning algorithms.
  - __Algorithms__: preprocessing, feature extraction, and more...

## Code snippet
```Python
# decision tree algorithm
>>> from sklearn.datasets import load_iris
>>> from sklearn.model_selection import cross_val_score
>>> from sklearn.tree import DecisionTreeClassifier
>>> clf = DecisionTreeClassifier(random_state=0)
>>> iris = load_iris()
>>> cross_val_score(clf, iris.data, iris.target, cv=10)
...                             
...
array([ 1.     ,  0.93...,  0.86...,  0.93...,  0.93...,
        0.93...,  0.93...,  1.     ,  0.93...,  1.      ])

# K-nearest neighbor
>>> import numpy as np
>>> from sklearn.neighbors import NearestNeighbors
>>> samples = [[0, 0, 2], [1, 0, 0], [0, 0, 1]]
>>> neigh = NearestNeighbors(n_neighbors=2, radius=0.4)
>>> neigh.fit(samples)
NearestNeighbors(...)

>>> neigh.kneighbors([[0, 0, 1.3]], 2, return_distance=False)
array([[2, 0]]...)

>>> nbrs = neigh.radius_neighbors(
...    [[0, 0, 1.3]], 0.4, return_distance=False
... )
>>> np.asarray(nbrs[0][0])
array(2)

# linear regression
>>> from sklearn.linear_model import LinearRegression
>>> X = np.array([[1, 1], [1, 2], [2, 2], [2, 3]])
>>> # y = 1 * x_0 + 2 * x_1 + 3
>>> y = np.dot(X, np.array([1, 2])) + 3
>>> reg = LinearRegression().fit(X, y)
>>> reg.score(X, y)
1.0
>>> reg.coef_
array([1., 2.])
>>> reg.intercept_
3.0000...
>>> reg.predict(np.array([[3, 5]]))
array([16.])

# bagging (ensemble)
>>> from sklearn.svm import SVC
>>> from sklearn.ensemble import BaggingClassifier
>>> from sklearn.datasets import make_classification
>>> X, y = make_classification(n_samples=100, n_features=4,
...                            n_informative=2, n_redundant=0,
...                            random_state=0, shuffle=False)
>>> clf = BaggingClassifier(base_estimator=SVC(),
...                         n_estimators=10, random_state=0).fit(X, y)
>>> clf.predict([[0, 0, 0, 0]])
array([1])

# support vector machine (linear kernel)
>>> from sklearn.svm import LinearSVC
>>> from sklearn.pipeline import make_pipeline
>>> from sklearn.preprocessing import StandardScaler
>>> from sklearn.datasets import make_classification
>>> X, y = make_classification(n_features=4, random_state=0)
>>> clf = make_pipeline(StandardScaler(),
...                     LinearSVC(random_state=0, tol=1e-5))
>>> clf.fit(X, y)
Pipeline(steps=[('standardscaler', StandardScaler()),
                ('linearsvc', LinearSVC(random_state=0, tol=1e-05))])

>>> print(clf.named_steps['linearsvc'].coef_)
[[0.141...   0.526... 0.679... 0.493...]]

>>> print(clf.named_steps['linearsvc'].intercept_)
[0.1693...]
>>> print(clf.predict([[0, 0, 0, 0]]))
[1]

# adaboost (ensemble)
>>> from sklearn.ensemble import AdaBoostClassifier
>>> from sklearn.datasets import make_classification
>>> X, y = make_classification(n_samples=1000, n_features=4,
...                            n_informative=2, n_redundant=0,
...                            random_state=0, shuffle=False)
>>> clf = AdaBoostClassifier(n_estimators=100, random_state=0)
>>> clf.fit(X, y)
AdaBoostClassifier(n_estimators=100, random_state=0)
>>> clf.predict([[0, 0, 0, 0]])
array([1])
>>> clf.score(X, y)
0.983...
```

## Reference
- [Mitchell, Tom](https://en.wikipedia.org/wiki/Tom_M._Mitchell) (1997). [Machine Learning](http://www.cs.cmu.edu/~tom/mlbook.html). New York: McGraw Hill. ISBN 0-07-042807-7. OCLC 36417892.
- "Paraphrasing Arthur Samuel (1959), the question is: How can computers learn to solve problems without being explicitly programmed?" in Koza, John R.; Bennett, Forrest H.; Andre, David; Keane, Martin A. (1996). Automated Design of Both the Topology and Sizing of Analog Electrical Circuits Using Genetic Programming. Artificial Intelligence in Design '96. Springer, Dordrecht. pp. 151–170. doi:10.1007/978-94-009-0279-4_9
- Jimmy Ba [Introduction & Linear Models](https://csc413-2020.github.io/assets/slides/lec01.pdf)
- [Scikit-learning](https://scikit-learn.org/stable/)
- [Scikit-learning (wikipedia)](https://en.wikipedia.org/wiki/Scikit-learn)
- [sklearn.tree.DecisionTreeClassifier](https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html?highlight=decision%20tree#sklearn.tree.DecisionTreeClassifier)
- [sklearn.neighbors.NearestNeighbors](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.NearestNeighbors.html?highlight=k%20nearest#sklearn.neighbors.NearestNeighbors.kneighbors)
- [sklearn.linear_model.LinearRegression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html?highlight=linear%20regression#sklearn.linear_model.LinearRegression)
- [sklearn.ensemble.BaggingClassifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.BaggingClassifier.html?highlight=bagging#sklearn.ensemble.BaggingClassifier)
- [sklearn.svm.LinearSVC](https://scikit-learn.org/stable/modules/generated/sklearn.svm.LinearSVC.html#sklearn.svm.LinearSVC)
- [sklearn.ensemble.AdaBoostClassifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.AdaBoostClassifier.html#sklearn.ensemble.AdaBoostClassifier)
