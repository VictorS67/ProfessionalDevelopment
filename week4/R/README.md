# the basic models in R
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
