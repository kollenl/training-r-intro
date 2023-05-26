---
title: "Functions and Importing Data"
output: 
  html_document: 
    keep_md: yes
date: "2023-05-22"
---



# Functions

- Functions are a way to repeat the same task on different data. 
- R has many built-in functions that perform common tasks


```r
x <- c(4, 8, 1, 14, 34)
mean(x) # Calculate the mean of the data set
```

```
## [1] 12.2
```


```r
y <- c(1, 4, 3, 5, 10, NA)
mean(y, na.rm = TRUE) # Tell the mean function to remove missing data before calculating
```

```
## [1] 4.6
```


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

- They all have the form `function()`
- `function` is the name, which usually gives you a clue about what it does (such as the `mean()` function)
- `()` is where you put your data or indicate options. These are referred to as the _arguments_ of the function.
- To see what goes inside `()`, type a question mark in front of the function and run it


```r
?mean()
```

In RStudio, you will see the help page for mean() in the bottom right corner help page

![](img/rstudio_help.png)

- On the help page, under `Usage`, you see `mean(x, ...)`
- This means that the only necessary thing that has to go into `()` is `x`
- On the help page under `Arguments` you will find a description of what `x `needs to be
- You can also use functions in combination with objects you have created


```r
answer <- 1+1
log(25 + answer)
```

```
## [1] 3.295837
```

Many built-in functions in R have multiple arguments, so you have to give the function some more information so that it can perform the correct calculation.


```r
round(12.3456) # default is to round to the nearest integer
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


## Other Common and Useful Functions
### `seq()`
The `seq()` function is used to create a vector with a certain sequence. This is used a lot when writing functions. seq(from = 1, to = 1, by = )


```r
seq(1, 5, by = 1)
```

```
## [1] 1 2 3 4 5
```


```r
x <- 1:5  # the colon is a shortcut to create a sequence of integers by 1
x
```

```
## [1] 1 2 3 4 5
```


### `paste()`
The paste function will concatenate two or more strings. Paste only works with 
characters so if you give it numbers to paste, it will convert them to characters first.


```r
x <- "Hello"
y <- "world!"
paste(x, y, sep = " ")
```

```
## [1] "Hello world!"
```


```r
x <- "You're number "
y <- 1
z <- "!"
z <- paste(x, y, z, sep = "")
```


### `substr()`
The `substr()` function allows you to pull out only the elements you care about 
in a character vector of dates, addresses, monitor IDs, parameter descriptions, etc.

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
You can place a function inside another function to perform multiple tasks on data in one step.

For instance, if you want to create a sequence of numbers and then take the mean of that sequence,
you could either do it in a couple of steps, or all at once.


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
mean(seq(from=1, to=10, by=3))  #Make sure you have the parentheses located in the correct spot as R will evaluate from the inside out.
```

```
## [1] 5.5
```

_Note: Typically you don’t want to have too many nested functions because it becomes difficult to read._

# Packages

- R comes with basic functionality, meaning that some functions will always be available when you start an R session
- However, anyone can write functions for R that are not part of the base functionality and make it available to other R users in a package
- Packages must be installed first then loaded before using it
- This is similar to a mobile app: you must first install the R package (like first downloading an app) then you must load the package before using its functions (like opening an app to use it)
- If base R doesn’t have a function you need, just ask Google. Use a search with key words describing what you want the function to do and just add "R package" at the end

For example, if you wanted to  find serial correlation in an environmental data set,
Google would tell you that the R package `EnvStats` has a function called `serialCorrelationTest()`.

First, you might try to use the function.


```r
x <- c(1.3, 3.5, 2.6, 3.4, 6.4)
serialCorrelationTest(x)
```

```
## Error in serialCorrelationTest(x): could not find function "serialCorrelationTest"
```

It’s not available because we need to install the package first (again, like initially downloading an app).

In the bottom right panel of RStudio, click on the "Packages" tab then click "Install Packages" in the tool bar packages.

![](img/rstudio_install_package.png)

A window will pop up. Start typing "EnvStats" into the "Packages" box, select that 
package, and click "Install". 

![](img/rstudio_install_package2.png)

Now that we’ve installed the package, we still can’t use the function we want.
We need to load the package first (opening the app). We use the `library()` function
to do this.


```r
install.packages("EnvStats")
library(EnvStats)
```


Now we can use the function we want


```r
x <- c(1.3, 3.5, 2.6, 3.4, 6.4)
serialCorrelationTest(x)
```

```
## $statistic
## RVN 
## 1.8 
## 
## $parameters
## NULL
## 
## $p.value
## [1] 0.7833333
## 
## $estimate
##        rho 
## -0.0187589 
## 
## $estimation.method
## [1] "Yule-Walker"
## 
## $null.value
## rho 
##   0 
## 
## $alternative
## [1] "two.sided"
## 
## $method
## [1] "Rank von Neumann Test for\n                                 Lag-1 Autocorrelation\n                                 (Exact Method)"
## 
## $sample.size
## [1] 5
## 
## $data.name
## [1] "x"
## 
## $bad.obs
## [1] 0
## 
## $interval
## $name
## [1] "Confidence"
## 
## $parameter
## [1] "rho"
## 
## $limits
##        LCL        UCL 
## -0.8951272  0.8576094 
## 
## $type
## [1] "two-sided"
## 
## $method
## [1] "Normal Approximation"
## 
## $conf.level
## [1] 0.95
## 
## attr(,"class")
## [1] "intervalEstimate"
## 
## attr(,"class")
## [1] "htestEnvStats"
```

Here is a link to a page that lists many, many useful packages for environmental data analysis: https://cran.r-project.org/web/views/Environmetrics.html

