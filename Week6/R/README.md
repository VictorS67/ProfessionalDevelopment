# Week 6 How to read your R output

Linear regression models are a key part of the family of supervised learning models. 
In particular, linear regression models are a useful tool for predicting a quantitative response. 
For more details, please check week 4 and week 5's content!
I’ve written on Simple Linear Regression - An example using R. 
In general, statistical softwares have different ways to show a model output. 
This quick guide will help the analyst who is starting with linear regression in R to understand what the model output looks like.

## examples in R
In the example below, we’ll use the ```cars``` dataset found in the datasets package in R
(for more details on the package you can call: ```library(help = "datasets")```.
```
summary(cars)
``` 
will help us to see data in ```car```

```
##      speed           dist       
##  Min.   : 4.0   Min.   :  2.00  
##  1st Qu.:12.0   1st Qu.: 26.00  
##  Median :15.0   Median : 36.00  
##  Mean   :15.4   Mean   : 42.98  
##  3rd Qu.:19.0   3rd Qu.: 56.00  
##  Max.   :25.0   Max.   :120.00
```
