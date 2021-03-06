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

## Reference
- [Mitchell, Tom](https://en.wikipedia.org/wiki/Tom_M._Mitchell) (1997). [Machine Learning](http://www.cs.cmu.edu/~tom/mlbook.html). New York: McGraw Hill. ISBN 0-07-042807-7. OCLC 36417892.
- "Paraphrasing Arthur Samuel (1959), the question is: How can computers learn to solve problems without being explicitly programmed?" in Koza, John R.; Bennett, Forrest H.; Andre, David; Keane, Martin A. (1996). Automated Design of Both the Topology and Sizing of Analog Electrical Circuits Using Genetic Programming. Artificial Intelligence in Design '96. Springer, Dordrecht. pp. 151–170. doi:10.1007/978-94-009-0279-4_9
- Jimmy Ba [Introduction & Linear Models](https://csc413-2020.github.io/assets/slides/lec01.pdf)
- [Scikit-learning](https://scikit-learn.org/stable/)
- [Scikit-learning (wikipedia)](https://en.wikipedia.org/wiki/Scikit-learn)
