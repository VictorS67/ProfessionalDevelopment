# Linear REgression
## Howt o build your linear regression model on R
Last week we introduced the basis of models in R and we are talked a little on the topic of linear regreesion.
This week, we will continue to learn Linear regression and also continue to solve the example from last week!

In the previous example, we clearlt state that there is a relationship between the size of an apple and its weight
we also formulated the linear relation as:
### Weight= a + size∗b

And to know those informations, we can now open our R or Rstudio (As suggested in the last few weeks) and do the real R stuff!

1. import the library 
```readxl``` 
to read Microsoft Excel files, it can be any kind of format, as long R can read it. 
2. create the linear regression in lines. The 
```
lm
```
command takes the variables in the format: 
### lm([target variable] ~ [predictor variables], data = [data source])
3. use the fuction 
```
summary()
```
you can see all the collected informationa and sorted informations!

## example of linear regression model in R
```
library(readxl) #In order to use the read fuction

name_of_your_data <- read_excel("xxx.xls") #Upload the data
name_of_your_linearmodel = lm(weight~size, data = name_of_your_data) #Create the linear regression
summary(name_of_your_model) #Review the results
```
