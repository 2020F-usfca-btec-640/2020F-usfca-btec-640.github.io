---
layout: post
title:  "Differences between Programming Languages"
date:   2020-11-04 12:50:28
categories: jekyll update
---
This page introduces all programming languages and compares the different programming languages in terms of the coding style, language principles, related applications, advantages and disadvantages, as well as how the language is executed. The purpose of making this page is to let you be familiar with all these programming languages and help you choose the one you mostly want to learn and use.

# List of Common Programming Languages
- Python
- Java/JavaScript
- Ruby
- Bash
- HTML
- C/C++
- SQL


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
