## Exercises


### Exercise 1

Exercise 1: Use the `seq()`, `round()`, `paste()`, `substr()` functions with different parameters and observe their results. Also, try combining the functions.

<details><summary>Click for Hint</summary>

The `seq()` function generates regular sequences, `round()` rounds the values to the nearest whole number, `paste()` concatenates vectors after converting to character and `substr()` extracts or replaces substrings in a character vector.
</details>
<details><summary>Click for Solution</summary>

#### Solution

```r
```r
# Using seq function
data_seq = seq(1, 20, by = 2)
print(data_seq)

# Using round function
data_round = round(3.5678, digits=2)
print(data_round)

# Using paste function
data_paste = paste('Hello', 'R')
print(data_paste)

# Using substr function
data_substr = substr('Hello R', start = 1, stop = 5)
print(data_substr)
```
```

#### Output

```r
```r
# seq function output
 [1]  1  3  5  7  9 11 13 15 17 19
# round function output
[1] 3.57
# paste function output
[1] 'Hello R'
# substr function output
[1] 'Hello'
```
```



</details>

---


### Exercise 2

Exercise 2: Write a custom function in R that takes two arguments, multiplies them, and adds a random number to the product. Test the function with some values.

<details><summary>Click for Hint</summary>

You need to define a function using `<- function(){}` in R. Inside the function, calculate the product of two numbers and add a random number to the product using `runif(1)`.
</details>
<details><summary>Click for Solution</summary>

#### Solution

```r
```r
# Custom function
custom_function <- function(x,y) {
  product <- x*y
  final_result <- product + runif(1)
  return(final_result)
}

# Test the function
print(custom_function(4,5))
```
```

#### Output

```r
```r
# This will vary due to the random addition
[1] 20.63213
```
```



</details>

---


### Exercise 3

Exercise 3: Use the `read.csv()` function to read a CSV file. Then use `head()`, `nrow()`, `colnames()`, `View()`, `str()`, and `summary()` functions to explore the data.

<details><summary>Click for Hint</summary>

Use `read.csv()` to read the data into R. The `head()` function shows the top rows of the data, `nrow()` returns the number of rows in the data, `colnames()` returns the names of the columns, `View()` opens the data in a spreadsheet-style view, `str()` shows the structure of the data, and `summary()` provides summary statistics of the data.
</details>
<details><summary>Click for Solution</summary>

#### Solution

```r
Assuming there's a CSV file named 'sample_data.csv' in the working directory, the solution would be:
```r
data <- read.csv('sample_data.csv')

# Display the first few lines
print(head(data))

# Number of rows
print(nrow(data))

# Column names
print(colnames(data))

# Quick look at the data
View(data)

# Structure of the data
print(str(data))

# Summary of the data
print(summary(data))
```
```

#### Output

```r
The output will vary depending on the CSV file
```



</details>

---
