# Additional Exercises for Lesson 4 - Writing Functions, Conditionals, and Loops

These are optional exercises that you can attempt for further practice over the material covered in Lesson 4.  

### Exercise 1 - Beginner

Write a function `ppm_to_ppb` that converts parts per million (ppm) to parts per billion (ppb).

<details><summary>Click for Solution</summary>
	
> This function multiplies the ppm value by 1000 to convert it to ppb.

#### Solution

```r
ppm_to_ppb <- function(ppm) {
  return(ppm * 1000)
}
```
</details>
---

### Exercise 2 - Beginner

Write a function `check_value` that prints "warning" if a value is above a given threshold and "OK" if below.

<details><summary>Click for Solution</summary>
	
> This function compares the value to the threshold using an if statement.

#### Solution

```r
check_value <- function(value, threshold) {
  if (value > threshold) {
    print("warning")
  } else {
    print("OK")
  }
}
```
</details>
---

### Exercise 3 - Beginner

Use a `for` loop to iterate through the `temp` column of `chicago_air` and print values above 90 degrees.

<details><summary>Click for Solution</summary>
	
> This loop checks each temperature value and prints it if it's above 90.

#### Solution

```r
for (temp in chicago_air$temp) {
  if (temp > 90) {
    print(temp)
  }
}
```
</details>
---

### Exercise 4 - Intermediate

Write a function `temp_category` that categorizes temperatures in `chicago_air` as "High" if above 85, "Medium" if between 65 and 85, and "Low" if below 65.

<details><summary>Click for Solution</summary>
	
> This function uses if-else statements to categorize the temperature.

#### Solution

```r
temp_category <- function(temp) {
  if (temp > 85) {
    return("High")
  } else if (temp >= 65) {
    return("Medium")
  } else {
    return("Low")
  }
}

chicago_air$temp_category <- sapply(chicago_air$temp, temp_category)
```
</details>
---

### Exercise 5 - Intermediate

Write a function `monthly_avg` to calculate the average ozone level for each month in `chicago_air`.

<details><summary>Click for Solution</summary>
	
> This function uses the `tapply` function to calculate the monthly averages.

#### Solution

```r
monthly_avg <- function(data) {
  return(tapply(data$ozone, data$month, mean, na.rm = TRUE))
}

monthly_averages <- monthly_avg(chicago_air)
print(monthly_averages)
```
</details>
---

### Exercise 6 - Intermediate

Use `ifelse()` to create a new column in `chicago_air` named `pressure_category` that is "High" if pressure is above 1015 millibars and "Low" otherwise.

<details><summary>Click for Solution</summary>
	
> This task uses the `ifelse` function to create a new column based on pressure values.

#### Solution

```r
chicago_air$pressure_category <- ifelse(chicago_air$pressure > 1015, "High", "Low")
```
</details>
---

### Exercise 7 - Advanced

Write a custom function `daily_summary` that returns a data frame with daily summaries (mean, max, and min) of temperature and ozone levels from `chicago_air`.

<details><summary>Click for Solution</summary>
	
> This function calculates daily summaries using the `aggregate` function.

#### Solution

```r
daily_summary <- function(data) {
  summary <- data.frame(
    date = unique(data$date),
    temp_mean = tapply(data$temp, data$date, mean, na.rm = TRUE),
    temp_max = tapply(data$temp, data$date, max, na.rm = TRUE),
    temp_min = tapply(data$temp, data$date, min, na.rm = TRUE),
    ozone_mean = tapply(data$ozone, data$date, mean, na.rm = TRUE),
    ozone_max = tapply(data$ozone, data$date, max, na.rm = TRUE),
    ozone_min = tapply(data$ozone, data$date, min, na.rm = TRUE)
  )
  return(summary)
}

daily_summaries <- daily_summary(chicago_air)
print(daily_summaries)
```
</details>
---

### Exercise 8 - Advanced

Use `for` loops and `ifelse()` to create a new column `temp_range` in `chicago_air` that categorizes temperatures into "Very High", "High", "Medium", "Low", and "Very Low".

<details><summary>Click for Solution</summary>
	
> This solution uses nested if-else statements within a loop to categorize temperature ranges.

#### Solution

```r
chicago_air$temp_range <- rep(NA, nrow(chicago_air))

for (i in 1:nrow(chicago_air)) {
  temp <- chicago_air$temp[i]
  chicago_air$temp_range[i] <- ifelse(temp > 95, "Very High",
                                ifelse(temp > 85, "High",
                                ifelse(temp > 65, "Medium",
                                ifelse(temp > 50, "Low", "Very Low"))))
}
```
</details>
---

### Exercise 9 - Advanced

Write a function `calc_stats` that computes mean, median, standard deviation, and IQR for numeric columns in `chicago_air`. Use `apply()` for calculations.

<details><summary>Click for Solution</summary>
	
> This function uses `apply` to compute statistical summaries for each numeric column.

#### Solution

```r
calc_stats <- function(data) {
  stats <- apply(data[, sapply(data, is.numeric)], 2, function(x) {
    c(
      mean = mean(x, na.rm = TRUE),
      median = median(x, na.rm = TRUE),
      sd = sd(x, na.rm = TRUE),
      IQR = IQR(x, na.rm = TRUE)
    )
  })
  return(stats)
}

statistics <- calc_stats(chicago_air)
print(statistics)
```
</details>
---

### Exercise 10 - Advanced

Create a function `extreme_days` that identifies days with extreme temperatures (above 95 or below 40 degrees) and returns a subset of `chicago_air` for those days.

<details><summary>Click for Solution</summary>
	
> This function subsets the data based on extreme temperature conditions.

#### Solution

```r
extreme_days <- function(data) {
  subset <- data[data$temp > 95 | data$temp < 40, ]
  return(subset)
}

extreme_temp_days <- extreme_days(chicago_air)
print(extreme_temp_days)
```
</details>
---
