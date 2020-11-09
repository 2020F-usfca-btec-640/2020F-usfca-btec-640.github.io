---
layout: post
title:  "Defensive programming - what it is and why it is important"
date:   2020-11-09 12:54:04 -0700
categories: defensive programming
---
Title:  Defensive programming - what it is and why it is important  
Author: Gabrielly Lunkes

Often times, a piece of code is used by different people, not only the person who created it. Also, codes can frequently be used to process different types of data. In my opinion, this flexibility to use the same code to process different datasets is one of the greatest things about coding. However, how is it possible to write a code in a way that other programmers would be able navigate through, and even use it with different types of input without spending endless hours trying to figure out how things work? Yes, you guessed it, the answer is in defensive programming.

1. What is defensive programming?  

In short, defensive programming is a way to prevent bugs from happening by including progress checkpoints in your code. This can be done by adding guard statements and assertions in your code that check if certain requirements are met and return a statement. The statements are usually helpful sentences that identify which requirement was not met and can even tell you what you should do to fix it. Here is an example:

‘’’’’’’
if (nrow(input_data) == 0) {
  stop("ERROR: Input data is empty. Did you make a typo?")
‘’’’’’’’’

In this case, the code is checking if the input file actually has data in it. If the file is empty, it will show the message “ERROR: Input data is empty. Did you make a typo?”. Notice that the statement points out what went wrong and gives an idea of how to solve the problem.

2. Some methods of defensive programming



3. Why is it important?  

Defensive programming is a good practice that allows the user to react to unexpected errors and fix them faster. Let’s say that you create a code that processes extensive tabular data, but you do not use defensive programming. The code works perfectly with one dataset, great! However, when you try to use the same code to process a similar tabular dataset.  
In this case, you first have to find where in the code did the error happen, and then you have to figure out why it happened. Perhaps the argument that a function is looking for does not exist in the new input file, or it exists but it is not in the correct format; any of these errors can take you two minutes to fix, but hours to find.  
Troubleshooting can take a lot of time, and it is probably part of every programmer’s worst nightmares. Now, by using defensive programming style, the guard statements and assertions can guide you in the direction of the problem, or even tell you exactly what the problem was, saving time and protecting your mental health.  

4. Final thoughts  

- Give one example and cite a website with more.

5. References
