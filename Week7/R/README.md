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
R Markdown files are the source code for rich, reproducible documents. You can transform an R Markdown file in two ways.

1. knit - You can knit the file. The ```rmarkdown``` package will call the ```knitr``` package. ```knitr``` will run each chunk of R code in the document and append the results of the code to the document next to the code chunk. This workflow saves time and facilitates reproducible reports.

Consider how authors typically include graphs (or tables, or numbers) in a report. The author makes the graph, saves it as a file, and then copy and pastes it into the final report. This process relies on manual labor. If the data changes, the author must repeat the entire process to update the graph.

In the R Markdown paradigm, each report contains the code it needs to make its own graphs, tables, numbers, etc. The author can automatically update the report by re-knitting.

2. convert - You can convert the file. The ```rmarkdown``` package will use the ```pandoc``` program to transform the file into a new format. For example, you can convert your .Rmd file into an HTML, PDF, or Microsoft Word file. You can even turn the file into an HTML5 or PDF slideshow. ```rmarkdown``` will preserve the text, code results, and formatting contained in your original .Rmd file.


In practice, authors almost always knit and convert their documents at the same time. In this article, I will use the term render to refer to the two step process of knitting and converting an R Markdown file.

You can manually render an R Markdown file with rmarkdown::render(). This is what the above document looks like when rendered as a HTML file.
