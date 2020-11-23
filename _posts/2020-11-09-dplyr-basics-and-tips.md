---
layout: post
title:  "The `dplyr` Package Basics"
date:   2020-11-09 12:54:04 -0700
categories: dplyr basics package introduction
---
# The `dplyr` Package Basics
By. Kyle Pratt  
November 11th, 2020

#### What is `dplyr`?
`dplyr` is a package in R that contains functions for quick and easy data manipulation. The `dplyr` base package works on a data frame.

#### 5 Verbs to Describe the Uses of `dplyr`
1. **Select** certain columns of data  
2. **Filter** to select certain rows.
3. **Arrange** the rows of data.
4. **Mutate** the data to contain new columns.
5. **Summarize** pieces of the data.  

#### What is the 'pipe' and how is it used?
The 'pipe' that is used in `dplyr` originally comes from the `magrittr` package and is represented as so: `%>%`. It allows for the user to simply pass the altered data frame to another function and continuously alter the data.

Another way to think of the pipe is saying the word then in between the functions. So if you wanted to first `group_by()` then `summarize()`. You would us the `%>%` in replacement of the word "then".

#### Examples of functions
1. `arrange()`
  * This function arrange the rows of a data frame by the values of selected columns
  * It takes a data frame as the first variable passed to it and variables or functions as inputs as well
2. `tally()`
  * This function will count the unique values of 1 or more variables
  * It takes a data frame as the first variable passed to it and variables to group by
3. `select()`
  * This function will subset columns using their names and types
  * It takes a data frame and one or more expressions to select
4. `summarize()`
  * This function will create a new data frame with a row for each combination of grouping variables
  * It takes a data frame and name value pairs or summary functions
5. `group_by()`
  * This function will group by one or more variables
  * It takes a data frame and variables or computations to group by
6. `filter()`
  * This function will subset a data frame and retain all rows satisfying the condition
  * It takes a data frame and expressions that return a logical value

#### Here is some sample code using these functions:

The following code chunks utilize an Apple COVID-19 mobility dataset. This dataset contains relative travel rates as a percentage or pre-pandemic travel. It is categorized by the location, date and type of transportation.

```r
count_cities_counties_by_type <- state_data %>%
  select(geo_type, region, transportation_type) %>%
  group_by(geo_type, transportation_type) %>%
  tally()
```
This code chunk would take the `state_data` data frame THEN select out the columns for `geo_type`, `region` and `transportation_type`THEN group by the unique `geo_type` and `transportation_type` THEN tally the unique values for each type. This is all stored in the variable `count_cities_counties_by_type`.

```r
state_data <- all_covid_data %>%
    dplyr::filter(sub_region == state_to_analyze)
```
This code chunk would take the `all_covid_data` THEN filter out the rows where the `sub_region` column is equal to the variable `state_to_analyze`. Then store those filtered results in the varaible `state_data`.

#### See the attached [dplyr cheat sheet](https://github.com/rstudio/cheatsheets/blob/master/data-transformation.pdf) for more tips and a graphical representation of some functions.


I hope you found this information helpful and happy coding!

-KP 11/23/20

#### References
1. https://dplyr.tidyverse.org/index.html
2. https://github.com/rstudio/cheatsheets/blob/master/data-transformation.pdf
3. https://seananderson.ca/2014/09/13/dplyr-intro/
