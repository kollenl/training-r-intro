## Quiz


### 1. What is the main use of the plot() function in R?

1. To import datasets in R
1. To visualize data in R through graphs
1. To calculate statistics of datasets
1. To transform data into different formats
<details><summary>Click for Answer</summary>

#### Answer

2.  To visualize data in R through graphs

> The plot() function in R is used to visualize data through graphs such as scatter plots, line graphs, etc.</details>

---


### 2. How do we create a scatter plot of temperature on the x-axis and ozone on the y-axis `using the chicago_air dataset?

1. plot(chicago_air$ozone, chicago_air$temp)
1. plot(chicago_air$temp, chicago_air$ozone)
1. scatter(chicago_air$temp, chicago_air$ozone)
1. scatter(chicago_air$ozone, chicago_air$temp)
<details><summary>Click for Answer</summary>

#### Answer

2.  plot(chicago_air$temp, chicago_air$ozone)

> The plot function in R can be used to create scatter plots by specifying the x-axis and y-axis variables.</details>

---


### 3. What does the `as.Date()` function in R do?

1. It converts a column to a Date data type
1. It converts Date data type to numeric data type
1. It calculates the current date
1. It calculates the difference between two dates
<details><summary>Click for Answer</summary>

#### Answer

1.  It converts a column to a Date data type

> The `as.Date()` function in R is used to convert a column to a Date data type.</details>

---


### 4. How do we place multiple graphs on the same plotting screen using par() function?

1. By defining the grid for plotting. The `mfrow` parameter takes a vector of two values - the first value is the number of rows and the second is the number of columns
1. By using mfrow = c(2,1)
1. By applying par function on each graph separately
1. By applying par function on the data, not on the graphs
<details><summary>Click for Answer</summary>

#### Answer

1.  By defining the grid for plotting. The `mfrow` parameter takes a vector of two values - the first value is the number of rows and the second is the number of columns

> The par() function is used to define the grid for plotting. The `mfrow` parameter takes a vector of two values. The first value is the number of rows and the second is the number of columns.</details>

---


### 5. What are factors in R?

1. Variables in R that are treated as categorical variables or 'levels' of data
1. A mathematical concept used for division
1. Variables in R that are treated as continuous data
1. Different data frames in R
<details><summary>Click for Answer</summary>

#### Answer

1.  Variables in R that are treated as categorical variables or 'levels' of data

> Factors are variables in R that are treated as categorical variables or 'levels' of data. This can be helpful for graphing and statistical summaries.</details>

---


### 6. What does the `scales = list(x=list(rot=45))` argument do in the bwplot function?

1. It rotates the x-axis labels 45 degrees
1. It scales the x-axis by a factor of 45
1. It adjusts the y-axis scaling
1. It rotates the plot 45 degrees
<details><summary>Click for Answer</summary>

#### Answer

1.  It rotates the x-axis labels 45 degrees

> The argument 'scales = list(x=list(rot=45))' is used to rotate the x-axis labels by 45 degrees.</details>

---


### 7. What is the purpose of ggplot2 in R?

1. To display relationships between variables by conditioning
1. To install and set up R and RStudio
1. To calculate statistics of datasets
1. To import data from various formats, such as CSV and Excel
<details><summary>Click for Answer</summary>

#### Answer

1.  To display relationships between variables by conditioning

> The ggplot2 package in R is used for displaying relationships between variables by conditioning.</details>

---


### 8. How can we save a plot made by ggplot2?

1. By pressing ctrl+S
1. Using the ggsave() function
1. By clicking 'File' then 'Save' in R
1. Using the save() function
<details><summary>Click for Answer</summary>

#### Answer

2.  Using the ggsave() function

> A plot made by ggplot2 can be saved using the ggsave() function.</details>

---


### 9. What does the `geom_smooth(method=lm)` function do?

1. It creates a fitted line to the points on the graph along with a 95% confidence shaded area
1. It smoothens the graph without adding a fitted line or confidence shaded area
1. It adds colors to the graph
1. It removes outliers from the graph
<details><summary>Click for Answer</summary>

#### Answer

1.  It creates a fitted line to the points on the graph along with a 95% confidence shaded area

> The `geom_smooth(method=lm)` function creates a fitted line to the points on the graph along with a 95% confidence shaded area.</details>

---


### 10. Which function do we use to make a line plot in lattice package?

1. barplot()
1. hist()
1. scatterplot()
1. xyplot()
<details><summary>Click for Answer</summary>

#### Answer

4.  xyplot()

> To make a line plot in lattice package, the xyplot() function is used.</details>

---