Remember, when you close down RStudio, then start it up again, you don’t have to download the package again.
But you do have to load the package to use any function that’s not in the R core functionality (this is very easy to forget).


# Importing Data

- R can import data from just about any format, including
  - CSV
  - Excel
  - Databases
  - GIS shapefiles
  
## CSV

R has a built-in function called `read.csv()` for reading `.csv` files. Download
the `chicago_daily.csv` file [here](../data/chicago.csv) and save it to your
working directory. If you don't know what your working directory is, run this
code in R and it will tell you.


```r
getwd()
```

Use `read.csv()` by providing the location and name of the file as the first
argument. If the file is in your working directory, simply supply the name of the 
file. Below, the data from the file is read into R and saved as a `data.frame`,
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
such as `xlsx`, `XLConnect`, and `readxl`
  
In this example, we'll use the The `readxl` to get data into R. Use the `read_excel()` 
function to read emissions data from [this Excel workbook](../data/emissions_IL_2022.xlsx).
Download the file to your working directory and read the first worksheet,
skipping the first 6 rows. (Remember, if the library is not available, you
must install it first.)


```r
library(readxl)
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

# Quick Data exploration

Now that we have imported some data let’s learn more about it.

The data we imported in the previous section can actually be obtained in R by 
using the data() function and a package we created for this training.

Use the code below to obtain the data that we will use moving forward. This is 
very similar to what is in the Excel file.

```r
library(devtools)
install_github("natebyers/region5air")
library(region5air)
data(chicago_air)
```



`chicago_air` is a data frame with ozone (ppm), temperature (F), and solar 
radiation (W/m2) readings from a monitor in the Chicago area.


What column names are in the data frame?


```r
colnames(chicago_air)
```

```
## [1] "date"    "ozone"   "temp"    "solar"   "month"   "weekday"
```

How many observations does the dataset contain?


```r
nrow(chicago_air) # number of rows
```

```
## [1] 365
```

RStudio has a special function called `View()` that makes it easier to look at
data in a data frame

```r
View(chicago_air)
```

Use `head()` to look at the first few lines of a dataset.

```r
head(chicago_air)   ##Looks at the first 5 lines in the dataset
```

```
##         date ozone temp solar month weekday
## 1 2013-01-01 0.032   17  0.65     1       3
## 2 2013-01-02 0.020   15  0.61     1       4
## 3 2013-01-03 0.021   28  0.17     1       5
## 4 2013-01-04 0.028   18  0.62     1       6
## 5 2013-01-05 0.025   26  0.48     1       7
## 6 2013-01-06 0.026   36  0.47     1       1
```
Use `tail()` to look at the last lines.

```r
tail(chicago_air)  ##Looks at the last 5 lines in the dataset
```

```
##           date ozone temp solar month weekday
## 360 2013-12-26 0.026   NA  0.41    12       5
## 361 2013-12-27 0.021   NA  0.62    12       6
## 362 2013-12-28 0.026   NA  0.61    12       7
## 363 2013-12-29 0.029   NA  0.08    12       1
## 364 2013-12-30 0.024   NA  0.44    12       2
## 365 2013-12-31 0.021   NA  0.49    12       3
```
The `str()` function is important because it describes the basic structure of a
dataset. This lets you know if all the data was imported they way it was intended,
i.e. numbers came in as numeric, text came in as characters, etc. This is great
if you want a snapshot of the data structure.


```r
str(chicago_air)  ##Describes the basic structure of the dataset
```

```
## 'data.frame':	365 obs. of  6 variables:
##  $ date   : chr  "2013-01-01" "2013-01-02" "2013-01-03" "2013-01-04" ...
##  $ ozone  : num  0.032 0.02 0.021 0.028 0.025 0.026 0.024 0.021 0.031 0.024 ...
##  $ temp   : num  17 15 28 18 26 36 25 30 41 33 ...
##  $ solar  : num  0.65 0.61 0.17 0.62 0.48 0.47 0.65 0.39 0.65 0.42 ...
##  $ month  : num  1 1 1 1 1 1 1 1 1 1 ...
##  $ weekday: num  3 4 5 6 7 1 2 3 4 5 ...
```
The `summary()` function is a more robust version of `str()` if you are working 
with a lot of numeric values, because it will automatically do summary statistics
on any numbers in your data.frame.

```r
summary(chicago_air)
```

```
##      date               ozone              temp            solar      
##  Length:365         Min.   :0.00400   Min.   :-17.00   Min.   :0.040  
##  Class :character   1st Qu.:0.02500   1st Qu.: 36.75   1st Qu.:0.510  
##  Mode  :character   Median :0.03400   Median : 59.50   Median :0.910  
##                     Mean   :0.03567   Mean   : 54.84   Mean   :0.841  
##                     3rd Qu.:0.04500   3rd Qu.: 73.00   3rd Qu.:1.200  
##                     Max.   :0.08100   Max.   : 92.00   Max.   :1.490  
##                     NA's   :26        NA's   :109                     
##      month           weekday     
##  Min.   : 1.000   Min.   :1.000  
##  1st Qu.: 4.000   1st Qu.:2.000  
##  Median : 7.000   Median :4.000  
##  Mean   : 6.526   Mean   :3.997  
##  3rd Qu.:10.000   3rd Qu.:6.000  
##  Max.   :12.000   Max.   :7.000  
## 
```
# The `$` operator
You can refer to a specific column name in a `data.frame` with the $ operator. It
will return that column as a vector.


```r
str(chicago_air$ozone) # Calculates the mean temperature of the ozone column. Because there is ```
```

```
##  num [1:365] 0.032 0.02 0.021 0.028 0.025 0.026 0.024 0.021 0.031 0.024 ...
```
