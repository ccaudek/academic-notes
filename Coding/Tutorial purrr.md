---
type: Zettel
title: 'Tutorial: purrr'
description: null
modificationDate: 2025-04-17 09:22
tags: []
coverImage: null
---

[link]([https://medium.com/number-around-us/mastering-purrr-from-basic-maps-to-functional-magic-in-r-e74ef3d0d349](https://medium.com/number-around-us/mastering-purrr-from-basic-maps-to-functional-magic-in-r-e74ef3d0d349))

---

Are map Functions Like apply Functions? It's a fair question! Both map and apply functions help you apply a function to elements in a data structure, but purrr takes it to a whole new level.

Here’s why purrr and its map functions are worth your attention:

- **Consistency**: purrr functions have a consistent naming scheme, making them easier to learn and remember.

- **Type Safety**: map functions in purrr return outputs of consistent types, reducing unexpected errors.

- **Integration**: Seamlessly integrate with other tidyverse packages, making your data wrangling pipeline smoother.

Let’s see a quick comparison:

```r
library(tidyverse)
# Using lapply (base R)
numbers <- list(1, 2, 3, 4, 5)
squared_lapply <- lapply(numbers, function(x) x^2)
# Using map (purrr)
squared_map <- map(numbers, ~ .x^2)
print(squared_lapply)
```

```text
[[1]]
[1] 1
[[2]]
[1] 4
[[3]]
[1] 9
[[4]]
[1] 16
[[5]]
[1] 25
```

```r
print(squared_map)
```

```text
[[1]]
[1] 1
[[2]]
[1] 4
[[3]]
[1] 9
[[4]]
[1] 16
[[5]]
[1] 25
```

Both do the same thing, but purrr’s `map` function is more readable and concise, especially when paired with the tidyverse syntax.

Here’s another example with a built-in dataset:

```r
# Using lapply with a built-in dataset
iris_split <- split(iris, iris$Species)
mean_sepal_length_lapply <- lapply(iris_split, function(df) mean(df$Sepal.Length))
# Using map with a built-in dataset
mean_sepal_length_map <- map(iris_split, ~ mean(.x$Sepal.Length))
print(mean_sepal_length_lapply)
```

```text
$setosa
[1] 5.006
$versicolor
[1] 5.936
$virginica
[1] 6.588
```

```r
print(mean_sepal_length_map)
```

```text
$setosa
[1] 5.006
$versicolor
[1] 5.936
$virginica
[1] 6.588
```

Again, the purrr version is cleaner and easier to understand at a glance.

---

### Simple Maps and Their Variants

Now that we know why purrr’s map functions are so cool, let’s dive into some practical examples. The `map` function family is like a Swiss Army knife for data transformation. It comes in different flavors depending on the type of output you want: logical, integer, character, or double.

Let’s start with the basic `map` function:

```r
library(tidyverse)
# Basic map example
numbers <- list(1, 2, 3, 4, 5)
squared_numbers <- map(numbers, ~ .x^2)
squared_numbers
```

```text
[[1]]
[1] 1
[[2]]
[1] 4
[[3]]
[1] 9
[[4]]
[1] 16
[[5]]
[1] 25
```

Now, let’s look at the type-specific variants:

**Logical (**`map_lgl`**)**:

```r
# Check if each number is even
is_even <- map_lgl(numbers, ~ .x %% 2 == 0)
is_even
```

```text
[1] FALSE  TRUE FALSE  TRUE FALSE
```

**Integer (**`map_int`**)**:

```r
# Double each number and return as integers
doubled_integers <- map_int(numbers, ~ .x * 2)
doubled_integers
```

```text
[1]  2  4  6  8 10
```

**Character (**`map_chr`**)**:

```r
# Convert each number to a string
number_strings <- map_chr(numbers, ~ paste("Number", .x))
number_strings
```

```text
[1] "Number 1" "Number 2" "Number 3" "Number 4" "Number 5"
```

**Double (**`map_dbl`**)**:

```r
# Half each number and return as doubles
halved_doubles <- map_dbl(numbers, ~ .x / 2)
halved_doubles
```

```text
[1] 0.5 1.0 1.5 2.0 2.5
```

---

### Not Only One Vector: map2 and pmap + Variants

`map2` **example**:

```r
library(tidyverse)
# Two vectors to work with
vec1 <- c(1, 2, 3)
vec2 <- c(4, 5, 6)
# Adding corresponding elements
sum_vecs <- map2(vec1, vec2, ~ .x + .y)
sum_vecs
```

```text
[[1]]
[1] 5
[[2]]
[1] 7
[[3]]
[1] 9
```

`pmap` **example**:

```r
# Creating a tibble for multiple lists
df <- tibble(
  a = 1:3,
  b = 4:6,
  c = 7:9
)
# Summing elements across columns
sum_pmap <- pmap(df, ~ ..1 + ..2 + ..3)
sum_pmap
```

```text
[[1]]
[1] 12
[[2]]
[1] 15
[[3]]
[1] 18
```

---

### Using imap for Indexed Mapping and Conditional Maps with `_if` and `_at`

`imap` **example**:

```r
library(tidyverse)
# Named list of scores
named_scores <- list(math = 90, science = 85, history = 78)
# Create descriptive strings
score_descriptions <- imap(named_scores, ~ paste(.y, "score is", .x))
score_descriptions
```

```text
$math
[1] "math score is 90"
$science
[1] "science score is 85"
$history
[1] "history score is 78"
```

`map_if` **example**:

```r
# Double only numeric elements
mixed_list <- list(1, "a", 3, "b", 5)
doubled_numbers <- map_if(mixed_list, is.numeric, ~ .x * 2)
doubled_numbers
```

```text
[[1]]
[1] 2
[[2]]
[1] "a"
[[3]]
[1] 6
[[4]]
[1] "b"
[[5]]
[1] 10
```

---

### Walk and Modify Functions

`walk` **example**:

```r
library(tidyverse)
# Print each number
walk(numbers, ~ print(.x))
```

```text
[1] 1
[1] 2
[1] 3
[1] 4
[1] 5
```

`modify` **example**:

```r
# Add 10 to each element
modified_numbers <- modify(numbers, ~ .x + 10)
modified_numbers
```

```text
[[1]]
[1] 11
[[2]]
[1] 12
[[3]]
[1] 13
[[4]]
[1] 14
[[5]]
[1] 15
```

---

### Gift for Patient Readers

**Custom function for multiple transformations**:

```r
# Define a function to apply multiple operations
apply_funs <- function(x, ...) purrr::map_dbl(list(...), ~ .x(x))
# Apply to a vector
number <- 1:48
results <- apply_funs(number, mean, median, sd)
results
```

```text
[1] 24.5 24.5 14.0
```

---

