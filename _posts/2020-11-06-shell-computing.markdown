---
layout: post
title:  "Shell Computing"
date:   2020-10-19 12:54:04 -0700
categories: jekyll update
---
**What is a shell?**

When you think of a shell what may first come to mind is the outer covering of an animal such as a crab or a turtle. However, leaving the animal world and entering into the computer world there is also a shell.

In the case of computer science, a shell is the tool a user can utilize in order to interact with the components of a computer. A shell is essentially a software program that is able to interpret commands from the user so the operating system can understand them and perform the various functions (Tech terms, 2020). It got the name shell because it is the outermost layer around the operating system. Shells can run on local systems but there is a way to make remote systems available as well making it possible to access remote servers. For example, our server at University of San Francisco, does not have a graphical interface so in this case we need to use the command line to access it in order to do our projects.   

**Command-line vs graphical interface**
So, we now know that shell is this command line interpreter which can really be broken down into two categories: command line interface or a graphical user interface. Command-line shells, require the user to be familiar with commands and their calling syntax and understanding the concepts about shell specific scripting languages.

A graphical user interface means that you can manipulate programs graphically. Graphical interfaces and shells are characterized as being easy to use. You can do things such as opening, closing windows in a desktop environment. Some people often think of graphical interfaces as an “electronic desktop” meaning it is where data files are represented as if they were paper documents on a desk

**Why are shells useful?**

Shells are useful for a multitude of reasons. Below are a few of the many shells allow you to automate repetitive tasks, making your work less error prone. They also make your work more reproducible because when you use the command line, your computer is able to keep a record of every step you have carried out. Shells become very useful in the bioinformatics field because many of these tools can only be used through command line interface.

**How to access shell**

On a Mac or Linux machine you can access shell through the terminal which is already on your computer. However, if you are on a windows machine, you will need to download a separate program to access shell.

**Examples of command line shells**
There are various shells that one can use such as C shell (csh), Kornshell (ksh), tcsh, and Bash (sh). Each one has its differences and advantages and disadvantages. Shells are like brands. Everyone has a favorite and will religiously defend that choice. Below is a table comparing various command line shells and some of the features they have in comparison to one another.



**Highlighting Bash**
The most commonly used shell tends to be bash, known as the bourne again shell. Bash is so popularly used because it is easy to use for beginners. Bash has great features such as tab completes commands. This makes it so you do not have to type out everything everytimes. It has the history saved and if you give it the first few letters you can tab and it will auto complete it. This is a huge time saver and also helps cute down on errors you could make while typing.





links

(https://en.wikipedia.org/wiki/Shell_(computing)).
https://www.edureka.co/blog/types-of-shells-in-linux/



















You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

Jekyll requires blog post files to be named according to the following format:

`YEAR-MONTH-DAY-title.MARKUP`

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

```ruby
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
```

If you want to add an image, you will need to add it to the assets/ directory, and then use the following special syntax where you want to include the image.

Note that the curly braces and site URL part needs to stay as is, the part you change is the image name and the alternative text between the square brackets.

```
![useful image alternative text]({% raw %}{{ site.url }}{% endraw %}/assets/the-name-of-your-image.png)
```

Here's an example:

![fastq screenshot]({{ site.url }}/assets/fastq-screenshot.jpg)

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
