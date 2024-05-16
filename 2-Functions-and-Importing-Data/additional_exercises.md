# Additional Exercises for Lesson 2 - Functions and Importing Data in R

These are optional exercises that you can attempt for further practice over the material covered in Lesson 2.

### Exercise 1 - Beginner

Create a sequence of numbers from 5 to 15 using the `seq()` function.

<details><summary>Click for Solution</summary>
	
> Use the `seq()` function to create the sequence.

#### Solution

```r
# Create a sequence from 5 to 15
seq(5, 15)
```
</details>
---

### Exercise 2 - Beginner

Round the number 45.67891 to three decimal places using the `round()` function.

<details><summary>Click for Solution</summary>
	
> Use the `round()` function with two arguments.

#### Solution

```r
# Round 45.67891 to three decimal places
round(45.67891, 3)
```
</details>
---

### Exercise 3 - Beginner

Concatenate the strings "Data" and "Science" using the `paste()` function.

<details><summary>Click for Solution</summary>
	
> Use the `paste()` function to combine the strings with a space.

#### Solution

```r
# Concatenate "Data" and "Science"
paste("Data", "Science")
```
</details>
---

### Exercise 4 - Beginner

Calculate the sum of the numbers from 1 to 20 using the `sum()` function.

<details><summary>Click for Solution</summary>
	
> Use the `sum()` function with a sequence of numbers from 1 to 20.

#### Solution

```r
# Sum the numbers from 1 to 20
sum(1:20)
```
</details>
---

### Exercise 5 - Intermediate

Read the first 10 rows of `chicago_air.csv` using `read.csv()`.

<details><summary>Click for Solution</summary>
	
> Use `read.csv()` and the `head()` function to read and display the first 10 rows.

#### Solution

```r
# Load the data
chicago_air <- read.csv("/mnt/data/chicago_air.csv")

# Display the first 10 rows
head(chicago_air, 10)
```
</details>
---

### Exercise 6 - Intermediate

Calculate the mean of the `ozone` column from the `chicago_air` dataset.

<details><summary>Click for Solution</summary>
	
> Use the `mean()` function on the `ozone` column.

#### Solution

```r
# Calculate the mean of the ozone column
mean(chicago_air$ozone, na.rm = TRUE)
```
</details>
---

### Exercise 7 - Intermediate

Find the minimum and maximum values of the `temp` column in the `chicago_air` dataset.

<details><summary>Click for Solution</summary>
	
> Use the `min()` and `max()` functions with the `temp` column.

#### Solution

```r
# Find the minimum temperature
min_temp <- min(chicago_air$temp, na.rm = TRUE)

# Find the maximum temperature
max_temp <- max(chicago_air$temp, na.rm = TRUE)

# Display the results
min_temp
max_temp
```
</details>
---

### Exercise 8 - Intermediate

Filter the `chicago_air` dataset to include only the rows where the `pressure` is greater than 1010 millibars.

<details><summary>Click for Solution</summary>
	
> Use the `subset()` function to filter the rows.

#### Solution

```r
# Filter rows where pressure is greater than 1010
high_pressure <- subset(chicago_air, pressure > 1010)

# Display the filtered data
head(high_pressure)
```
</details>
---

### Exercise 9 - Advanced

Import `chicago_air.csv` and create a new column that categorizes `temp` into "Hot" (above 85 degrees) and "Cold" (85 degrees or below).

<details><summary>Click for Solution</summary>
	
> Use `read.csv()` to import the data and `ifelse()` to create the new column.

#### Solution

```r
# Load the data
chicago_air <- read.csv("/mnt/data/chicago_air.csv")

# Create a new column categorizing temperature
chicago_air$temp_category <- ifelse(chicago_air$temp > 85, "Hot", "Cold")

# Display the updated data
head(chicago_air)
```
</details>
---

### Exercise 10 - Advanced

Read `chicago_air.csv` and calculate the average `ozone` levels for each month.

<details><summary>Click for Solution</summary>
	
> Use `read.csv()` to import the data, and then use `tapply()` to calculate the average ozone levels by month.

#### Solution

```r
# Load the data
chicago_air <- read.csv("/mnt/data/chicago_air.csv")

# Calculate average ozone levels for each month
average_ozone_by_month <- tapply(chicago_air$ozone, chicago_air$month, mean, na.rm = TRUE)

# Display the results
average_ozone_by_month
```
</details>
---
