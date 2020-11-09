---
layout: post
title:  "Beginner's Guide to Citing Open-Source Code in Rmarkdown"
date:   2020-11-07 21:18:00 EST
categories: jekyll update
---
As a collaborative programmer at any experience level, it's important to use open-source tools that make your job easier.
Any script you write can fully utilize code that's been made available by experienced programmers.
An impressive library of useful code exists in the public domain, ready to be applied to the most mundane class assignment and the largest corporate research project alike.
These are tools made available to use without fees or licenses in good faith that they will advance science and help us achieve our goals quicker and easier.
Because of our respect for the providers of these tools, it's important to give them credit.
You're absolutely aware at this point in your academic career that writing an original paper requires you to properly cite any words that aren't your own.
You're probably aware that multiple citation formats exist and each has an appropriate place in writing.
The same goes for lines of code that aren't your own!
While you won't be sued for using open-source tools without giving credit to their authors, it's generally seen as bad practice in the community and may result in a negative reaction to your published code.
Fortunately, there's a super easy tool for citing references in your markdown files that uses a plain text format with the .bib file extension!
Here we'll look at a typical BibTex file followed by some helpful tips for calling your references in Rmarkdown. Finally I'll show you where you can find the information to populate your BibTex entries.
I was introduced to this technique by my bioinformatics professor at the University of San Francisco, but I see myself using it in many projects in the future and I hope you do as well.
""  


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
