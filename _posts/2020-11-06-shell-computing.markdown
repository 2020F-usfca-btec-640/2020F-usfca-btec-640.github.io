---
layout: post
title:  "Introduction to Shell Computing"
date:   2020-11-08 12:54:04 -0700
categories: shell computing
---
**What is a shell?**
When you think of a shell what may first come to mind is the outer covering of an animal such as a crab or a turtle. However, when you leave the animal world and enter into the computer world there is another kind of shell.

In the case of computer science, a shell is the tool a user can utilize in order to interact with the components of a computer. A shell is essentially a software program that is able to interpret commands from the user so the operating system can understand them and perform the various functions. It got the name shell because it is the outermost layer around the operating system. Shells can run on local systems but there is a way to make remote systems available as well making it possible to access remote servers. For example, our server at University of San Francisco, does not have a graphical interface so in this case we need to use the command line to access it in order to do our projects.   

**Command-line interface vs graphical user interface**
So, we now know that shell is this command line interpreter which can really be broken down into two categories: command line interface or a graphical user interface. Command-line shells, require the user to be familiar with commands and their calling syntax and understanding the concepts about shell specific scripting languages.

A graphical user interface means that you can manipulate programs graphically. Graphical interfaces are characterized as being easy to use. You can do things such as open and close windows in a desktop environment. Some people often think of graphical interfaces as an electronic desktop because it is where data files are represented as if they were paper documents on a desk.

**Why are command-line shells useful?**
Shells are useful for a multitude of reasons. Shells allow you to automate repetitive tasks, making your work less prone to errors. They also make your work more reproducible because when you use the command line, your computer is able to keep a record of every step you have carried out. Because of this, you can easily press the up arrow and go through previous commands you have ran. Shells become especially useful in the bioinformatics field because many of these tools can only be used through command line interface so it is a necessary skill to know.

**How to access shell**
On a Mac or Linux machine you can access shell through the terminal which is already on your computer. However, if you are on a windows machine, you will need to download a separate program to access shell.

**Examples of command line shells**
There are various shells that one can use such as C shell (csh), Kornshell (ksh), tcsh, and Bash (sh). Each one has its differences and advantages and disadvantages. Shells are like brands. Everyone has a favorite and will religiously defend that choice. Below is a table comparing various command line shells and some of the features they have in comparison to one another.

![shell comparison]({{ site.url }}/assets/shell_functions.png)

**Highlighting Bash**
The most commonly used shell tends to be the bourne again shell (bash). Bash tends to be popularly used because it is easy to use for beginners. Bash has great features such as tab completed commands. This makes it so you do not have to type out everything all the time. It has the history saved and if you give it the first few letters you can tab and it will auto complete it. This is a huge time saver and also helps cut down on errors you can make while typing. It is important to remember that every shell has slightly different syntax. Below is a list of commonly used commands in bash with a short description of what those commands do.

![general shell commands]({{ site.url }}/assets/file_commands.png)
![head and tail usage]({{ site.url }}/assets/head_tail.png)
![removal]({{ site.url }}/assets/remove.png)


**Sources**
1) https://en.wikipedia.org/wiki/Shell_(computing)
2) https://www.edureka.co/blog/types-of-shells-in-linux/
3) https://techterms.com/definition/shell
4) https://subscription.packtpub.com/book/networking_and_servers/9781785286216/1/ch01lvl1sec08/comparison-of-shells
5) https://www.quora.com/Why-is-Bash-still-so-popular#:~:text=Because%20it%20is%20easy%20to,like%20it's%20constantly%20being%20improvised
6) https://www.edureka.co/blog/types-of-shells-in-linux/
7) https://datacarpentry.org/shell-genomics/01-introduction/index.html
