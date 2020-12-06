---
layout: post
title:  "How to be successful with for loops"
date:   2020-11-07 12:54:04 -0700
categories: jekyll update
---
In this post you will learn about the basics of creating for loops and why they
are important as a bioinformatics tool.

# What to know beforehand
In order to utilize for loops it is best to have a working function. The main
advantage of being able to use a function is the fact that it makes your code
incredibly flexible. With a properly working function all you would need to do is
have an input and the code will work to manipulate your input data and produce a workable output. Without the function, your code will only work for a specific input and only produce a singular output.  While still useful making the code more flexible allows you to perform
the same action on multiple different potential inputs. This is an example of a basic function

```
square_this <- function(x) {
  if (!is.numeric(x)) {
    stop("ERROR: You did not use a numeric value.")
  }
  x^2
}
```
This function is designed to take a numeric input (if it is a non numeric input the function will not run) and add two to it. It then stores this function into the variable "square_this" in order to call the function for use at a later time.  

# What is a for loop?
Using a function makes your code more flexible. But say you had numerous different inputs you wanted to run. Running the function for each input one at a time can be tedious. If you had hundreds of different inputs to run inputting each and every one would be impractical. This is where for loops come in.

A for loop is a special kind of command that allows you to run the same function as many times as you wish but substituting the input file each time. This makes your code even more flexible as it allows you to run the same code many times over in a fraction of the time it would normally take to manually input each and every input file. Let us take a look at a relatively simple for loop.

# Anatomy of a for loop

Let's take a look at a basic for loop:
```
for (my_number in 1:5) {
  my_number <- square_this(my_number)
  my_number <- add_two_to_this(my_number)
  print(my_number)
}

my_number = {"1", "2", "3", "4", "5"}
```
Before doing anything else make sure your function is called into your global environment.

To start out the for loop type `for ()`. This will start out the for loop. In the parentheses place the name of the variables that you want to start in the loop and when you want to finish. In this case we want the values from 1 through 5. Each of these variables will be represented by "my_number" whenever the for loop re-runs itself.

Within the curly braces is where to put the names of the specific functions you want to run. In this case the function from before "square_this"is being called along with another function "add_two_to_this". It's anyone's guess what exactly this function does. To make life on yourself easier put a print statement at the end so it can show you the output of your operation and determine if adjustments need to be made.

To test the for loop assign your variable name to something you want to test. In the example my number is set to find 1 through 5. This test is meant to find CHARACTERS  not values. In real life you might look for a character in the data you are running such as "sample 1" or "California". It would look something like this:

```
my_state = {"California", "Florida", "Oregon", "Wyoming", "Virginia"}
```
# Where does my for loop go?
It is a pretty good practice to make your function script successful and then make the for loop in a separate file. This way instead of remaking the entire function within the brackets of your loop, you can simply source the function and it will call it from the other file. Have an output directory set up so that the outputs of the for loop have a place that can be stored and processed by other functions.

# In Conclusion
For loops are a powerful tool which is incredibly helpful when you want to run the same operation on multiple different files. In a bioinformatics pipeline it gives you the ability to run a specific function on multiple variables in sequence. Without it, you would need to run the function individually for each variable you wanted to run which, for larger datasets, is impractical. Thus, for loops are an effective tool to make your pipeline run much more smoothly. 
