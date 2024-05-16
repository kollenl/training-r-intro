# Additional Exercises for Lesson 5 - Plotting

These are optional exercises that you can attempt for further practice over the material covered in Lesson 5 - Plotting.

### Exercise 1 - Beginner

Create a basic scatter plot of `ozone` versus `temp` using the base `plot()` function from the `chicago_air` dataset.

<details><summary>Click for Solution</summary>
	
> This exercise helps you practice using the base `plot()` function to create a scatter plot.

#### Solution

```r
# Load necessary library and dataset
library(region5air)
data(chicago_air)

# Create a scatter plot
plot(chicago_air$temp, chicago_air$ozone, 
     main = "Scatter plot of Ozone vs Temperature", 
     xlab = "Temperature (F)", 
     ylab = "Ozone (ppm)")
```
</details>
---

### Exercise 2 - Beginner

Create a histogram of the `pressure` variable using the base `hist()` function from the `chicago_air` dataset.

<details><summary>Click for Solution</summary>
	
> This exercise helps you practice creating histograms to visualize the distribution of a variable.

#### Solution

```r
# Load necessary library and dataset
library(region5air)
data(chicago_air)

# Create a histogram
hist(chicago_air$pressure, 
     main = "Histogram of Barometric Pressure", 
     xlab = "Pressure (millibars)",
     col = "lightblue")
```
</details>
---

### Exercise 3 - Intermediate

Using the `ggplot2` package, create a box plot of `ozone` levels for each day of the week using `chicago_air`. Ensure that the `weekday` variable is treated as a factor.

<details><summary>Click for Solution</summary>
	
> This exercise introduces you to creating box plots with `ggplot2` and handling categorical variables.

#### Solution

```r
# Load necessary libraries and dataset
library(region5air)
library(ggplot2)
data(chicago_air)

# Convert weekday to a factor
chicago_air$weekday <- as.factor(chicago_air$weekday)

# Create a box plot
ggplot(chicago_air, aes(x = weekday, y = ozone)) +
  geom_boxplot() +
  labs(title = "Box Plot of Ozone Levels by Day of the Week",
       x = "Day of the Week",
       y = "Ozone (ppm)")
```
</details>
---

### Exercise 4 - Intermediate

Create a time series plot of `temp` over the year using the base `plot()` function. Ensure the `date` column is converted to the `Date` class.

<details><summary>Click for Solution</summary>
	
> This exercise helps you practice working with date data and creating time series plots.

#### Solution

```r
# Load necessary library and dataset
library(region5air)
data(chicago_air)

# Convert date column to Date class
chicago_air$date <- as.Date(chicago_air$date)

# Create a time series plot
plot(chicago_air$date, chicago_air$temp, 
     type = "l", 
     main = "Temperature Over Time", 
     xlab = "Date", 
     ylab = "Temperature (F)", 
     col = "red")
```
</details>
---

### Exercise 5 - Intermediate

Using `ggplot2`, create a histogram of `pressure` values for each month. Facet the histogram by `month`.

<details><summary>Click for Solution</summary>
	
> This exercise helps you practice faceting in `ggplot2` to create multiple plots based on a factor.

#### Solution

```r
# Load necessary libraries and dataset
library(region5air)
library(ggplot2)
data(chicago_air)

# Create a faceted histogram
ggplot(chicago_air, aes(x = pressure)) +
  geom_histogram(binwidth = 5, fill = "blue", color = "black") +
  facet_wrap(~ month) +
  labs(title = "Histogram of Barometric Pressure by Month",
       x = "Pressure (millibars)",
       y = "Frequency")
```
</details>
---

### Exercise 6 - Advanced

Create a scatter plot of `temp` versus `ozone` using `ggplot2`, and color the points by `month`. Add a smoothing line to show the trend.

<details><summary>Click for Solution</summary>
	
> This exercise combines scatter plots, coloring by groups, and adding trend lines using `ggplot2`.

#### Solution

