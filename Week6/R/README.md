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
 As the summary output above shows, the cars dataset’s speed variable varies from cars with speed of 4 mph to 25 mph 
 (the data source mentions these are based on cars from the ’20s! - to find out more about the dataset, you can type ```?cars```). 
 When it comes to distance to stop, there are cars that can stop in 2 feet and cars that need 120 feet to come to a stop.
 
 
 ## example of R output
 Here, I will introduce a example of aR output:
 ```
 ## 
## Call:
## lm(formula = dist ~ speed.c, data = cars)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -29.069  -9.525  -2.272   9.215  43.201 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)    
## (Intercept)  42.9800     2.1750  19.761  < 2e-16 ***
## speed.c       3.9324     0.4155   9.464 1.49e-12 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 15.38 on 48 degrees of freedom
## Multiple R-squared:  0.6511,	Adjusted R-squared:  0.6438 
## F-statistic: 89.57 on 1 and 48 DF,  p-value: 1.49e-12

```
### Formula Call

As you can see, the first item shown in the output is the formula R used to fit the data. 
Note the simplicity in the syntax: the formula just needs the predictor (speed) and the target/response variable (dist), together with the data being used (cars)

### Residuals

The next item in the model output talks about the residuals. 
Residuals are essentially the difference between the actual observed response values (distance to stop dist in our case) and the response values that the model predicted. 
The Residuals section of the model output breaks it down into 5 summary points. When assessing how well the model fit the data, you should look for a symmetrical distribution across these points on the mean value zero (0). 
In our example, we can see that the distribution of the residuals do not appear to be strongly symmetrical. 
That means that the model predicts certain points that fall far away from the actual observed points. 
We could take this further consider plotting the residuals to see whether this normally distributed, etc. but will skip this for this example

### Coefficient - Estimate

The coefficient Estimate contains two rows; the first one is the intercept. 
The intercept, in our example, is essentially the expected value of the distance required for a car to stop when we consider the average speed of all cars in the dataset. 
In other words, it takes an average car in our dataset 42.98 feet to come to a stop. 
The second row in the Coefficients is the slope, or in our example, the effect speed has in distance required for a car to stop. 
The slope term in our model is saying that for every 1 mph increase in the speed of a car, the required distance to stop goes up by 3.9324088 feet.

### Coefficient - Standard Error

The coefficient Standard Error measures the average amount that the coefficient estimates vary from the actual average value of our response variable. 
We’d ideally want a lower number relative to its coefficients. 
In our example, we’ve previously determined that for every 1 mph increase in the speed of a car, the required distance to stop goes up by 3.9324088 feet. 
The Standard Error can be used to compute an estimate of the expected difference in case we ran the model again and again. 
In other words, we can say that the required distance for a car to stop can vary by 0.4155128 feet. The Standard Errors can also be used to compute confidence intervals and to statistically test the hypothesis of the existence of a relationship between speed and distance required to stop.

### Coefficient - t value

The coefficient t-value is a measure of how many standard deviations our coefficient estimate is far away from 0. 
We want it to be far away from zero as this would indicate we could reject the null hypothesis - that is, we could declare a relationship between speed and distance exist. 
In our example, the t-statistic values are relatively far away from zero and are large relative to the standard error, which could indicate a relationship exists. 
In general, t-values are also used to compute p-values.

