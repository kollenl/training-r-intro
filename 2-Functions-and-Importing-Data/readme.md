---
title: "Functions and Importing Data"
output: 
  html_document: 
    keep_md: yes
date: "2023-08-18"
---


This lesson covers the use of functions in R, including built-in functions and 
functions from packages. It also discusses how to import data from CSV text
files and Excel documents.

- [Functions](#functions)
- [Useful Built-in Functions](#useful-built-in-functions)
- [Packages](#packages)
- [Importing Data](#importing-data)
- [Exercises](#exercises)

# Functions

In R, there are two main types of objects: variables and functions. We covered 
variables in the [introductory lesson](../1-Introduction-to-R/readme.md). A variable
is used to create and reference data. The data can be a character, numeric, or 
logical data type. Variables can reference various "containers" for data, such as
a __vector__, __list__, or __data frame__. 

Functions are similar to variables in that they are short names that reference
something saved in R. In this case, a function is not referencing data but a piece
of code. A function is saved code that can be used to do some operation on data.

R has many built-in functions that perform common tasks. When you open RStudio
you can immediately use a function called `mean( )`. Here is an example of using
the `mean( )` function to find the average of a vector of integers. We first
save a vector of integers in the `x` variable then put the variable inside the
parentheses of the function.


```r
x <- c(4, 8, 1, 14, 34)

mean(x)
```

```
## [1] 12.2
```

As you would expect, R has many built-in math functions. Below
are a series of examples.


```r
log(27)  #Natural logarithm
```

```
## [1] 3.295837
```


```r
log10(100) #base 10 logarithm
```

```
## [1] 2
```


```r
sqrt(225) # Square root 
```

```
## [1] 15
```


```r
abs(-5) #Absolute value 
```

```
## [1] 5
```

All of the examples show that the general form is `function_name( )`. The name
of the function should give you some clue as to what it does, and the `( )`
is where you provide the data to the function. 

Many functions also have additional options you can choose, which are called the 
_arguments_. To see what needs to go inside `( )`, type a 
question mark in front of the function and run it in the R console.


```r
?mean()
```

In RStudio, you will see the help page for `mean()` in the bottom right corner panel.

![](img/rstudio_help.png)


On the help page, under `Usage`, you see `mean(x, ...)`. This means that the only 
thing that necessarily has to go into `( )` is `x`. On the help page under `Arguments`
you will find a description of what `x` needs to be: a numeric or logical vector. 

Many built-in functions in R have multiple arguments. This allows you to give the 
function some more information to perform calculation you want. The example below
shows how to use the `digits` argument in the `round( )` function. Providing 
different values to the `digits` argument will return different values.


```r
round(12.3456) 
```

```
## [1] 12
```


```r
round(12.3456, digits=3)  
```

```
## [1] 12.346
```


```r
round(12.3456, digits=1)
```

```
## [1] 12.3
```
In the first example, you can see that we did not provide a value for the 
`digits` argument. That's because there is a default value `digits = 0` (see
the `Usage` section on the help page `?round`). If there is a default value,
then that argument does not need to be specified inside `( )`. If there is no
default value for an argument, then the function will error and tell you that
you forgot to supply a value for the argument.


# Useful Built-in Functions

When you start an R session there are many built-in functions that are immediately
available for you to use. Other functions are available in community developed
packages, as explained in a later section of this lesson. Below is a list of a 
few commonly used built-in functions in R.

### 1. `sum( )` 
Returns the sum of a vector of numeric values.


```r
sum(c(2.3, 7.5, 9, -10))
```

```
## [1] 8.8
```

### 2. `min()`
Get the minimum value from a numeric vector.


```r
min(c(6, 9, 3, 11, -2))
```

```
## [1] -2
```
### 3. `max()`
Get the maximum value from a numeric vector.


### 4. `seq()`
Create a numeric vector with a certain sequence. The example below creates a 
vector of integers from 1 to 5.


```r
seq(from = 1, to = 5, by = 1)
```

```
## [1] 1 2 3 4 5
```

Another way to create a sequence of integers is to use the colon.


```r
1:5
```

```
## [1] 1 2 3 4 5
```



### 5. `paste()`
Concatenate two or more strings. 


```r
x <- "Hello"
y <- "world!"
paste(x, y, sep = " ")
```

```
## [1] "Hello world!"
```

Any numbers will be converted to strings.


```r
x <- "You're number "
y <- 1
z <- "!"
paste(x, y, z, sep = "")
```

```
## [1] "You're number 1!"
```


### 6. `substr()`
The `substr()` function allows you to pull out a section from a string
based on the position of the characters in the string. This is useful for vectors
of dates, addresses, monitor IDs, parameter descriptions, etc.

For example, in AQS data a monitor ID may be written in the following format: 

> [State code - County code - Site number - Parameter code - POC]. 

If we only wanted to pull out the site number for this monitor ID we could do the following:


```r
wisconsin_monitor <- c('55-021-0015-44201-2')  # Ozone monitor in Columbia County, WI
site_id <- substr(wisconsin_monitor, start = 8, stop = 11)  # start and stop position within the character string.
site_id
```

```
## [1] "0015"
```


## Nesting functions
R allows you to place a function inside another function to perform multiple tasks 
on data in one step.

For instance, if you want to create a sequence of numbers and then take the mean
of that sequence, you could either do it in a couple of steps, or all at once.


```r
#Two steps
x <- seq(from=1, to=10, by=3)
mean(x)
```

```
## [1] 5.5
```


```r
#One step
mean(seq(from=1, to=10, by=3))  
```

```
## [1] 5.5
```

_Note: Typically you don’t want to have too many nested functions because it becomes difficult to read._

# Packages

R comes with basic functionality, meaning that some functions will always be 
available when you start an R session. But anyone can write functions for R that
are not part of the base functionality and make it available to other R users in
a package.


Packages must be installed on your computer first then loaded before using it.
This is similar to a mobile app: you must first install the R package (like first
downloading an app) then you must load the package before using its functions 
(like opening an app to use it). 

If base R doesn't have a function you need, the best thing to do is a Google
search. Use a search with key words describing what you want the function to do 
and just add "R package" at the end.

For example, if you wanted to  find serial correlation in an environmental data 
set, Google would tell you that the R package `EnvStats` has a function called
`serialCorrelationTest()`.

First, you might try to use the function.


```r
x <- c(1.3, 3.5, 2.6, 3.4, 6.4)
serialCorrelationTest(x)
```

```
## Error in serialCorrelationTest(x): could not find function "serialCorrelationTest"
```

It's not available because we need to install the package first (again, like 
initially downloading an app).

In the bottom right panel of RStudio, click on the "Packages" tab then click
"Install Packages" in the tool bar.

![](img/rstudio_install_package.png)

A window will pop up. Start typing "EnvStats" into the "Packages" box, select that 
package, and click "Install". 

![](img/rstudio_install_package2.png)

Now that we've installed the package, we still can't use the function we want.
We need to load the package first (opening the app). We use the `library()` function
to do this.


```r
library(EnvStats)
```


Now we can use the function we want.


```r
x <- c(1.3, 3.5, 2.6, 3.4, 6.4)
serialCorrelationTest(x)
```

```
## 
## Results of Hypothesis Test
## --------------------------
## 
## Null Hypothesis:                 rho = 0
## 
## Alternative Hypothesis:          True rho is not equal to 0
## 
## Test Name:                       Rank von Neumann Test for
##                                  Lag-1 Autocorrelation
##                                  (Exact Method)
## 
## Estimated Parameter(s):          rho = -0.0187589
## 
## Estimation Method:               Yule-Walker
## 
## Data:                            x
## 
## Sample Size:                     5
## 
## Test Statistic:                  RVN = 1.8
## 
## P-value:                         0.7833333
## 
## Confidence Interval for:         rho
## 
## Confidence Interval Method:      Normal Approximation
## 
## Confidence Interval Type:        two-sided
## 
## Confidence Level:                95%
## 
## Confidence Interval:             LCL = -0.8951272
##                                  UCL =  0.8576094
```

Here is a link to a page that lists many useful packages for environmental data
analysis: https://cran.r-project.org/web/views/Environmetrics.html

Remember, when you close down RStudio, then start it up again, you don’t have to
download the package again. But you do have to load the package to use any function
that's not in the R core functionality (this is very easy to forget).


# Importing Data

R can import data from just about any format, including
  - CSV
  - Excel
  - Databases
  - GIS shapefiles
  
This section will demonstrate how to import CSV and Excel files. 
  
## CSV

R has a built-in function called `read.csv()` for reading `.csv` files. Download
the `chicago_daily.csv` file [here](../data/chicago_daily.csv) and save it to your
working directory. If you don't know what your working directory is, run this
code in R and it will tell you.


```r
getwd()
```

Use `read.csv()` by providing the location and name of the file as the first
argument. If the file is in your working directory, simply supply the name of the 
file. Below, the data from the file is read into R and saved as a data frame,
which is the data type for storing tables. The function `head()` will show the 
first few lines.


```r
chicago_daily <- read.csv("chicago_daily.csv")
head(chicago_daily)
```


```
##         date  no2 ozone pm25 so2
## 1 2021-02-06 19.1    NA  4.2 1.5
## 2 2021-02-07 28.7    NA  9.0 3.1
## 3 2021-02-08 51.2    NA 34.6 5.1
## 4 2021-02-09 49.3    NA 16.8 4.6
## 5 2021-02-10 46.0    NA 15.6 3.2
## 6 2021-02-11 39.5    NA 13.1 2.0
```
  
## Excel

There are several packages that can be used to import data from an Excel file,
such as `xlsx`, `XLConnect`, and `readxl`. In this example, we'll use the `readxl`
package. If you do not have the package installed, you can use RStudio to install
as described in the section above on packages. You can also use the function
`install.packages( )`.


```r
install.packages("readxl")
```

Once you have the package installed, remember to load the package by using
the `library()` function.


```r
library(readxl)
```


Use the `read_excel()` function from the `readxl` package to read emissions data 
from [this Excel workbook](../data/emissions_IL_2022.xlsx).
Download the file to your working directory and read the first worksheet (named
"UNIT_DATA"), skipping the first 6 rows. 




```r
emissions <- read_excel("emissions_IL_2022.xlsx", sheet = "UNIT_DATA", skip = 6)
head(emissions)
```


```
## # A tibble: 6 × 17
##   `Facility Id` `FRS Id`     `Facility Name`    City  State `Primary NAICS Code`
##           <dbl> <chr>        <chr>              <chr> <chr> <chr>               
## 1       1003742 110043790804 31st Street Landf… WEST… IL    562212              
## 2       1003742 110043790804 31st Street Landf… WEST… IL    562212              
## 3       1003742 110043790804 31st Street Landf… WEST… IL    562212              
## 4       1003742 110043790804 31st Street Landf… WEST… IL    562212              
## 5       1003742 110043790804 31st Street Landf… WEST… IL    562212              
## 6       1003742 110043790804 31st Street Landf… WEST… IL    562212              
## # ℹ 11 more variables: `Reporting Year` <dbl>,
## #   `Industry Type (subparts)` <chr>, `Industry Type (sectors)` <chr>,
## #   `Unit Name` <chr>, `Unit Type` <chr>, `Unit Reporting Method` <chr>,
## #   `Unit Maximum Rated Heat Input (mmBTU/hr)` <dbl>,
## #   `Unit CO2 emissions (non-biogenic)` <dbl>,
## #   `Unit Methane (CH4) emissions` <dbl>,
## #   `Unit Nitrous Oxide (N2O) emissions` <dbl>, …
```

# Next Lesson

The next lesson in this series is on 
[Subsetting, Sorting, and Combining Data Frames](../3-Subsetting-Sorting-and-Combining/readme.md).

# Exercises

Try these exercises to test your comprehension of material in this lesson.

### Exercise 1

Use the `seq()` function to create a vector from 1 to 20 by 2. For help with the
parameters, run `?seq()` in the console and use the documentation.

<details><summary>Click for Solution</summary>

> In the `seq()` function, set `by = 2`.

#### Solution


```r
seq(from = 1, to = 20, by = 2)
```

```
##  [1]  1  3  5  7  9 11 13 15 17 19
```

</details>

---

### Exercise 2

Use the `round( )` to round the number 13.5678 to two digits after the decimal
point.

<details><summary>Click for Solution</summary>

> Set the `digits` parameter to 2.

#### Solution


```r
round(3.5678, digits=2)
```

```
## [1] 3.57
```

</details>

---

### Exercise 3

Concatenate the strings "Hello" and "R" using the `paste()` function.

<details><summary>Click for Solution</summary>

#### Solution


```r
paste("Hello", "R")
```

```
## [1] "Hello R"
```

</details>

---

### Exercise 4 

Sum the numbers 1 through 10 using the `sum()` function.

<details><summary>Click for Solution</summary>

> Use `:` to create the sequence of integers and place it inside the `sum()` function.

#### Solution


```r
sum(1:10)
```

```
## [1] 55
```

</details>

---

### Exercise 5

Read in the first 10 rows of the `chicago_daily.csv` file [here](../data/chicago_daily.csv).

<details><summary>Click for Solution</summary>

> Save the file to  your working directory and use `nrows = 10` in the `read.csv()`
function

#### Solution


```r
read.csv("chicago_daily.csv", nrows = 10)
```


```
##          date  no2 ozone pm25 so2
## 1  2021-02-06 19.1    NA  4.2 1.5
## 2  2021-02-07 28.7    NA  9.0 3.1
## 3  2021-02-08 51.2    NA 34.6 5.1
## 4  2021-02-09 49.3    NA 16.8 4.6
## 5  2021-02-10 46.0    NA 15.6 3.2
## 6  2021-02-11 39.5    NA 13.1 2.0
## 7  2021-02-12 36.0    NA  9.8 2.1
## 8  2021-02-13 24.9    NA 11.0 1.9
## 9  2021-02-14 17.6    NA  9.0 1.9
## 10 2021-02-15 22.6    NA  3.3 1.7
```