```r
# Load necessary libraries and dataset
library(region5air)
library(ggplot2)
data(chicago_air)

# Create a scatter plot with trend line
ggplot(chicago_air, aes(x = temp, y = ozone, color = as.factor(month))) +
  geom_point() +
  geom_smooth(method = "loess") +
  labs(title = "Scatter Plot of Ozone vs Temperature",
       x = "Temperature (F)",
       y = "Ozone (ppm)",
       color = "Month")
```
</details>
---

### Exercise 7 - Advanced

Using `ggplot2`, create a line plot of `temp` over time and add a second line for `ozone` levels. Ensure that the `date` column is converted to the `Date` class and use different colors for each line.

<details><summary>Click for Solution</summary>
	
> This exercise helps you practice creating multi-line plots in `ggplot2`.

#### Solution

```r
# Load necessary libraries and dataset
library(region5air)
library(ggplot2)
data(chicago_air)

# Convert date column to Date class
chicago_air$date <- as.Date(chicago_air$date)

# Create a line plot
ggplot(chicago_air, aes(x = date)) +
  geom_line(aes(y = temp, color = "Temperature")) +
  geom_line(aes(y = ozone * 100, color = "Ozone")) + # scale ozone for better visualization
  labs(title = "Temperature and Ozone Levels Over Time",
       x = "Date",
       y = "Value",
       color = "Parameter") +
  scale_color_manual(values = c("Temperature" = "red", "Ozone" = "blue")) +
  scale_y_continuous(
    name = "Temperature (F)",
    sec.axis = sec_axis(~./100, name = "Ozone (ppm)")
  )
```
</details>
---

### Exercise 8 - Advanced

Create a pairwise plot of all numeric variables in `chicago_air` using the `pairs()` function. Add a regression line to each scatter plot.

<details><summary>Click for Solution</summary>
	
> This exercise introduces you to creating pairwise plots and adding regression lines.

#### Solution

```r
# Load necessary library and dataset
library(region5air)
data(chicago_air)

# Create pairwise plots with regression lines
pairs(chicago_air[, c("ozone", "temp", "pressure")], 
      panel = function(x, y) {
        points(x, y)
        abline(lm(y ~ x), col = "red")
      },
      main = "Pairwise Plots with Regression Lines")
```
</details>
---

### Exercise 9 - Advanced

Using `ggplot2`, create a density plot of `ozone` levels and fill the density by `month`. Add transparency to the filled areas.

<details><summary>Click for Solution</summary>
	
> This exercise helps you practice creating density plots and using transparency for better visualization.

#### Solution

```r
# Load necessary libraries and dataset
library(region5air)
library(ggplot2)
data(chicago_air)

# Create a density plot
ggplot(chicago_air, aes(x = ozone, fill = as.factor(month))) +
  geom_density(alpha = 0.4) +
  labs(title = "Density Plot of Ozone Levels by Month",
       x = "Ozone (ppm)",
       fill = "Month")
```
</details>
---

### Exercise 10 - Advanced

Create a bar plot of the mean `ozone` level for each `weekday` using `ggplot2`. Add error bars to represent the standard deviation.

<details><summary>Click for Solution</summary>
	
> This exercise combines bar plots with error bars to represent variability in the data.

#### Solution

```r
# Load necessary libraries and dataset
library(region5air)
library(ggplot2)
library(dplyr)
data(chicago_air)

# Calculate mean and standard deviation of ozone by weekday
ozone_stats <- chicago_air %>%
  group_by(weekday) %>%
  summarize(mean_ozone = mean(ozone, na.rm = TRUE),
            sd_ozone = sd(ozone, na.rm = TRUE))

# Create a bar plot with error bars
ggplot(ozone_stats, aes(x = as.factor(weekday), y = mean_ozone)) +
  geom_bar(stat = "identity", fill = "skyblue") +
  geom_errorbar(aes(ymin = mean_ozone - sd_ozone, ymax = mean_ozone + sd_ozone), width = 0.2) +
  labs(title = "Mean Ozone Level by Day of the Week",
       x = "Day of the Week",
       y = "Mean Ozone (ppm)")
```
</details>
---
