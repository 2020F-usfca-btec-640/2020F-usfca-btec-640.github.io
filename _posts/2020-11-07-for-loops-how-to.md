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
have an input and the code will work to manipulate your input data and produce a workable output. Without the function, your code will only work for a specific input and only produce a singular output.  

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
