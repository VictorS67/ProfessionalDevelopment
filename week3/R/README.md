# How to learn R (in General)
## General introduction (warm up form last week)
Learning R can be difficult and easy at the same time, especially if you have no programming experience or are more familiar working with point-and-click 
statistical software versus a real programming language. 
This learning path is mainly for novice R users that are just getting started 
but it will also cover some of the latest changes in the language that might appeal to more advanced R users.
Step 1: Learn how to Set-Up your own R station in your on device
Step 2: Understanding the R Syntax step bu step
Step 3: Knowing the core of R -> packages
Step 4: The Data Analysis Workflow
step 5: Practice make you perfect

## Learn it step by step!
### Step 3
What is R package in General ?
Every R package is simply a bundle of code that serves a specific purpose and is designed to be reusable by other developers. 
In addition to the primary codebase, packages often include data, documentation, and tests. 
As an R user, you can simply download the particular package (some are even pre-installed since many package will be used very often in R) and start using its functionalities. 
Everyone can develop R packages since the R is a open source and free for downloading, and everyone can share their R packages with others. 
Highly suggets trying to design your own package, it will save your time in the rest of your time of using R and it will dramtically increasing your understanding of R.

The above is an extremely powerful concept and one of the key reasons R is so successful as a language and as a community. 
Namely, you don’t need to do all the hard core programming yourself or understand every complex detail of a particular algorithm or visualization. 
You can simple use the out-of-the box functions that come with the relevant package as an interface to such functionalities.  
As such it is useful to have an understanding of R’s package ecosystem.

Many R packages are available from the Comprehensive R Archive Network, and you can install them using the install.packages function. 
What is great about CRAN is that it associates packages with a particular task via Task Views. 
Alternatively, you can find R packages on bioconductor, github and bitbucket.

Looking for a particular package and corresponding documentation? 
Try Rdocumentation, where you can easily search packages from CRAN, github and bioconductor.

### Step 4
Once you have an understanding of R’s syntax, the package ecosystem, and how to get help, 
it’s time to focus on how R can be useful for the most common tasks in the data analysis workflow!

1. Importing Data
Before you can start performing analysis, you first need to get your data into R. 
The good thing is that you can import into R all sorts of data formats, the hard part this is that different types often need a different approach:

to read flat files: use read.table() or read.csv
to read excel file, you will need: either the readxl package, the gdata package and XLConnect package. (Read more on importing your excel files into R)
to read SAS, STATA and SPSS data files into R: The foreign package lets you import formats like Systat and Weka
to web scraping: you can use packages like rvest. (For more info on web scraping with R check the blog of Rolf Fredheim.)

2. Data Manipulation
Performing data manipulation with R is a broad topic as you can see in for example this Data Wrangling with R video by RStudio or the book Data Manipulation with R. 
This is a list of packages in R that you should master when performing data manipulations, and the rest of this develpment project will be focused mostly on Data manipulation!

3. ploting data and make a report
if you finish importing and sorting, you can fit in models and find a answer for you research question. After that you will need to plot you data and make a report for your project.
This will also be a seperate section in this project!
