# Week 7 how to write your own report in R

## What do we learned in the previous 6 weeks:
we already spent 6 weeks in the previous sections, and now we are arrived the final section!
We learned why use R, What is R, How to learn R. 
We learned What is R packages, What is linear regression.
We learned how to read our R output.
And now we need to know how to make a good report to share your work with others!

## Where to write a report and How to use it
ususally you can use any edit software to make your report
However, we suggest you to use the RMarkDown software that has been installing in our Rstudio alreay.

### R Markdown
R Markdown is a file format for making dynamic documents with R. 
An R Markdown document is written in markdown (an easy-to-write plain text format) and contains chunks of embedded R code, like the document below:
```
---
output: html_document
---

This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see .

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. 
You can embed an R code chunk like this:

```{r}
summary(cars)
```
```
You can also embed plots, for example:

```{r, echo=FALSE}
plot(cars)
```
```

Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.
```
R Markdown files are designed to be used with the ```rmarkdown``` package. ```rmarkdown``` comes installed with the RStudio IDE, but you can acquire your own copy of ```rmarkdown``` from CRAN with the command:
```
install.packages("rmarkdown")
```
