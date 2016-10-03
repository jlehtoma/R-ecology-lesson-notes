000-challenges
========================================================
author:
date:
autosize: true

Challenge 1.1
========================================================

* **Question**: We’ve seen that atomic vectors can be of type character,
  numeric, integer, and logical. But what happens if we try to mix these types in
  a single vector?
<!-- * _Answer_: R implicitly converts them to all be the same type -->

* **Question**: What will happen in each of these examples? (hint: use `class()`
  to check the data type of your objects):

```r
num_char <- c(1, 2, 3, 'a')
num_logical <- c(1, 2, 3, TRUE)
char_logical <- c('a', 'b', 'c', TRUE)
tricky <- c(1, 2, 3, '4')
```

* **Question**: Why do you think it happens?

* **Question**: Can you draw a diagram that represents the hierarchy of the data
  types?

Challenge 1.2
========================================================

* Can you figure out why `"four" > "five"` returns `TRUE`?


Challenge 1.3
========================================================

* **Question**: Why does the following piece of code give an error message?

```r
sample <- c(2, 4, 4, "NA", 6)
mean(sample, na.rm = TRUE)
```
<!-- * _Answer_: Because R recognizes the NA in quotes as a character. -->

* **Question**: Why does the error message say the argument is not numeric?

Challenge 2.1
========================================================

Based on the output of `str(surveys)`, can you answer the following questions?

* What is the class of the object `surveys`?
* How many rows and how many columns are in this object?
* How many species have been recorded during these surveys?

Challenge 2.2
========================================================

he function `plot()` can be used to quickly create a bar plot of a factor. For instance, for the factor

`exprmt <- factor(c("treat1", "treat2", "treat1", "treat3", "treat1", "control", "treat1", "treat2", "treat3"))`,

the code `plot(exprmt)` gives you a barplot of the number of observations at each level, as shown
below.

* What determines the order in which the treatments are listed in the plot? (Hint: use `str` to inspect the factor.)
* How can you recreate this plot with "control" listed last instead
of first?

Challenge 3.1.1
========================================================

1. There are a few mistakes in this hand crafted `data.frame`, can you spot and
fix them? Don't hesitate to experiment!

    
    ```r
    author_book <- data.frame(author_first=c("Charles", "Ernst", "Theodosius"),
                              author_last=c(Darwin, Mayr, Dobzhansky),
                              year=c(1942, 1970))
    ```

Challenge 3.1.2
========================================================

2. Can you predict the class for each of the columns in the following example?
   Check your guesses using `str(country_climate)`:
     * Are they what you expected?  Why? Why not?
     * What would have been different if we had added `stringsAsFactors = FALSE` to this call?
     * What would you need to change to ensure that each column had the accurate data type?


```r
country_climate <- data.frame(country=c("Canada", "Panama", "South Africa", "Australia"),
                                   climate=c("cold", "hot", "temperate", "hot/temperate"),
                                   temperature=c(10, 30, 18, "15"),
                                   northern_hemisphere=c(TRUE, TRUE, FALSE, "FALSE"),
                                   has_kangaroo=c(FALSE, FALSE, FALSE, 1))
```

Challenge 3.1.3
========================================================

We introduced you to the `data.frame()` function and `read.csv()`, but what if we are starting with some vectors? The best way to do this is to pass those vectors to the `data.frame()` function, similar to the above.


```r
color <- c("red", "green", "blue", "yellow")
counts <- c(50, 60, 65, 82)
new_datarame <- data.frame(colors = color, counts = counts)
```

Try making your own new data frame from some vectors. You can check the data
type of the new object using `class()`.

Challenge 3.2
========================================================

1. The function `nrow()` on a `data.frame` returns the number of rows. Use it,
   in conjunction with `seq()` to create a new `data.frame` called
   `surveys_by_10` that includes every 10th row of the survey data frame
   starting at row 10 (10, 20, 30, ...)

2. Create a `data.frame` containing only the observations from row 1999 of the
   `surveys` dataset.

3. Notice how `nrow()` gave you the number of rows in a `data.frame`? Use `nrow()`
  instead of a row number to make a `data.frame` with observations from only the last
  row of the `surveys` dataset.

4. Now that you've seen how `nrow()` can be used to stand in for a row index, let's combine
  that behavior with the `-` notation above to reproduce the behavior of `head(surveys)`
  excluding the 7th through final row of the `surveys` dataset.

Challenge 4.1
========================================================

Using pipes, subset the data to include individuals collected before 1995, and retain the columns `year`, `sex`, and `weight.`

Challenge 4.2
========================================================

Create a new dataframe from the survey data that meets the following
criteria: contains only the `species_id` column and a column that contains
values that are half the `hindfoot_length` values (e.g. a new column
`hindfoot_half`). In this `hindfoot_half` column, there are no NA values
and all values are < 30.

**Hint**: think about how the commands should be ordered to produce this data frame!

Challenge 4.3
========================================================

How many individuals were caught in each `plot_type` surveyed?

Challenge 4.4
========================================================

What was the heaviest animal measured in each year? Return the columns `year`,
`genus`, `species_id`, and `weight`.

Challenge 4.5
========================================================

Download a messy version of the surveys data and see how you could
tidy it up using the tools from tidyr-package.


```r
# Don't usually do this!
download.file("http://bit.ly/dc-messy-data", "data/messy_survey_data.csv")
```

```r
messy_survey_data <- read.csv("data/messy_survey_data.csv")
```

Challenge 5.1
========================================================

Boxplots are useful summaries, but hide the *shape* of the distribution. For
example, if there is a bimodal distribution, this would not be observed with a
boxplot. An alternative to the boxplot is the violin plot (sometimes known as a
beanplot), where the shape (of the density of points) is drawn.

- Replace the box plot with a violin plot; see `geom_violin()`

In many types of data, it is important to consider the *scale* of the
observations.  For example, it may be worth changing the scale of the axis to
better distribute the observations in the space of the plot.  Changing the scale
of the axes is done similarly to adding/modifying other components (i.e., by
incrementally adding commands).

- Represent weight on the log10 scale; see `scale_y_log10()`

- Create boxplot for `hindfoot_length`.

Challenge 5.2
========================================================

Use what you just learned to create a plot that depicts how the average weight
of each species changes through the years.

Challenge 5.3
========================================================

With all of this information in hand, please take another five minutes to either
improve one of the plots generated in this exercise or create a beautiful graph
of your own. Use the RStudio ggplot2 cheat sheet, which we linked earlier for
inspiration.

Here are some ideas:

* See if you can change thickness of the lines.
* Can you find a way to change the name of the legend? What about its labels?
* Use a different color palette (see http://www.cookbook-r.com/Graphs/Colors_(ggplot2)/)

Challenge 6.1
========================================================

1. Write a query that returns counts of genus by `plot_id`
2. You can join multiple tables together in SQL using the following syntax
where foreign key refers to your unique id (e.g., `species_id`):

```{}
SELECT table.col, table.col
FROM table1 JOIN table2
ON table1.key = table2.key
JOIN table3 ON table2.key = table3.key
```

Write a query that joins the species, plot, and survey tables together. The
query should return counts of genus by plot type. Then create a bar plot of
your results in R.

Challenge 6.2
========================================================

Add the remaining tables to the existing database. Open the new database
using the Firefox SQLite manager to verify that the database was built
successfully.

