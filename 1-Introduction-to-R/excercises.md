## Exercises


### Exercise 1

Add two numbers in R, say 25 and 75.

<details><summary>Click for Solution</summary>


	
> R allows you to do simple arithmetic operations such as addition, subtraction, multiplication, etc. directly. Here, we're simply adding two numbers.

#### Solution

```r
25 + 75
```

#### Output

```r
[1] 100
```



</details>

---


### Exercise 2

Create an R variable `x` that stores the value 10.

<details><summary>Click for Solution</summary>


	
> The arrow symbol (`<-`) is used to assign a value to a variable in R. In this case, we're storing the value 10 in a variable named `x`.

#### Solution

```r
x <- 10
```



</details>

---


### Exercise 3

Create a vector `v` that contains the numbers 1 through 5.

<details><summary>Click for Solution</summary>


	
> We use the `c()` function in R to combine elements into a vector.

#### Solution

```r
v <- c(1, 2, 3, 4, 5)
```



</details>

---


### Exercise 4

Create a list `l` that contains a number (e.g., 5, a string (e.g., 'apple'), and a logical value (e.g., TRUE).

<details><summary>Click for Solution</summary>


	
> In R, we create a list using the `list()` function. A list can contain elements of different types.

#### Solution

```r
l <- list(5, 'apple', TRUE)
```



</details>

---


### Exercise 5

Create a data frame `df` with two columns, `name` and `age`, each containing three entries of your choosing.

<details><summary>Click for Solution</summary>


	
> In R, we can combine vectors of equal length into a data frame using the `data.frame()` function. Here, we're creating two vectors, `name` and `age`, and combining them into a data frame.

#### Solution

```r
df <- data.frame(name = c('Alice', 'Bob', 'Charlie'), age = c(25, 32, 28))
```



</details>

---


### Exercise 6

Create a character vector `fruit` that contains the values 'apple', 'banana', and 'grape'.

<details><summary>Click for Solution</summary>


	
> We use the `c()` function in R to combine elements into a vector.

#### Solution

```r
fruit <- c('apple', 'banana', 'grape')
```



</details>

---


### Exercise 7

Create a numeric vector `nums` with the values 10, 20 and 30 and add 5 to each element of the vector.

<details><summary>Click for Solution</summary>


	
> We can operate on every element of a vector at once in R.

#### Solution

```r
nums <- c(10, 20, 30)
nums + 5
```

#### Output

```r
[1] 15 25 35
```



</details>

---

