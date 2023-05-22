---
title: "Introduction to R"
output: 
  html_document: 
    keep_md: yes
date: "2023-05-21"
---




# What is R

R is many things…

- R is a free, open-source language and environment for statistical analysis
- It’s been very popular in academia for more than a decade
- A statistical software that can do simple or complex analyses, similar to SAS or S plus, and which makes really great looking graphs
- R is not just a stats software, it’s a programming language that allows the user to do a limitless number of tasks
- R is open source, so users can make it available to others
   restrictions)
- Widely used in academia, government, and increasingly in industry, especially the biotech and finance sectors.
Here is a link describing the [increasing popularity of R](https://r4stats.com/articles/popularity/).

# R vs. Excel


## Advantages of Excel
- Easy to use
- Familiar
- Easy to sort and scroll through data


## Disadvantages of Excel
- Easy to make a mistake
- Limits on data size, not a huge deal anymore. But with large datasets, can really bog down your computer
- Difficult to perform a series of steps
- Without very very good documentation, difficult to describe steps of an analysis


## Disadvantages of R
- Difficult to use at first
- Figuring out errors can be difficult
- Relies on the user finding answers via Google searches, no structured support
- Often times your colleague may not be familiar with it, so sharing data analyses with them can be difficult


## Advantages of R
- Because you can see all of your steps, much harder to make an error
- If you know the right tricks, almost unlimited size of data
- Easily reproducible and repeatable
- Active user community means lots of internet sources and rapid releases of new technology


## When to Use Excel

- Doing a one-time analysis, small dataset, basic graphics


## When to Use R
- Doing repeated analyses, lots of variables, advanced graphics
- Most likely will begin as a hybrid user and migrate over time


# R and RStudio
- This section covers the two pieces of software you need to download
- R is the core piece
- RStudio is a nice integrated development environment (IDE) that makes it much easier to use R


## R
- To download R, [see this page](https://cran.r-project.org/)
- If you open R itself, it will look very plain
plain R console

![](img/r1.png)

## RStudio
- RStudio makes R a little more user friendly
- It’s free and can be downloaded from the [Posit website](https://posit.co/download/rstudio-desktop/) 
- It’s not necessary to open RStudio to use R, but in these sessions we will assume that RStudio is your interface to R

- When you first open RStudio, this is what you see:

![first opening RStudio](img/rstudio1.png)


- The left panel is the console for R
Type `1 + 1` then hit "Enter" and R will return the answer


![RStudio 1 + 1](img/rstudio2.png)



- It’s a good idea to use a script so you can save your code
- Open a new script by selecting "File" -> "New File" -> "R Script" and it will appear in the top left panel of RStudio


![RStudio open script](img/rstudio3.png)



- This is basically a text document that can be saved (go to "File" -> "Save As")
- You can type and run more than one line at a time by highlighting and clicking the "Run" button on the script tool bar


![RStudio many lines](img/rstudio4.png)

- The bottom right panel can be used to find and open files, view plots, load packages, and look at help pages
- The top right panel gives you information about what variables you’re working with during your R session

# R basics
## Doing math
- Open up a script if you haven’t already (“File” -> “New File” -> “R Script”)
- Try some math by either typing the lines below or copying and pasting the lines into your script


```r
10 + 5
10 - 5
10 * 5
10 / 5
10 ^ 5
```


- Remember, to run the lines, highlight your code and click the "Run" button on the toolbar of the script panel

## Reference table of arithmetic operators

|Operator  |Meaning         |Example |
|:--|:--|:--|
|+         |addition	      |2 + 2   |
|-	       |subtraction     |2 - 2   |
|*         |multiplication  |2 * 2   |
|/	       |division	      |2 / 2   |
|^         |exponentiation  |2 ^ 2   |

## Order of operations

R follows the usual order of arithmetical operations and uses parentheses for grouping operations.


```r
10 - 3 / 5    # R will first do division operation then subtraction
```

```
## [1] 9.4
```


```r
(10 - 3) / 5  # Use parentheses to group and prioritize operations.
```

```
## [1] 1.4
```

## Note on commenting

- To write a comment in your script that will not be evaluated, type # in front of your comment
- The text after# will not be evaluated
- Run all of the code below and see what gets returned in the R console (bottom left panel in RStudio)


```r
# Full line comment
x # partial line comment
```

# Creating objects

- An object is used to store information in R
- To create an object or variable in R we use an arrow symbol pointing left `<-`
- Below we’ve created the variables x and y by assigning some numbers to them


```r
x <- 10
y <- 5
x + y
```

```
## [1] 15
```

_Above, the top panel is what you run in your script, the bottom panel is the output_


- In RStudio, you will see the variables we created in the top right panel


![variables](img/rstudio5.png)

- If you’ve already created a variable, you can replace the value with another value


```r
x
```

```
## [1] 10
```


```r
x <- 20
x
```

```
## [1] 20
```

- In the top right panel you can see that the number stored in the variable x has changed


![variables2](img/rstudio6.png)



- You can basically use anything for a variable name, x, X, x2, my.data, my.text, etc.
- However, there are 3 important naming conventions to remember:
  1. You can’t start your variable with a number.
  2. You can’t use any spaces or special characters ($,%,#,-). Periods (.) are ok.
  3. Capitalization __DOES__ matter in R. That is, R will consider ‘my.data’ and ‘My.data’ or ‘x’ and ‘X’ to be different objects.
- Try running the following code and you will see that in your global environment there are two different objects listed.


```r
x <- 5
X <- 5
```

# R Object types
R has three main object types:

Type                        |  Description      |  Examples
----------------------------|-------------------|-----------
character	                  | letters and words |	"z", "red", "H2O"
numeric	                    | numbers	          |1, 3.14, log(10)
logical                     |	binary            |	TRUE, FALSE


# Grouping Data
There are several ways to group data to make them easier to work with:

- Vectors: contain multiple values of the same type (e.g., all numbers or all words)
- Lists: contain multiple values of different types (e.g., some numbers and some words)
- Matrices: a table, like a spreadsheet, with only one data type
- Data Frames: Like a matrix, but you can mix data types

## Vectors
- Vectors are variables with an ordered set of values
- They contain only one type of data (numeric, character, or logical)
- We use c( ) as a container for vector elements. Think of the c as combining elements.


```r
x <- c(1, 2, 3, 4, 5)
x
```

```
## [1] 1 2 3 4 5
```


```r
fruit <- c("apples","bananas","oranges")
fruit
```

```
## [1] "apples"  "bananas" "oranges"
```

If you try to type in text without using quotations marks (either single or double), R will throw an error. Try the text below.


```r
fruit <- c(apples, bananas, oranges)
fruit
```


This is because R will interpret text without quotes as the names of variables. Since we don’t have any variables named apples, bananas, or oranges, R can’t find them.



# Lists
- Lists are like vectors but can contain any mix of data types
- We use list() as a container for list items


```r
x <- list("Benzene", 1.3, TRUE)
x
```

```
## [[1]]
## [1] "Benzene"
## 
## [[2]]
## [1] 1.3
## 
## [[3]]
## [1] TRUE
```


# Data frames
- Data frames are ‘spreadsheet-like’ tables in R
- We use data.frame() as a container for many vectors of the same length
- Data frames are the most common objects that we work with while analyzing environmental data, but vectors and lists can be important when you start using R as a programming language.


```r
pollutant <- c("Benzene", "Toluene", "Xylenes")
concentration <- c(1.3, 5.5, 6.0)
carcinogen <- c(TRUE, FALSE, FALSE)
my.data <- data.frame(pollutant, concentration, carcinogen)
my.data
```

```
##   pollutant concentration carcinogen
## 1   Benzene           1.3       TRUE
## 2   Toluene           5.5      FALSE
## 3   Xylenes           6.0      FALSE
```


If you try to input a data frame where the elements are not all the same length, this will cause an error


```r
pollutant <- c("Benzene", "Toluene")
concentration <- c(1.3, 5.5, 6.0)
carcinogen <- c(TRUE, FALSE, FALSE)
my.data <- data.frame(pollutant, concentration, carcinogen)
```


Now let’s try some exercises to test our understanding of R basics and data types.

# Exercise 1

