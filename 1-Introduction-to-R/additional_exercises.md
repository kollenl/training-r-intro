# Additional Exercises for Lesson 1: Introduction to R

These are optional exercises that you can attempt for further practice over the material covered in Lesson 1.

### Exercise 1 - Beginner

Add 25 and 75 in R.

<details><summary>Click for Solution</summary>
	
> This exercise introduces basic arithmetic operations in R.

#### Solution

```r
25 + 75
```
</details>
---

### Exercise 2 - Beginner

Create an R variable `x` that stores the value 10.

<details><summary>Click for Solution</summary>
	
> This exercise helps you understand variable assignment in R.

#### Solution

```r
x <- 10
```
</details>
---

### Exercise 3 - Beginner

Create a vector `v` that contains the numbers 1 through 5.

<details><summary>Click for Solution</summary>
	
> This exercise introduces the concept of vectors, which are a basic data structure in R.

#### Solution

```r
v <- c(1, 2, 3, 4, 5)
```
</details>
---

### Exercise 4 - Beginner

Create a list `l` that contains a number, a string, and a logical value.

<details><summary>Click for Solution</summary>
	
> This exercise demonstrates how to create lists, which can hold different types of data in R.

#### Solution

```r
l <- list(42, "Hello, R!", TRUE)
```
</details>
---

### Exercise 5 - Beginner

Create a data frame `df` with two columns, `name` and `age`, each containing three entries of your choosing.

<details><summary>Click for Solution</summary>
	
> This exercise introduces data frames, which are essential for handling tabular data in R.

#### Solution

```r
df <- data.frame(name = c("Alice", "Bob", "Charlie"), age = c(25, 30, 35))
```
</details>
---

### Exercise 6 - Intermediate

Create a vector `temps` that contains the temperature values 72, 75, 80, 78, 85 and calculate the mean temperature.

<details><summary>Click for Solution</summary>
	
> This exercise helps you practice creating vectors and using functions to perform calculations on them.

#### Solution

```r
temps <- c(72, 75, 80, 78, 85)
mean(temps)
```
</details>
---

### Exercise 7 - Intermediate

Create a vector `days` that contains the names of the days of the week and use the `length()` function to find the number of days.

<details><summary>Click for Solution</summary>
	
> This exercise demonstrates the use of character vectors and applying functions to determine their properties.

#### Solution

```r
days <- c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday")
length(days)
```
</details>
---

### Exercise 8 - Intermediate

Create a matrix `m` with 2 rows and 3 columns containing the numbers 1 to 6.

<details><summary>Click for Solution</summary>
	
> This exercise introduces the concept of matrices, which are a type of two-dimensional data structure in R.

#### Solution

```r
m <- matrix(1:6, nrow = 2, ncol = 3)
```
</details>
---

### Exercise 9 - Advanced

Create a vector `ozone_levels` with the following values: 0.03, 0.04, 0.05, 0.06, 0.07. Use logical indexing to create a new vector `high_ozone` that contains only the values greater than 0.05.

<details><summary>Click for Solution</summary>
	
> This exercise introduces logical indexing, which is a powerful way to subset data in R.

#### Solution

```r
ozone_levels <- c(0.03, 0.04, 0.05, 0.06, 0.07)
high_ozone <- ozone_levels[ozone_levels > 0.05]
high_ozone
```
</details>
---

### Exercise 10 - Advanced

Create a data frame `weather` with columns `day`, `temp`, and `pressure`, and fill it with appropriate values. Then, use the `summary()` function to get a summary of the data frame.

<details><summary>Click for Solution</summary>
	
> This exercise combines the creation of a data frame with the use of a function to summarize its contents, providing insight into basic data exploration techniques in R.

#### Solution

```r
weather <- data.frame(
  day = c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday"),
  temp = c(72, 75, 80, 78, 85),
  pressure = c(1015, 1013, 1012, 1014, 1011)
)
summary(weather)
```
</details>
---
