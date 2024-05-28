# Introduction to R for Air Quality Data Science

This repository contains training materials for learning the R programming language,
specifically tailored towards air quality data science. The training is structured
into distinct lessons, each focusing on a different aspect using R. Each lesson
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


## Data Science and Programming

These lessons are meant to be self-learning materials for air quality data science
using R. It also provides some instructions on how to program with R. These two
topics are related but it's helpful to understand the distinction.

- _Data Science_ is a collection of skills and methods for extracting insights from
data. We are not using this phrase to include machine learning, as many do. In
our use of the term, data science focuses on obtaining, storing, transforming, 
and visualizing data. Basic statistics and quality assurance are also touched on. 

- _Programming_, in our use of the term, is automating tasks using a computer
language. In our case, we want to use R programming to automate air quality data 
science tasks to make our life easier. We also want to use programming to handle
a high volume of data and a wide variety of analyses.

The topics in these lessons are not necessarily divided into data science lessons
and programming lessons. But it may be helpful to keep these two topics separate
in your mind as you progress through the material. Programming topics such as conditionals
and loops (and the R version of loops called `apply` functions) are difficult
to understand at first. However, they are not essential for using R to read air
quality data, transform it, and visualize the output for use in a report or presentation. 
Data science tasks will be more straight forward and they are the main topics in 
these lessons.


## Lessons

1. [Introduction to R](1-Introduction-to-R/readme.md): This lesson provides a 
basic introduction to R, including how to install and set up R and RStudio, an 
overview of R syntax, and how to perform simple operations.

2. [Functions and Importing Data](2-Functions-and-Importing-Data/readme.md): This
lesson covers how to use functions in R, including built-in functions and 
functions from packages. It also discusses how to import data such as text data
in CSV files and 
Excel workbooks.

3. [Subsetting, Sorting, and Combining Data Frames](3-Subsetting-Sorting-and-Combining/readme.md): 
This lesson covers how to subset data using indexing, logical operators, and the
`filter( )` function from `dplyr`. It also covers how to sort and combine data frames.

4. [Writing Functions, Conditionals, and Loops](4-Writing-Functions-Conditionals-and-Loops): 
This lesson introduces the concept of writing functions in R, using conditionals
to control the flow of execution, and implementing loops for repetitive tasks.
    
5. [Plotting](5-Plotting/readme.md): This lesson focuses on visualizing data using
various plotting techniques in R, including scatter plots, line graphs, and histograms.

6. [Basic Statistics](6-Basic-Statistics/readme.md): This lesson covers the basics
of statistical analysis in R, including calculating means, medians, standard deviations,
and correlations.

7. [Quality Assurance](7-Quality-Assurance/readme.md): This lesson discusses quality
assurance in data analysis, including checking data types, handling outliers, dealing
with missing data, and other common pitfalls.

## Contributing

Contributions to this repository are welcome. If you have a suggestion, please open
an issue in this repository and let us know how we can improve the material. You 
can also submit a pull request.

## Resources

Below is a list of helpful resources for learning R:

- [R Basics Cheat Sheet](https://www.datacamp.com/cheat-sheet/getting-started-r)
- [Posit Cheatsheets](https://posit.co/resources/cheatsheets/)
- The R courses on [datacamp.com](https://www.datacamp.com/category/r)
- [R for Data Science](https://r4ds.had.co.nz/)
- AI applications are helpful for answering specific R programming questions, such as [ChatGPT](https://chatgpt.com/) and [Perplexity](https://perplexity.ai).
- Using [GitHub Copilot directly in RStudio](https://docs.posit.co/ide/user/ide/guide/tools/copilot.html) will help you learn R by giving suggestions for how to write your code.


## License

This project is licensed under the MIT License. 
