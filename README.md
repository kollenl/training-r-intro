# Introduction to R for Air Quality Data Science

This repository contains training materials for learning the R programming language,
specifically tailored towards air quality data science. The training is structured into
distinct lessons, each focusing on a different aspect using R. Each lesson
is contained in a separate folder, and includes a README.md file with the lesson 
material.

## Prerequisites

These lessons do not assume that you have any experience using R or any other 
programming language. It does assume that you have some familiarity with air
quality data. Below is a list of software and R packages that are used 
throughout the lessons.

- [R](https://cran.r-project.org/): The statistical programming language. See
the [Introduction to R](1-Introduction-to-R/readme.md) lesson for instructions
on downloading.

- [RStudio](https://posit.co/download/rstudio-desktop/): The integrated development
environment. See the [Introduction to R](1-Introduction-to-R/readme.md) lesson 
for instructions on downloading.

- `region5air`: The R package with air quality data used throughout the lessons.
See [install instructions on GitHub](https://github.com/FluentData/region5air/blob/main/README.md).

- `tidyverse`: The R package that installs a series of "tidyverse" packages.
See the [package site for install instructions](https://www.tidyverse.org/packages/).

## Data Science and Programming

These lessons are meant to be self-learning materials for air quality data science
using R. It also provides some instructions on how to program with R. These two
topics are related but it's helpful to understand the distinction.

- _Data Science_ is a collection of skills and methods for extracting insights from
data. We are not using this phrase to include machine learning, as many do. In
our use of the term, data science focuses on obtaining, storing, transforming, 
and visualizing data. Modeling data and communicating results are also aspects
of data science that we also touch on. 

- _Programming_, in our use of the term, is automating tasks using a computer
language. In our case, we want to use programming to automate data science tasks
to make our life easier. We also want to use programming to handle a high volume
of data and a wide variety of analyses.

The topics in these lessons are not necessarily divided into data science lessons
and programming lessons. But it may be helpful to keep these two topics separate
in your mind as you progress through the material. Programming topics such as conditionals
and loops (and the R version of loops called `apply` functions) are difficult
to understand at first. However, they are not essential for using R to read air
quality data, transform it, and visualize the output for use in a report or presentation. 
Data science tasks will be more straight forward and they are the main topics in 
these lessons.


## Lessons

1. [Introduction to R](1-Introduction-to-R/readme.md): This lesson provides a basic introduction to R, including how to install and set up R and RStudio, an overview of R syntax, and how to perform simple operations.

2. [Functions and Importing Data](2-Functions-and-Importing-Data/readme.md): This lesson covers the use of functions in R, including built-in functions and how to create your own. It also discusses how to import data from various formats, such as CSV and Excel, and how to explore and manipulate this data in R.

3. [Data Exploration and Visualization](3-Subsetting-Sorting-and-Dates/readme.md): This lesson covers how to subset data using indexing and logical operators, sort data using the `order()` function, and combine data frames using `rbind()` and `cbind()` functions in R.

4. [Writing Functions, Conditionals, and Loops](4-Writing-Functions-Conditionals-and-Loops): This lesson introduces the concept of writing functions in R, using conditionals to control the flow of execution, and implementing loops for repetitive tasks.
    
5. [Plotting](5-Plotting/readme.md): This lesson focuses on visualizing data using various plotting techniques in R, including scatter plots, line graphs, and histograms.

6. [Basic Statistics](6-Basic-Statistics/readme.md): This lesson covers the basics of statistical analysis in R, including calculating means, medians, standard deviations, and correlations.

7. [Regression and Data Transformation](7-Regression-and-Data-Transformation/readme.md): This lesson explores the use of linear regression to understand relationships between variables, and how to transform data to fit linear models.

8. [Quality Assurance](8-Quality-Assurance/readme.md): This lesson discusses quality assurance in data analysis, including checking data types, handling outliers, dealing with missing data, and other common pitfalls.

## Contributing

Contributions to this repository are welcome. If you have a suggestion for improvement,
please open an issue to discuss it before making any changes.

## License

This project is licensed under the MIT License. 
