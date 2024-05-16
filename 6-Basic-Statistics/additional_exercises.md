# Additional Exercises for Lesson 6 - Basic Statistics

These are optional exercises that you can attempt for further practice over the material covered in Basic Statistics.

### Exercise 1 - Beginner

Find the mean of the ozone column in `chicago_air`.

<details><summary>Click for Solution</summary>

> Calculate the mean using the `mean()` function.

#### Solution

```r
# Load the dataset
library(region5air)
data(chicago_air)

# Calculate the mean of the ozone column
mean_ozone <- mean(chicago_air$ozone, na.rm = TRUE)
mean_ozone
```
</details>
---

### Exercise 2 - Beginner

Find the standard deviation of the temperature column in `chicago_air`.

<details><summary>Click for Solution</summary>

> Calculate the standard deviation using the `sd()` function.

#### Solution

```r
# Load the dataset
library(region5air)
data(chicago_air)

# Calculate the standard deviation of the temperature column
sd_temp <- sd(chicago_air$temp, na.rm = TRUE)
sd_temp
```
</details>
---

### Exercise 3 - Beginner

Find the variance of the pressure column in `chicago_air`.

<details><summary>Click for Solution</summary>

> Calculate the variance using the `var()` function.

#### Solution

```r
# Load the dataset
library(region5air)
data(chicago_air)

# Calculate the variance of the pressure column
var_pressure <- var(chicago_air$pressure, na.rm = TRUE)
var_pressure
```
</details>
---

### Exercise 4 - Intermediate

Calculate the interquartile range (IQR) of the ozone column in `chicago_air`.

<details><summary>Click for Solution</summary>

> Calculate the IQR using the `IQR()` function.

#### Solution

```r
# Load the dataset
library(region5air)
data(chicago_air)

# Calculate the IQR of the ozone column
iqr_ozone <- IQR(chicago_air$ozone, na.rm = TRUE)
iqr_ozone
```
</details>
---

### Exercise 5 - Intermediate

Perform a Shapiro-Wilk test to check if the temperature column in `chicago_air` is normally distributed.

<details><summary>Click for Solution</summary>

> Use the `shapiro.test()` function to perform the test.

#### Solution

```r
# Load the dataset
library(region5air)
data(chicago_air)

# Perform the Shapiro-Wilk test for the temperature column
shapiro_test_temp <- shapiro.test(chicago_air$temp)
shapiro_test_temp
```
</details>
---

### Exercise 6 - Intermediate

Calculate the correlation between the ozone and temperature columns in `chicago_air`.

<details><summary>Click for Solution</summary>

> Use the `cor()` function to calculate the correlation.

#### Solution

```r
# Load the dataset
library(region5air)
data(chicago_air)

# Calculate the correlation between ozone and temperature
cor_ozone_temp <- cor(chicago_air$ozone, chicago_air$temp, use = "complete.obs")
cor_ozone_temp
```
</details>
---

### Exercise 7 - Advanced

Create a correlation matrix of all numeric columns in `chicago_air`.

<details><summary>Click for Solution</summary>

> Use the `cor()` function to create a correlation matrix.

#### Solution

```r
# Load the dataset
library(region5air)
data(chicago_air)

# Create a correlation matrix for all numeric columns
cor_matrix <- cor(chicago_air[, sapply(chicago_air, is.numeric)], use = "complete.obs")
cor_matrix
```
</details>
---

### Exercise 8 - Advanced

Create pairwise plots for numeric columns in `chicago_air`, with a smooth line in lower-panel plots.

<details><summary>Click for Solution</summary>

> Use the `pairs()` function and add a smooth line to the lower panels.

#### Solution

```r
# Load the dataset
library(region5air)
data(chicago_air)

# Create pairwise plots with a smooth line
pairs(chicago_air[, sapply(chicago_air, is.numeric)],
      lower.panel = panel.smooth)
```
</details>
---

### Exercise 9 - Advanced

Compare the mean temperature in `chicago_air` between weekdays and weekends using a Student's t-test.

<details><summary>Click for Solution</summary>

> Use the `t.test()` function to compare means between two groups.

#### Solution

```r
# Load the dataset
library(region5air)
data(chicago_air)

# Create a factor indicating weekday or weekend
chicago_air$weekend <- ifelse(chicago_air$weekday %in% c(6, 7), "Weekend", "Weekday")

# Perform the t-test
t_test_temp <- t.test(temp ~ weekend, data = chicago_air)
t_test_temp
```
</details>
---

### Exercise 10 - Advanced

Find the mean and median of the ozone column in `chicago_air` and compare them. Discuss what the comparison indicates about the distribution of the ozone data.

<details><summary>Click for Solution</summary>

> Calculate the mean and median, and compare them to understand the skewness of the data.

#### Solution

```r
# Load the dataset
library(region5air)
data(chicago_air)

# Calculate the mean and median of the ozone column
mean_ozone <- mean(chicago_air$ozone, na.rm = TRUE)
median_ozone <- median(chicago_air$ozone, na.rm = TRUE)

# Print the results
mean_ozone
median_ozone

# Discussion
# If the mean is greater than the median, the distribution is positively skewed (right-skewed).
# If the mean is less than the median, the distribution is negatively skewed (left-skewed).
# If the mean and median are close, the distribution is approximately symmetric.
```
</details>
---
