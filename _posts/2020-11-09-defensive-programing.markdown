---
layout: post
title:  "Defensive programming - what it is and why it is important"
date:   2020-11-09 12:54:04 -0700
categories: defensive programming
---
Title:  Defensive programming - what it is and why it is important  
Author: Gabrielly Lunkes

Often times, a piece of code is used by different people, not only the person who created it. Also, codes can frequently be used to process different types of data. In my opinion, this flexibility to use the same code to process different datasets is one of the greatest things about coding. However, how is it possible to write a code in a way that other programmers would be able to navigate through and even use it with different types of input without spending endless hours trying to figure out how things work? Yes, you guessed it, the answer is in defensive programming.

1. What is defensive programming?  

In short, defensive programming is a way to make sure that your code works even when given incorrect output. This can be done by adding guard statements and assertions in your code that check if certain requirements are met and return a statement. The statements are usually helpful sentences that identify which requirement was not met and can even tell you what you should do to fix it. Here is an example:

‘’’’’’’
if (nrow(input_data) == 0) {
  stop("ERROR: Input data is empty. Did you make a typo?")
‘’’’’’’’’

In this case, the code is checking if the input file actually has data in it. If the file is empty, it will show the message “ERROR: Input data is empty. Did you make a typo?”. Notice that the statement points out what went wrong and gives an idea of how to solve the problem.

2. Some methods of defensive programming

•	Assertions

Assertions are statements that check if a condition is true or false. If it is, the program does nothing. If the condition is false, the program will print an error message.
Example:

numbers = [1.5, 2.3, 0.7, -0.001, 4.4]
total = 0.0
for n in numbers:
    assert n >= 0.0, 'Data should only contain positive values'
    total += n
print 'total is:', total

In this piece of code, the for loop will work only with positive numbers. When it encounters a negative number, it will stop the loop and print the error message “Data should only contain positive values”

•	Pre-conditions

Pre-conditions are statements that make sure certain conditions are true before it runs the code. If the conditions are not met, the code doesn’t run, and an error message can be displayed explaining what happened.

public void CreateAppointment(DateTime dateTime)
{
    if (dateTime.Date < DateTime.Now.AddDays(1).Date)
        throw new ArgumentException("Date is too early");

    if (dateTime.Date > DateTime.Now.AddMonths(1).Date)
        throw new ArgumentException("Date is too late");

    /* Create an appointment */
}

Here, the code will only make the appointment if the the given date is correct, not too early or too late.

•	Nulls

Null is a pointer used in programming for uninitialized, undefined, empty, or meaningless value. Because many programs cannot discriminate null values, they are often the reason for bugs in codes. Therefore, checking your code for nulls when applicable is always a good idea.

Example:

public class Controller
{
    public Controller(ILogger logger, IEmailGateway gateway)
    {
        if (logger == null)
            throw new ArgumentNullException();
        if (gateway == null)
            throw new ArgumentNullException();

        /* ... */
    }

    public void Process(User user, Order order)
    {
        if (user == null)
            throw new ArgumentNullException();

        /* ... */
    }
}

	In this case, the code is checking for null values.

3. Why is defensive programming important?

Defensive programming is a good practice that allows the user to react to unexpected errors and fix them faster. Let’s say that you create a code that processes extensive tabular data, but you do not use defensive programming. The code works perfectly with one dataset, great! However, when you try to use the same code to process a similar tabular dataset.  
In this case, you first have to find where in the code did the error happen, and then you have to figure out why it happened. Perhaps the argument that a function is looking for does not exist in the new input file, or it exists but it is not in the correct format; any of these errors can take you two minutes to fix, but hours to find.  
Troubleshooting can take a lot of time, and it is probably part of every programmer’s worst nightmares. Now, by using defensive programming style, the guard statements and assertions can guide you in the direction of the problem, or even tell you exactly what the problem was, saving time and protecting your mental health.  

4. Final thoughts  

"Defensive programming is good programming". This phrase caught my attention the first time I heard it, and now I think it might be one of the most important things I have learned about programming. When writing a code that will later be used with different input data or by someone else, it is important to think about how you can make things easier for the user. Defensive programming helps programmers write codes that are prepared to deal with any unexpected circumstances, and even provide guidance on how to solve the issue. It helps to create self-checking codes that can be widely used, and that is a beautiful thing.

I hope you enjoyed this post. Here are some sources with more interesting information about defensive programming and some more examples of defensive programming methods:



5. References
