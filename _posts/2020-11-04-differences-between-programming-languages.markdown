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

# Introduction of Common Programming Languages
## 1. Python
![python](https://beat0154.github.io/Python-Programming-Portfolio/python.png)

Python is a high-level programming language. It supports a variety of programming paradigms such as functional programming, object-oriented programming and procedural programming. Python is highly extensible, which serves as a feature of adding programmable interfaces to many applications.

Python is an easily understandable and readable language. If you are new to the programming language, Python would be a nice choice. Unlike other languages, it uses whitespace indentation to delimit blocks.[^1]

### Python History
Python was designed by *Guido van Rossum* in the late 1980s. Python *2.0* was released on October 2000 with the new feature of containing a cycle-detecting garbage collector. Python *3.0* was released on December 2000. New version will be released on May 2022.[^1]
![Python](https://www.cwi.nl/news/blogs/interview-guido-van-rossum-201cid-rather-write-code-than-papers.201d/@@images/58e10972-b372-4cec-9e1f-a265cf227e78.jpeg)

### Python programming examples
```
counter = 1
while counter < 5:
  print("The current counter value: " % counter)
  counter = counter + 1
```
Some common statements and controls: `if`,  `for`,  `while`, `raise`, `break`, `continue`, `return`, `print`, `import` ...

## 2. Java/JavaScript
![Java/Javascript](https://www.educative.io/api/edpresso/shot/6424035982311424/image/5707702298738688)

### - Java
Java is an object-oriented and high-level programming language; and it can run on all platforms and all sorts of hardwares. A data collected on Github shows that Java has been the top popular programming language in web design and web applications. [^2] Java is particularly common in web-based development, as well as the development in video games and mobile applications.

Java's primary principle is:
> write once, run anywhere (WORA)

### - JavaScript
JavaScript is high-level and multi-paradigm. It is a client-side programming language, written for the web browser. Unlike Java which objects are class-based, JavaScript objects are prototype-based. [^3] The main difference between Java and JavaScript is the design idea, where JavaScript is more user-friendly and interactive.

## 3. Ruby
![Ruby](https://i.pinimg.com/564x/eb/9e/3b/eb9e3b7dab09358e7cf13f188f64f9f4.jpg)

Ruby is similar to Python. It is a high-level, general-purpose programming language. Ruby uses garbage collection and it supports multiple paradigms, including functional programming and object-oriented programming. Ruby was released its first version Ruby 1.0 in December, 1996; and now it is on the Ruby 3.0. [^4] Ruby is commonly used in 3D modeling and it is a useful tool to manage and track information.

Ruby is a part of the Ruby on Rails web framework. Ruby uses primary on its website-building framework Ruby on Rails.

### History of Ruby
Ruby was designed by Yukihiro Matsumoto in Japan. He wrote his early idea of developing Ruby in his post:

>I was talking with my colleague about the possibility of an object-oriented scripting language. I knew Perl (Perl4, not Perl5), but I didn't like it really, because it had the smell of a toy language (it still has). The object-oriented language seemed very promising. I knew Python then. But I didn't like it, because I didn't think it was a true object-oriented language – OO features appeared to be add-on to the language. As a language maniac and OO fan for 15 years, I really wanted a genuine object-oriented, easy-to-use scripting language. I looked for but couldn't find one. So I decided to make it.

## 4. Bash
![Bash](https://www.fullstackpython.com/img/logos/bash-wide.jpg)

Bash is a scripting language. It is a a command processor and it is a Unix shell. Bash can run in a text editor window where user types commands and runs to make actions. Bash can also execute commands from a shell script file.

Bash was originally released in 1989 written by Brian Fox. The language was designed primarily as a free software replacement for the Bourne shell. [^5]

Bash contains a variety of features, including wildcard matching, piping, control structures, command history and brace expansion, etc. It has both features from the C shell's major advantages and its own features. [^6]

### Bash Script Example
```
#!/bin/bash
n=0
if [ $n -eq 0 ];
then
echo "It is number 0"
else
echo "It is not number 0"
fi
```
Run the file in the bash command line:
```
$ bash if_example.sh
```

Some common bash commands: `ls`, `echo`, `touch`,`mkdir`,`pwd`, `grep`, `cd`, `mv`,  `|`- Pipe, `head`, `clean`...
# Comparison Between Different Languages
| Languages | Features | Best For | Used By | Easy to Learn
| --- | --------------- | --------------- | ---------------- | ----- |
| Python | multi-paradigm, simple, high readability | machine learning, data analysis, web design | Google, Pinterest, Youtube, NASA | ⭐️⭐️⭐️⭐️⭐️
| Java | interpreted language, extensive network library | web development | Android apps | ⭐️⭐️
| JavaScript | flexible, new front-end frameworks | front-end website, video games | almost every website | ⭐️⭐️⭐️⭐️ |
| Ruby | simple and flexible, completely object-oriented | web development，web applications, security | Amazon | ⭐️⭐️⭐️⭐️|
| Bash | brace expansion, command line completion, extremely useful in all IT works | IT professions | Everyone | ⭐️⭐️⭐️⭐️ |
| HTML |  |  |  | ⭐️⭐️⭐️ |
| C |  |  |  | ⭐️⭐️ |
| C++ |  |  |  | ⭐️⭐️ |
| SQL |  |  |  | ⭐️⭐️⭐️ |


[^1]: Wikipedia - Python
[^2]: Wikipedia - Java
[^3]: What is the difference between Java and JavaScript. https://www.educative.io/edpresso/what-is-the-difference-between-java-and-javascript
[^4]: Wikipedia - Ruby
[^5]: 11 Popular Programming Languages. https://www.varonis.com/blog/programming-languages/
[^6]: Summary of bash Features. https://www.oreilly.com/library/view/learning-the-bash/1565923472/pr01s02.html
