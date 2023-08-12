## Exercises


### Exercise 1

1. Plot the correlation between temperature and ozone. Use the `plot()` function with `chicago_air$temp` as `x` and `chicago_air$ozone` as `y`.

<details><summary>Click for Solution</summary>


	
> This will create a scatter plot of the correlation between temperature and ozone in the `chicago_air` data frame.

#### Solution

```r
plot(chicago_air$temp, chicago_air$ozone)
```



</details>

---


### Exercise 2

2. Convert the `date` column in the `chicago_air` data frame from a string to a `Date` object then print the first 5 rows. Use `as.Date()` for conversion.

<details><summary>Click for Hint</summary>

Use the `head()` function to print the first few rows of a data frame.
</details>
<details><summary>Click for Solution</summary>

#### Solution

```r
chicago_air$date <- as.Date(chicago_air$date)
head(chicago_air)
```



</details>

---


### Exercise 3

3. Plot ozone levels over time (date on the x-axis, ozone on the y-axis). Use `type = 'l'` to create a line plot.

<details><summary>Click for Solution</summary>


	
> This line plot will display ozone levels over time.

#### Solution

```r
plot(chicago_air$date, chicago_air$ozone, type = 'l')
```



</details>

---


### Exercise 4

4. Create a grid layout with two plots: One for the ozone data and another for the temperature data. Use the `par()` function with `mfrow = c(1,2)`.

<details><summary>Click for Solution</summary>


	
> This will create a grid of two plots: one displaying ozone levels over time and the other displaying temperature over time.

#### Solution

```r
par(mfrow = c(1,2))
plot(chicago_air$date, chicago_air$ozone, type='l')
plot(chicago_air$date, chicago_air$temp, type='l')
```



</details>

---


### Exercise 5

5. Convert the `date` column in `chicago_air` data frame to factors representing the day of the week using `factor()` and `weekdays()`. Then print the first 10 rows.

<details><summary>Click for Solution</summary>


	
> This will convert the date to a factor displaying the day of the week and will then print the first 10 rows.

#### Solution

```r
chicago_air$weekday <- factor(weekdays(chicago_air$date, abbreviate = TRUE))
head(chicago_air, 10)
```



</details>

---


### Exercise 6

6. Use `lattice` to create a line plot of ozone values over time. Use `xyplot()`.

<details><summary>Click for Solution</summary>


	
> This line plot displays ozone values over time.

#### Solution

```r
library(lattice)
xyplot(ozone ~ date, data = chicago_air, type = 'l')
```



</details>

---


### Exercise 7

7. Create a `ggplot` line graph of ozone over time. Use `geom_line()` to create the line graph.

<details><summary>Click for Solution</summary>


	
> This creates a line graph of ozone levels over time.

#### Solution

```r
library(ggplot2)
ggplot(chicago_air, aes(x = date, y = ozone)) + geom_line()
```



</details>

---


### Exercise 8

8. Reshape the `chicago_air` data frame into a long format. Use the `pivot_longer()` function from `tidyr`. Print the first 5 rows of reshaped data.

<details><summary>Click for Hint</summary>

Make sure to use the right column names in the `cols` argument of `pivot_longer` function.
</details>
<details><summary>Click for Solution</summary>


	
> This will reshape the data frame so each row is a unique id-variable combination.

#### Solution

```r
library(tidyr)
chicago_long <- pivot_longer(chicago_air, cols = c('ozone', 'temp', 'solar'))
head(chicago_long)
```



</details>

---


### Exercise 9

9. Using `ggplot` on the reshaped `chicago_long` data, create a plot with `date` on the x-axis, `value` on the y-axis, and color the points by `high_temp`. Use `geom_point()` to add points to the plots, and `facet_grid()` to create separate panels for each variable.

<details><summary>Click for Solution</summary>


	
> This creates a plot with date on the x-axis, value on the y-axis, and separate plots (facets) for each variable. Points are colored based on high temperature.

#### Solution

```r
ggplot(chicago_long, aes(x = date, y = value, color = high_temp)) + geom_point() + facet_grid(rows = vars(variable))
```



</details>

---


### Exercise 10

10. Save the plot you made in the previous question as a PNG file named 'my_plot.png'. Use `ggsave()` to save the plot.

<details><summary>Click for Solution</summary>


	
> This will save the last plot that was displayed in Rstudio to a PNG file named 'my_plot.png'.

#### Solution

```r
ggsave(filename = 'my_plot.png')
```



</details>

---

