---
layout: post
title:  "Introduction to programming functions in R!"
date:   2020-11-08 12:54:04 -0700
categories: R topics
---
In this post you will learn the basics of functions in R.  This will include:
what a function is, how to set up a function, and how to call for a function
from another R script.

# What is a function?
In programming, a function is a subroutine that performs some calculation with
given variables.  These variables are given by a program and a result is
returned.

You can think of this type function the same way you would think about a
mathematical one.  
The function is a shorthand way to make different variables go through the
same process without needing to rewrite the formula every time.

For instance: if you have the function y=x^2, and are given a list of x
variables (1:5).  You are doing the same function 5 times with different
variables giving different outputs.  Here the function would be running in
a loop of y=1^2, y=2^2, y=3^2, y=4^2, and y=5^2.  

The difference between this mathematical function and a programming function
is that the programming function is located on its own R script and can be
called for from any other script contained in the same directory.

# How to set up a function
the basic outline for a function in R is
```ruby
 `func_name <- function (argument){  
    statement`  
   `}`
```
The function name can be what ever you want the function to be called.  If you
want a function that reads in a csv file containing data on different states,
and then subset that data to look at one state at a time, you might name it
"look_at_state_data".  So far we have `look_at_state_data`.

Next we need to assign a function to that name with variables (the argument
  ).  You use the `<-` symbol to
tell R that what ever follows the symbol is named what immediately proceeds it.
To keep functions more dynamic, the variables should be named based on the
type of input you will use.    
For this example one of the variables  will be  
`(input_file_name)` and
`(subsetted_state)`  
we now have the function
```ruby
  `look_at_state_data <- function(input_file_name,  
                                  subsetted_state){

                                      }`
```                                      


Next you need your statement.  Here is where you read in your csv file.  It is
 also a good idea to give the file a new variable name.  Here you might call
 this variable "all_state_data" as this file has all of the states in it.  
The function now looks like:
```ruby
  `look_at_state_data <- function(input_file_name,  
                                  subsetted_state){
    all_state_data <- read.csv(input_file_name)
    }`
```                           
Now that the csv file is loaded into the function, you need to subset it to
look at one state at a time.  you would need to go into the csv file to see
how it is formatted and how the data is assigned to a state.  If the state names
are all in one column named "state" all you have to do is use a pipe and the
dpylr package to filter the column.

```ruby
  `look_at_state_data <- function(input_file_name,  
                                  subsetted_state){
    all_state_data <- read.csv(input_file_name)
    one_state_data <- all_state_data  %>%
      dplyr::filter(state == subsetted_state)}                                  
    }`
```   
You now have a function that will go through a csv file and pars out any
state of your choosing. The only problem is you cannot see what the function
did.  As a last step in the function you should tell it to make a new csv
file that only contains the data of the state you are interested in. This new
csv file can be written to go anywhere, but for this example it will go into an
output directory with a file name based on the state you are looking at.                       
```ruby
  `look_at_state_data <- function(input_file_name,  
                                    subsetted_state){
    all_state_data <- read.csv(input_file_name)
    one_state_data <- all_state_data  %>%
      dplyr::filter(state == subsetted_state)
    write.csv(one_state_data, path = "output/individual_state_data/subsetted_state.csv")                                    
    }`
```   
It is important to make sure that all of the variables you are making in this function are unique so that you do not break your script.
