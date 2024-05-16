# Additional Exercises for Lesson 7: Quality Assurance

These are optional exercises that you can attempt for further practice over the material covered in Lesson 7.

### Exercise 1 - Beginner

Find the data types for the `chicago_air` data frame.

<details><summary>Click for Solution</summary>
	
> Use `str()` to display the structure of the data frame.

#### Solution

```r
# Load the chicago_air data
library(region5air)
data(chicago_air)

# Display the structure of the data frame
str(chicago_air)
```
</details>
---

### Exercise 2 - Beginner

Create a vector with inconsistent character values and standardize them using logical expressions.

<details><summary>Click for Solution</summary>
	
> Standardize character values by converting them to a consistent format using logical expressions and the `tolower()` function.

#### Solution

```r
# Create a vector with inconsistent character values
vec <- c("Yes", "NO", "yes", "No", "YES", "no")

# Standardize the character values
vec_standardized <- ifelse(tolower(vec) == "yes", "yes", "no")

vec_standardized
```
</details>
---

### Exercise 3 - Beginner

Use a boxplot to check for outliers in the ozone column of `chicago_air`.

<details><summary>Click for Solution</summary>
	
> Use `boxplot()` to visualize outliers.

#### Solution

```r
# Load the chicago_air data
library(region5air)
data(chicago_air)

# Create a boxplot for the ozone column
boxplot(chicago_air$ozone, main = "Boxplot of Ozone Levels", ylab = "Ozone (ppm)")
```
</details>
---

### Exercise 4 - Intermediate

Find and handle any missing values in the `chicago_air` data frame.

<details><summary>Click for Solution</summary>
	
> Use `is.na()` and `sum()` to find missing values, then handle them using `na.omit()`.

#### Solution

```r
# Load the chicago_air data
library(region5air)
data(chicago_air)

# Find missing values
missing_values <- sum(is.na(chicago_air))
print(missing_values)

# Handle missing values by removing rows with any NA values
chicago_air_clean <- na.omit(chicago_air)
```
</details>
---

### Exercise 5 - Intermediate

Convert the `date` column in `chicago_air` to Date class and verify the conversion.

<details><summary>Click for Solution</summary>
	
> Use `as.Date()` to convert and `str()` to verify.

#### Solution

```r
# Load the chicago_air data
library(region5air)
data(chicago_air)

# Convert the date column to Date class
chicago_air$date <- as.Date(chicago_air$date, format = "%Y-%m-%d")

# Verify the conversion
str(chicago_air$date)
```
</details>
---

### Exercise 6 - Intermediate

Check for any duplicate rows in the `chicago_air` data frame and remove them.

<details><summary>Click for Solution</summary>
	
> Use `duplicated()` to identify duplicates and remove them using `!duplicated()`.

#### Solution

```r
# Load the chicago_air data
library(region5air)
data(chicago_air)

# Check for duplicate rows
duplicate_rows <- duplicated(chicago_air)
print(sum(duplicate_rows))

# Remove duplicate rows
chicago_air_unique <- chicago_air[!duplicate_rows, ]
```
</details>
---

### Exercise 7 - Advanced

Detect and handle outliers in the temperature column using the IQR method.

<details><summary>Click for Solution</summary>
	
> Calculate the IQR, then use it to find and remove outliers.

#### Solution

```r
# Load the chicago_air data
library(region5air)
data(chicago_air)

# Calculate the IQR
temp_iqr <- IQR(chicago_air$temp, na.rm = TRUE)
temp_q1 <- quantile(chicago_air$temp, 0.25, na.rm = TRUE)
temp_q3 <- quantile(chicago_air$temp, 0.75, na.rm = TRUE)

# Define the outlier thresholds
lower_bound <- temp_q1 - 1.5 * temp_iqr
upper_bound <- temp_q3 + 1.5 * temp_iqr

# Detect and remove outliers
chicago_air_no_outliers <- chicago_air[chicago_air$temp >= lower_bound & chicago_air$temp <= upper_bound, ]
```
</details>
---

### Exercise 8 - Advanced

Convert the `month` and `weekday` columns in `chicago_air` to factors and verify the conversion.

<details><summary>Click for Solution</summary>
	
> Use `as.factor()` to convert and `str()` to verify.

#### Solution

```r
# Load the chicago_air data
library(region5air)
data(chicago_air)

# Convert month and weekday columns to factors
chicago_air$month <- as.factor(chicago_air$month)
chicago_air$weekday <- as.factor(chicago_air$weekday)

# Verify the conversion
str(chicago_air$month)
str(chicago_air$weekday)
```
</details>
---

### Exercise 9 - Advanced

Identify and clean any inconsistencies in the `date` column format in `chicago_air`.

<details><summary>Click for Solution</summary>
	
> Use regular expressions to identify and correct inconsistent date formats.

#### Solution

```r
# Load the chicago_air data
library(region5air)
data(chicago_air)

# Identify inconsistencies using regex (assuming they exist)
inconsistent_dates <- grep("^(\\d{4})-(\\d{2})-(\\d{2})$", chicago_air$date, invert = TRUE, value = TRUE)
print(inconsistent_dates)

# Assuming manual correction for illustration (no inconsistencies in actual data)
# Convert to consistent format if needed (example for demonstration)
chicago_air$date <- as.Date(chicago_air$date, format = "%Y-%m-%d")
```
</details>
---

### Exercise 10 - Advanced

Ensure all numeric columns in `chicago_air` have no non-numeric values.

<details><summary>Click for Solution</summary>
	
> Use `sapply()` to check for numeric values and clean if necessary.

#### Solution

```r
# Load the chicago_air data
library(region5air)
data(chicago_air)

# Check for non-numeric values in numeric columns
numeric_columns <- sapply(chicago_air, is.numeric)
non_numeric_values <- sapply(chicago_air[, numeric_columns], function(x) sum(!is.numeric(x)))

print(non_numeric_values)

# Convert any non-numeric entries to NA and remove them (for demonstration)
chicago_air_cleaned <- chicago_air
chicago_air_cleaned[!sapply(chicago_air_cleaned, is.numeric)] <- lapply(chicago_air_cleaned[!sapply(chicago_air_cleaned, is.numeric)], as.numeric)
chicago_air_cleaned <- na.omit(chicago_air_cleaned)
```
</details>
---
