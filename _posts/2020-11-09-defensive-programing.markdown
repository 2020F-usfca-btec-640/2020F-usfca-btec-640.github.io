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

In short, defensive programming is a way to prevent bugs from happening by including progress checkpoints in your code.

2. Why is it important?  

Defensive programming is a good practice that allows the user to react to unexpected errors and fix them faster. Let’s say that you create a code that processes extensive tabular data, but you do not use defensive programming. The code works perfectly with one dataset, great! However, when you try to use the same code to process a similar tabular dataset.  
In this case, you first have to find where in the code did the error happen, and then you have to figure out why it happened. Perhaps the argument that a function is looking for does not exist in the new input file, or it exists but it is not in the correct format; any of these errors can take you two minutes to fix, but hours to find.  
Troubleshooting can take a lot of time, and it is probably part of every programmer’s worst nightmares. Now, by using defensive programming style, the guard statements and assertions can guide you in the direction of the problem, or even tell you exactly what the problem was, saving time and protecting your mental health.  

3. Examples of defensive programing  

- Give one example and cite a website with more.

4. Final thoughts  
