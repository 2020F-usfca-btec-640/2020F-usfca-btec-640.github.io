---
layout: post
title:  "Introduction to programming functions in R!"
date:   2020-11-22 12:54:04 -0700
categories: R topics
author: Jaclyn Cherry
---
In this post you will learn the basics of functions in R.  This will include:
what a function is, how to set up a function, and how to call a function
from another R script.

# What is a function?
In programming, a function is a subroutine that performs some calculation with
given variables.  These variables are given by a program and a result is
returned.

You can think of this type of function the same way you would think about a
mathematical one.  
The function is a shorthand way to make different variables go through the
same process without needing to rewrite the formula every time.  Functions also
allow for your code and projects to be more reproducible for others that may use
your code.

For instance: if you have the function y=x^2, and are given a list of x
variables (1:5).  You are doing the same function 5 times with different
variables giving different outputs.  Here the function would be running in
a loop of y=1^2, y=2^2, y=3^2, y=4^2, and y=5^2.  

The difference between this mathematical function and a programming function
that you make is that the programming function can be located on its own R
script and can then be called from any other script. The function could also be
on the same script as where it will be used; however, keeping them on their own
script improves the general organization of your project and allows for you to
call that function on other scripts.

There are also functions built into R's base and the packages that you can
install, however it is necessary to make your own functions at times to do
specific tasks.

# How to set up a function
The basic outline for making a function in R is
```r
 func_name <- function (argument){  
    statement`  
   `}
```
The function name can be what ever you want.  If you
want a function that reads in a csv file containing data on different states
and then subset that data to look at a specific state, you might name it
"look_at_state_data".  It is important to note that the names of your Functions
should be both descriptive and short so that you and others that see your code
know what the function does and can tell your functions apart from each other.  
So now we have `func_name = look_at_state_data`.

Next we need to assign a function to that name with variables (the argument).
You use the `<-` symbol to tell R that what ever follows the symbol is named
what immediately proceeds it.
To keep functions more dynamic, the variables should be named based on the
type of input you will use.    
For this example one of the variables  will be  
`(input_file_name)` and
`(subsetted_state)`.  

We now have the function:
```r
  look_at_state_data <- function(input_file_name,
                                  subsetted_state){
   }
```                                      


Next you need your statement.  Here is where you read in your csv file.  It is
 also a good idea to give the file a new variable name.  Here you might call
 this variable "all_state_data" as this file has all of the states in it.  
The function now looks like:
```r
  look_at_state_data <- function(input_file_name,  
                                  subsetted_state){
    all_state_data <- read.csv(input_file_name)
    }
```                           
Now that the csv file is loaded into the function, you need to subset it to
look at one state at a time.  You would need to go into the csv file to see
how it is formatted and how the data is assigned to a state.  If the state names
are all in one column named "state" all you have to do is use a pipe and the
dpylr package to filter the column (you will need to install the dpylr package
if you have not already done so to do this).

```r
  look_at_state_data <- function(input_file_name,  
                                  subsetted_state){
    all_state_data <- read.csv(input_file_name)
    one_state_data <- all_state_data  %>%
      dplyr::filter(state == subsetted_state)}                                  
    }
```   
You now have a function that will go through a csv file and parse out any
state of your choosing. The only problem is you cannot see what the function
did.  As a last step in the function you should tell it to make a new csv
file that only contains the data of the state you are interested in. This new
csv file can be written to go anywhere, but for this example it will go into an
output directory with a file name based on the state you are looking at.                       
```r
  look_at_state_data <- function(input_file_name,  
                                    subsetted_state){
    all_state_data <- read.csv(input_file_name)
    one_state_data <- all_state_data  %>%
      dplyr::filter(state == subsetted_state)
    write.csv(one_state_data, path = "output/individual_state_data/subsetted_state.csv")                                    
    }
```   
It is important to make sure that all of the variables you are making in this
function are unique so that you do not break your script.  For any additional
lines of code you add you should retest your function to make sure it
still works.

# How to call for a function from another script
Once you make a function, the easy part is calling for the function from
somewhere else.  You do this through loading your function on the other script
through the built in source function.  Using source you then write out the
path to the function you have created.
`source("code/function_file_name")`

Next you would call for the function and supply what the variables are.  
`(input_file_name = your_original_csv_file)`
`(subsetted_state = state of choice)`

Overall your script will look like this:  
```r
source("code/function_file_name")

look_at_state_data(input_file_name = "path_to_csv",
                    subsetted_state = "California")
```
From this script you can choose any state for the subsetted_state variable and
get a new output csv of only the data from that state.

The above is only one example of a function that you can make in R.  However,
by using the basic template of a function, paying attention to variable names,
and keeping track of what your end goal is, you can make a function do just
about anything.
