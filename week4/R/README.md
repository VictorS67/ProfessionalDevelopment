# the basis of models in R
## Introduction
The final goal of every model is all the same: to provide a simple low-dimensional summary of a dataset. 
In this week, we’re going to introduce some very common and useful models to partition data into patterns and residuals. 
Usually speaking, strong patterns will hide subtler trends, so we’ll use models to help peel back layers of structure as we explore a dataset.
However, before we can start using models on interesting, real, datasets, you need to understand the basics of how models work. 

### There are two parts to a model:

1. First, you define a family of models that express a precise but generic, pattern that you want to capture. 
For example, the pattern might be a straight line, or a quadratic curve. 
You will express the model family as an equation like y = a_1 * x + a_2 or y = a_1 * x ^ a_2. 
Here, x and y are known (and commonly used) variables from your data, and a_1 and a_2 are parameters that can vary to capture different patterns.

2. Next, you generate a fitted model by finding the model from the family that is the closest to your data. 
This takes the generic model family and makes it specific, like y = 3 * x + 7 or y = 9 * x ^ 2.

### note that:
It’s important to understand that a fitted model is just the closest model from a family of models. That implies that you have the “best” model (according to some criteria); it doesn’t imply that you have a good model and it certainly doesn’t imply that the model is “true”. George Box puts this well in his famous aphorism:

All models are wrong, but some are useful.


# linear regreesion
## What is linear regression?
A linear regression is a statistical model that analyzes the relationship between a response variable (often called y) and one or more variables and their interactions (often called x or explanatory variables). 
You make this kind of relationships in your head all the time, for example when you calculate the weight of an apple based on its size, you are assuming the bigger apple is, the heavier it will be. 
Linear regression is one of the most basic statistical models out there, its results can be interpreted by almost everyone, and it has been around since the 19th century. 
This is precisely what makes linear regression so popular. It’s simple, and it has survived for hundreds of years. Even though it is not as sophisticated as other algorithms like artificial neural networks or random forests, according to a survey made by KD Nuggets, regression was the algorithm most used by data scientists in 2021. It’s even predicted it’s still going to be the used in next 10 year (at least).

## Creating a Linear Regression in R
Not every problem can be solved with the same algorithm. 
In this case, linear regression assumes that there exists a linear relationship between the response variable and the explanatory variables. 
This means that you can fit a line between the two (or more) variables. 
In the previous example (metioned in the intriduction section), it is clear that there is a relationship between the size of apples and their weight.

In this particular example, you can calculate the weight of an apple if you know the size:

### formulated as: weight = a + size∗b

In this case, “a” and “b” are called the intercept and the slope respectively. With the same example, “a” or the intercept, is the value from where you start measuring. New grow apples with zero months are not zero centimeters necessarily; this is the function of the intercept. The slope measures the change of weight with respect to the size in months. In general, for every month older the apple is, its weight will increase with “b”.

Notablely, A linear regression can be calculated in R with the command: 
```
lm()
```
I highly recomend to learn linear regression as the first model in R

### In the next week, I will teach how to use this model to calculate the hwight of apples based on the size of the apple.

