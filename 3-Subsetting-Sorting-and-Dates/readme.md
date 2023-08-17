---
title: "Subsetting, Sorting, and Dates"
output: 
  html_document: 
    keep_md: yes
date: "2023-08-17"
---

This lesson covers how to subset data using indexing, logical operators, and
the `filter( )` function from `dplyr`. It also covers how to sort data,
combine data frames, and use the `Date` class.

- [Prerequisites](#prerequisites)
- [Viewing Data Frames](#viewing-data-frames)
- [Subsetting](#subsetting)
- [Sortting](#sorting)
- [Combinging Data Frames](#combining-data-frames)
- [Dates](#dates)

<br>
<hr>
<br>

# Prerequisites

This lesson assumes you are familiar with the material in the previous lesson on
[Functions and Importing Data](2-Functions-and_Importing-Data/readme.md).

The data from the R package `region5air` is used throughout these lessons.
To install the package from GitHub, use the `remotes` package.


```r
# if you have not installed remotes
install.packages("remotes")

library(remotes)
install_github("FluentData/region5air")
```

To load the `chicago_air` data frame we will be using in the lesson, use the 
`data( )` function. 


```r
library(region5air)

data(chicago_air)
```

You should see the `chicago_air` variable in the top right panel of RStudio, which
means the data frame has been loaded to your R session from the `region5air`
package.


# Viewing Data Frames


We always want to make sure our data looks the way it is supposed to before we 
begin working with it.

The best way to take a quick look at the first few rows of a data frame
is to use the `head()` function


```r
head(chicago_air)  
```

```
##         date ozone temp pressure month weekday
## 1 2021-01-01 0.019   42   1006.8     1       6
## 2 2021-01-02 0.020   35   1002.6     1       7
## 3 2021-01-03 0.026   34   1002.1     1       1
## 4 2021-01-04 0.022   44   1001.8     1       2
## 5 2021-01-05 0.028   37   1008.8     1       3
## 6 2021-01-06 0.027   38   1012.1     1       4
```

You can specify the number of lines to display by using the `n` parameter.


```r
head(chicago_air, n = 3)
```

```
##         date ozone temp pressure month weekday
## 1 2021-01-01 0.019   42   1006.8     1       6
## 2 2021-01-02 0.020   35   1002.6     1       7
## 3 2021-01-03 0.026   34   1002.1     1       1
```

You can also look at the bottom of the data frame by using the `tail( )` function.


```r
tail(chicago_air)
```

```
##           date ozone temp pressure month weekday
## 360 2021-12-26 0.022   53   1003.1    12       1
## 361 2021-12-27 0.019   66    997.3    12       2
## 362 2021-12-28 0.021   42    997.1    12       3
## 363 2021-12-29 0.017   42    997.5    12       4
## 364 2021-12-30 0.022   48    997.0    12       5
## 365 2021-12-31 0.023   62    994.7    12       6
```

In RStudio, you can either click on the name of the data frame in the top right
panel or use the `View( )` function to generate a web based table of the data
in the top left panel.


```r
View(chicago_air)
```

![](img/view.png)

By inspecting the data frame this way, you can see that the records are daily values
of ozone, temperature, and air pressure. For more information about the 
data set you can type a question mark in from the name of the data frame variable
in the console.


```r
?chicago_air
```

From the `Description` section of the help page:

> A dataset containing daily values of ozone, temperature, and barometric pressure
> from a Chicago monitor between January 1, 2021 and December 31, 2021.


# Subsetting

If we want to work with a particular subset of a data frame, we need to know how
to select particular records. We will cover how to subset using numeric indexing,
logical conditions, and the `filter( )` function.

## Indexing

Values in a data frame can be selected, individually or in a group, based on their
index values. These are integers that represent the locations in the data frame.
If there is a 2 x 2 table, then there are 2 rows and 2 columns. Each cell can be 
represented by two numbers, like  coordinates on a map. For a data frame, the format
is `[row, column]`. Below is a table that shows the index values in each cell.

|Column 1 | Column 2|
|---      |---      |
| `[1, 1]`| `[1, 2]`|
| `[2, 1]`| `[2, 2]`|

Below is an example of how you access a particular value in a `data.frame` based on its index.


```r
my_data <- data.frame(x = 1:5, y = 6:10)
my_data[4, 2] ## This should grab the value in the 4th row and 2nd column 
```

```
## [1] 9
```


We can also access data from a vector using the same indexing idea. In this case,
you don’t need the comma to separate the rows and columns since you are accessing 
one dimensional data.


```r
x <- c(1, 3, 2, 7, 25.3, 6)
x[5]  # This will access the fifth element in the vector
```

```
## [1] 25.3
```


Now that we understand indexing we can subset the `chicago_air` data frame by using the 
`[` function.

# Subsetting Using Indexing
To get one row of the data frame, specify the row number you would like in the 
brackets, on the left side of the comma. By leaving the column value on the right
side of the comma blank, it returns all the columns associated with row number 1.


```r
chicago_air[1, ]
```

```
##         date ozone temp pressure month weekday
## 1 2021-01-01 0.019   42   1006.8     1       6
```


If you want more than one row, you can supply a vector of row numbers


```r
chicago_air[c(1, 2, 5), ] #Accesses the 1, 2 and 5th rows of data
```

```
##         date ozone temp pressure month weekday
## 1 2021-01-01 0.019   42   1006.8     1       6
## 2 2021-01-02 0.020   35   1002.6     1       7
## 5 2021-01-05 0.028   37   1008.8     1       3
```

To get a column from the data frame, specify the column number in the brackets, 
to the right of the comma. By leaving the row value blank, you are telling it to
return all rows associated with column 1.


```r
head( chicago_air[, 1] )
```

```
## [1] "2021-01-01" "2021-01-02" "2021-01-03" "2021-01-04" "2021-01-05"
## [6] "2021-01-06"
```

You can obtain more than one column by supplying a vector of column numbers


```r
head( chicago_air[, c(3, 4, 6)] )
```

```
##   temp pressure weekday
## 1   42   1006.8       6
## 2   35   1002.6       7
## 3   34   1002.1       1
## 4   44   1001.8       2
## 5   37   1008.8       3
## 6   38   1012.1       4
```

Column names can also be used.


```r
head( chicago_air[, "pressure"] )
```

```
## [1] 1006.8 1002.6 1002.1 1001.8 1008.8 1012.1
```

Or a vector of column names


```r
head( chicago_air[, c("ozone", "temp", "month")] )
```

```
##   ozone temp month
## 1 0.019   42     1
## 2 0.020   35     1
## 3 0.026   34     1
## 4 0.022   44     1
## 5 0.028   37     1
## 6 0.027   38     1
```

Both rows and columns can be specified at the same time. 


```r
chicago_air[1:5, 3:5]  # Returns first 5 rows of data and the third through fifth columns.
```

```
##   temp pressure month
## 1   42   1006.8     1
## 2   35   1002.6     1
## 3   34   1002.1     1
## 4   44   1001.8     1
## 5   37   1008.8     1
```

# Logical Operators
You can also subset a data frame by using logical expressions
The logical expression is used to specify rows that you want to keep or discard


## Reference Table of Logical Operators
|Operator |Description |
| :---    | :---       |
| <	      | less than  |
| <=	    | less than or equal to|
| >	      | greater than |
| >=	    | greater than or equal to |
| ==	    | exactly equal to |
| !=	    | not equal to |
| !x      | not x |
| x & y   | x AND y |
| x <code>&#124;</code> y |	x OR y|

Here is an example using a logical expression to subset.


```r
logical_vector <- chicago_air$solar > 1.45 # records with greater than 1.45 in the solar column

chicago_air[logical_vector, ] 
```

```
## [1] date     ozone    temp     pressure month    weekday 
## <0 rows> (or 0-length row.names)
```


Another helpful tool when subsetting is the complete.cases function.
This function allows us to only look at data where observations for all columns are complete.
The function returns a logical vector that can be used to subset a `data.frame`.


```r
complete <- complete.cases(chicago_air)

air <- chicago_air[complete,] 
```


_We will use the `air` `data.frame` for the rest of the subsetting
examples._


Let's say we only want rows in this `data.frame` where ozone was above 70 ppb (.070 ppm).


```r
ozone_violation <- air[(air$ozone > .070), ]  # This returns all the days with readings above .070 ppm

ozone_violation
```

```
## [1] date     ozone    temp     pressure month    weekday 
## <0 rows> (or 0-length row.names)
```


If we wanted all of the days in the 7th month, we could use the `==` operator.


```r
air[(air$month == 7), ]
```

```
##           date ozone temp pressure month weekday
## 182 2021-07-01 0.040   81   1000.4     7       5
## 183 2021-07-02 0.034   76   1002.0     7       6
## 184 2021-07-03 0.041   77   1002.9     7       7
## 185 2021-07-04 0.039   83   1000.7     7       1
## 186 2021-07-05 0.042   85   1002.6     7       2
## 187 2021-07-06 0.043   86   1003.7     7       3
## 188 2021-07-07 0.046   85   1000.4     7       4
## 189 2021-07-08 0.041   84    999.3     7       5
## 190 2021-07-09 0.032   76   1002.6     7       6
## 191 2021-07-10 0.043   76   1000.4     7       7
## 192 2021-07-11 0.040   77    997.7     7       1
## 193 2021-07-12 0.038   80    999.9     7       2
## 194 2021-07-13 0.035   78   1005.1     7       3
## 195 2021-07-14 0.037   83   1006.7     7       4
## 196 2021-07-15 0.031   85   1002.8     7       5
## 197 2021-07-16 0.025   75   1000.4     7       6
## 198 2021-07-17 0.041   79   1004.3     7       7
## 199 2021-07-18 0.038   82   1005.5     7       1
## 200 2021-07-19 0.037   82   1005.3     7       2
## 201 2021-07-20 0.053   83   1003.3     7       3
## 202 2021-07-21 0.049   83   1004.8     7       4
## 203 2021-07-22 0.041   81   1007.0     7       5
## 204 2021-07-23 0.047   84   1005.9     7       6
## 205 2021-07-24 0.041   86   1001.5     7       7
## 206 2021-07-25 0.034   84    999.3     7       1
## 207 2021-07-26 0.050   87   1001.1     7       2
## 208 2021-07-27 0.048   86   1002.6     7       3
## 209 2021-07-28 0.043   85   1003.0     7       4
## 210 2021-07-29 0.028   86   1000.5     7       5
## 211 2021-07-30 0.034   79   1003.7     7       6
## 212 2021-07-31 0.030   67   1002.8     7       7
```

Or if we want all days except the 6th day, we would use `!=`.


```r
head( air[(air$weekday != 6), ] ) #Excludes all data from the 6th day of the week
```

```
##         date ozone temp pressure month weekday
## 2 2021-01-02 0.020   35   1002.6     1       7
## 3 2021-01-03 0.026   34   1002.1     1       1
## 4 2021-01-04 0.022   44   1001.8     1       2
## 5 2021-01-05 0.028   37   1008.8     1       3
## 6 2021-01-06 0.027   38   1012.1     1       4
## 7 2021-01-07 0.029   39   1009.8     1       5
```

We can combine logical conditions with `&` (the _AND_ operator)

If we wanted only rows where the temperature was between 80 and 85 (including those numbers)


```r
air[(air$temp >= 80 & air$temp <= 85), ]
```

```
##           date ozone temp pressure month weekday
## 97  2021-04-07 0.039   81    997.0     4       4
## 117 2021-04-27 0.057   82    996.9     4       3
## 140 2021-05-20 0.049   82   1009.2     5       5
## 141 2021-05-21 0.056   82   1013.2     5       6
## 142 2021-05-22 0.056   83   1013.7     5       7
## 143 2021-05-23 0.054   85   1009.2     5       1
## 145 2021-05-25 0.050   85   1003.9     5       3
## 146 2021-05-26 0.042   80   1002.7     5       4
## 147 2021-05-27 0.047   82   1002.8     5       5
## 155 2021-06-04 0.064   83   1001.4     6       6
## 158 2021-06-07 0.032   81    999.9     6       2
## 160 2021-06-09 0.035   81   1000.7     6       4
## 161 2021-06-10 0.038   84    998.3     6       5
## 166 2021-06-15 0.047   82   1002.6     6       3
## 167 2021-06-16 0.047   82   1003.3     6       4
## 170 2021-06-19 0.046   82    999.7     6       7
## 172 2021-06-21 0.036   80    997.8     6       2
## 175 2021-06-24 0.046   80   1003.0     6       5
## 176 2021-06-25 0.032   81   1000.0     6       6
## 177 2021-06-26 0.035   85    998.2     6       7
## 181 2021-06-30 0.035   82   1004.4     6       4
## 182 2021-07-01 0.040   81   1000.4     7       5
## 185 2021-07-04 0.039   83   1000.7     7       1
## 186 2021-07-05 0.042   85   1002.6     7       2
## 188 2021-07-07 0.046   85   1000.4     7       4
## 189 2021-07-08 0.041   84    999.3     7       5
## 193 2021-07-12 0.038   80    999.9     7       2
## 195 2021-07-14 0.037   83   1006.7     7       4
## 196 2021-07-15 0.031   85   1002.8     7       5
## 199 2021-07-18 0.038   82   1005.5     7       1
## 200 2021-07-19 0.037   82   1005.3     7       2
## 201 2021-07-20 0.053   83   1003.3     7       3
## 202 2021-07-21 0.049   83   1004.8     7       4
## 203 2021-07-22 0.041   81   1007.0     7       5
## 204 2021-07-23 0.047   84   1005.9     7       6
## 206 2021-07-25 0.034   84    999.3     7       1
## 209 2021-07-28 0.043   85   1003.0     7       4
## 216 2021-08-04 0.046   80   1004.6     8       4
## 217 2021-08-05 0.050   80   1005.0     8       5
## 218 2021-08-06 0.043   81   1003.7     8       6
## 219 2021-08-07 0.040   84   1001.9     8       7
## 220 2021-08-08 0.037   85   1000.0     8       1
## 221 2021-08-09 0.034   81   1000.3     8       2
## 225 2021-08-13 0.037   83   1004.5     8       6
## 226 2021-08-14 0.041   81   1007.8     8       7
## 228 2021-08-16 0.038   81   1002.1     8       2
## 229 2021-08-17 0.036   83   1000.9     8       3
## 230 2021-08-18 0.035   84   1003.2     8       4
## 231 2021-08-19 0.041   85   1003.3     8       5
## 233 2021-08-21 0.031   84    997.1     8       7
## 242 2021-08-30 0.027   82   1000.4     8       2
## 243 2021-08-31 0.038   83    995.9     8       3
## 244 2021-09-01 0.041   80   1000.0     9       4
## 249 2021-09-06 0.045   85   1000.5     9       2
## 251 2021-09-08 0.040   80    997.2     9       4
## 253 2021-09-10 0.037   80   1004.6     9       6
## 259 2021-09-16 0.045   84   1003.3     9       5
## 263 2021-09-20 0.026   85    999.9     9       2
## 269 2021-09-26 0.042   80   1003.6     9       1
## 274 2021-10-01 0.049   84   1006.8    10       6
## 282 2021-10-09 0.049   83   1000.0    10       7
## 284 2021-10-11 0.040   81    994.1    10       2
```

We can also use `|` (the _OR_ operator) to select rows on days 3 or 5

```r
head( air[(air$weekday == 3 | air$weekday == 5),] )
```

```
##          date ozone temp pressure month weekday
## 5  2021-01-05 0.028   37   1008.8     1       3
## 7  2021-01-07 0.029   39   1009.8     1       5
## 12 2021-01-12 0.022   41   1009.7     1       3
## 14 2021-01-14 0.026   46    991.7     1       5
## 19 2021-01-19 0.033   40   1009.7     1       3
## 21 2021-01-21 0.032   49    998.1     1       5
```

# Subsetting using the subset() function

You can also use the `subset()` function to filter a `data.frame` down to the records
you want. The first argument in the function is the name of the `data.frame` and
the second argument is the logical expression. No need to use `$` for column names.


```r
high_temp <- subset(air, temp > 90)  

head(high_temp)
```

```
##           date ozone temp pressure month weekday
## 163 2021-06-12 0.053   91    995.4     6       7
## 169 2021-06-18 0.062   93    997.5     6       6
## 239 2021-08-27 0.044   91   1003.3     8       6
```

By using the select = parameter you can specify which columns to keep

```r
high_temp_ozone <- subset(air, temp > 90, select = c(ozone, temp))

head(high_temp_ozone)
```

```
##     ozone temp
## 163 0.053   91
## 169 0.062   93
## 239 0.044   91
```



# Sorting data 

You can sort the rows of a `data.frame` using the `order()` function. For 
example, we can sort the `chicago_air` dataset by ozone. The output of the `order()`
function is a vector of integers that map to the ascending order of the input. 



```r
ozone_ordered <- order(air$ozone)

head(ozone_ordered)
```

```
## [1] 293 299 361 350   1  25
```

We can use the output to arrange the rows of the `data.frame` by placing the 
ordered vector on the left side of the `[, ]` operator.


```r
air_ozone_ascending <- air[ozone_ordered, ] 

head(air_ozone_ascending)
```

```
##           date ozone temp pressure month weekday
## 295 2021-10-22 0.012   52   1002.6    10       6
## 301 2021-10-28 0.015   53    989.2    10       5
## 363 2021-12-29 0.017   42    997.5    12       4
## 352 2021-12-18 0.018   42   1009.1    12       7
## 1   2021-01-01 0.019   42   1006.8     1       6
## 25  2021-01-25 0.019   35   1002.3     1       2
```


You can easily sort the `data.frame` in descending order by reversing the
ordered vector, using the `rev()` function.


```r
air_ozone_descending <- air[rev(ozone_ordered), ] 

head(air_ozone_descending)
```

```
##           date ozone temp pressure month weekday
## 165 2021-06-14 0.065   87   1000.4     6       2
## 155 2021-06-04 0.064   83   1001.4     6       6
## 169 2021-06-18 0.062   93    997.5     6       6
## 168 2021-06-17 0.062   86   1001.7     6       5
## 164 2021-06-13 0.062   86    998.8     6       1
## 144 2021-05-24 0.061   86   1006.4     5       2
```

# Combining `data.frame`s

`data.frame`s can be combined using the `rbind()`  and `cbind()` functions, standing
for "row bind" and "column bind" respectively. 

The `rbind()` function requires that there to be an an equal number of columns
among the `data.frame`s. To illustrate, we will make two subsets of the `air`
`data.frame` and then combine them using `rbind()`.


```r
nrow(air) # show the original number of records
```

```
## [1] 363
```

```r
air_warm <- subset(air, temp > 80) # get warm air records

nrow(air_warm) # show the number of records
```

```
## [1] 93
```

```r
air_cool <- subset(air, temp <= 80) # get cool air records

nrow(air_cool) # show number of records
```

```
## [1] 270
```

```r
air_recombined <- rbind(air_warm, air_cool) # combine the data.frames

nrow(air_recombined) # number of records
```

```
## [1] 363
```



