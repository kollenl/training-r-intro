# Additional Exercises for Lesson 3 - Subsetting, Sorting, and Combining Data

These are optional exercises that you can attempt for further practice over the material covered in Lesson 3.  

### Exercise 1 - Beginner

Load the `chicago_air` dataset and display the structure of the dataset.

<details><summary>Click for Solution</summary>
	
> This exercise helps familiarize you with the dataset structure.

#### Solution

```r
library(region5air)
data(chicago_air)
str(chicago_air)
```
</details>
---

### Exercise 2 - Beginner

Load `chicago_air` and display the first 10 rows using numeric indexing.

<details><summary>Click for Solution</summary>
	
> Use numeric indexing to view the first few rows of the dataset.

#### Solution

```r
library(region5air)
data(chicago_air)
chicago_air[1:10, ]
```
</details>
---

### Exercise 3 - Beginner

Use `filter()` from `dplyr` to subset `chicago_air` to values where ozone is above 0.060 ppm.

<details><summary>Click for Solution</summary>
	
> This exercise demonstrates how to filter data based on a condition.

#### Solution

```r
library(region5air)
library(dplyr)
data(chicago_air)
filtered_data <- filter(chicago_air, ozone > 0.060)
filtered_data
```
</details>
---

### Exercise 4 - Intermediate

Use `filter()` to subset `chicago_air` to values where ozone is above 0.060 ppm and temperature is above 90 degrees.

<details><summary>Click for Solution</summary>
	
> This exercise combines multiple conditions to filter the data.

#### Solution

```r
library(region5air)
library(dplyr)
data(chicago_air)
filtered_data <- filter(chicago_air, ozone > 0.060, temp > 90)
filtered_data
```
</details>
---

### Exercise 5 - Intermediate

Use `arrange()` from `dplyr` to sort `chicago_air` by temperature in descending order.

<details><summary>Click for Solution</summary>
	
> This exercise demonstrates sorting a dataset by a specific column.

#### Solution

```r
library(region5air)
library(dplyr)
data(chicago_air)
sorted_data <- arrange(chicago_air, desc(temp))
sorted_data
```
</details>
---

### Exercise 6 - Intermediate

Use `select()` from `dplyr` to create a new data frame from `chicago_air` that contains only the `date`, `ozone`, and `temp` columns.

<details><summary>Click for Solution</summary>
	
> This exercise shows how to select specific columns from a dataset.

#### Solution

```r
library(region5air)
library(dplyr)
data(chicago_air)
selected_data <- select(chicago_air, date, ozone, temp)
selected_data
```
</details>
---

### Exercise 7 - Advanced

Create a new column `ozone_level` in `chicago_air` that categorizes ozone values into "Low" (< 0.050), "Medium" (0.050 - 0.100), and "High" (> 0.100).

<details><summary>Click for Solution</summary>
	
> This exercise involves creating new categorical data based on existing numeric data.

#### Solution

```r
library(region5air)
data(chicago_air)
chicago_air$ozone_level <- cut(chicago_air$ozone, 
                               breaks = c(-Inf, 0.050, 0.100, Inf), 
                               labels = c("Low", "Medium", "High"))
chicago_air
```
</details>
---

### Exercise 8 - Advanced

Use `mutate()` from `dplyr` to add a new column `temp_celsius` to `chicago_air` that converts temperatures from Fahrenheit to Celsius.

<details><summary>Click for Solution</summary>
	
> This exercise demonstrates how to create new columns based on existing ones using `mutate()`.

#### Solution

```r
library(region5air)
library(dplyr)
data(chicago_air)
chicago_air <- mutate(chicago_air, temp_celsius = (temp - 32) * 5/9)
chicago_air
```
</details>
---

### Exercise 9 - Advanced

Use `group_by()` and `summarize()` from `dplyr` to calculate the average ozone and temperature for each month in `chicago_air`.

<details><summary>Click for Solution</summary>
	
> This exercise covers grouping data and summarizing it by specific groups.

#### Solution

```r
library(region5air)
library(dplyr)
data(chicago_air)
monthly_summary <- chicago_air %>%
  group_by(month) %>%
  summarize(avg_ozone = mean(ozone, na.rm = TRUE), 
            avg_temp = mean(temp, na.rm = TRUE))
monthly_summary
```
</details>
---

### Exercise 10 - Advanced

Combine two data frames using `bind_rows()`: `chicago_air` and a new data frame containing made-up data for the first three days of January 2023.

<details><summary>Click for Solution</summary>
	
> This exercise demonstrates how to combine datasets using `bind_rows()`.

#### Solution

```r
library(region5air)
library(dplyr)
data(chicago_air)

# Creating a new data frame with made-up data
new_data <- data.frame(
  date = as.Date(c("2023-01-01", "2023-01-02", "2023-01-03")),
  ozone = c(0.030, 0.045, 0.055),
  temp = c(32, 30, 28),
  pressure = c(1020, 1018, 1019),
  month = c(1, 1, 1),
  weekday = c(7, 1, 2)
)

# Combining the data frames
combined_data <- bind_rows(chicago_air, new_data)
combined_data
```
</details>
---
