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

## 5. HTML
![HTML](https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/HTML5_logo_and_wordmark.svg/240px-HTML5_logo_and_wordmark.svg.png)

HTML, Hypertext Markup Language, is a markup language designed for the development of web browser. You can insert and edit text, images, videos and other media via HTML. It aims to provide structured formatting so that users can clearly see what developers want to display in the webpage. Almost everything we use and see on the website is fundamentally coded in HTML. If you want to make your own website, HTML is absolutely a nice choice. Even for the complex website formatting style, HTML can still handle it.

HTML is assisted by CSS (Cascading Style Sheets) and JavaScript. If you want to learn HTML, be prepared to learn CSS and JavaScript as well.  

### HTML History
HTML was developed my a physicist Tim Berners-Lee. His purpose of developing this system was to share documents. In the late 1980, he wrote the browser and server software. The first version was published in November 1995 in order to upload file and client-side image. In the latest version HTML 5, it was published as a W3C Recommendation. [^7]

![Tim Berners](http://archive.thegovlab.org/wp-content/uploads/2014/01/Sir-Tim-Berners-Lee.png)

# Example of HTML
```
<!-- This is a comment -->
<html>
  <head>
    <title>This is a title</title>
  </head>
  <body>
    <div>
        <p>Hello world!</p>
    </div>
  </body>
</html>
```

## 6. C/C++

Both C and C++ are programming languages and they are both used for the application development. C is not so popular now but it has the longest history than many other programming languages. C is a structure-oriented, middle-level language. Many systems that are developed by C Language can be then integrated into other systems such as Linux and UNIX. Nowadays, many device drivers are still designed and coded by using C Language. C Language is considered as the "mother" of all programming languages, so if you are an  expert in working on C Language, it will be much easier to start learning other languages than those who are the beginners in programming languages. [^8]

C++ was developed based upon on C Language. C++ is more powerful and it is a high-performance language but a low-level programming language. As a low-level programming language, it is relatively complicated and it is pretty hard to learn. C++ requires tons of code in order to function properly. [^8] The main difference between C and C++ is that C is procedural programming language and C++ is a combination of procedural and object-oriented programming language. [^9]

### Keywords
- Keywords in C and C++: auto, break, char, double, float, do, else, void, while, switch, register...
- Keywords that were added into C++: bool, catch, class, false, const_cast, try, public, using, this, private...

## 7. SQL
![SQL](http://tugrul.dbsdataprojects.com/wp-content/uploads/sites/162/2017/03/Introduction-to-SQL.png)

SQL is a domain-specific language. It is used to manage data and for stream processing. It is particularly useful for dealing with structured data. SQL has multiple features in terms of data management, including data query, data manipulation, data storage and data access control. [^10]

SQL is used by many companies which they need to gather data, such as UnitedHealthCare and airline companies. In 1987, SQL was used as a standard of the International Organization for Standardization (ISO). [^10]


# Comparison Between Different Languages
| Languages | Features | Best For | Used By | Easy to Learn
| --- | --------------- | --------------- | ---------------- | ----- |
| Python | multi-paradigm, simple, high readability | machine learning, data analysis, web design | Google, Pinterest, Youtube, NASA | ⭐️⭐️⭐️⭐️⭐️|
| Java | interpreted language, extensive network library | web development | Android apps | ⭐️⭐️|
| JavaScript | flexible, new front-end frameworks | front-end website, video games | Almost every website | ⭐️⭐️⭐️⭐️ |
| Ruby | simple and flexible, completely object-oriented | web development，web applications, security | Amazon | ⭐️⭐️⭐️⭐️ |
| Bash | brace expansion, command line completion, extremely useful in all IT works | IT professions | Everyone | ⭐️⭐️⭐️⭐️|
| HTML | easy to use, multiple website formatting versions | web developers | Apple, CyberCoders | ⭐️⭐️⭐️|
| C | can be used in almost all systems | operating systems, software development| Apple, Microsoft | ⭐️|
| C++ | quick processing, widely-used in software | operating systems, video games, application and software development | Google, Firefox, Blackberry OS | ⭐️⭐️ |
| SQL | free and easily accessible, simple syntax | data processing, database management | nearly all applications | ⭐️⭐️⭐️ |


[^1]: Wikipedia - Python
[^2]: Wikipedia - Java
[^3]: What is the difference between Java and JavaScript. https://www.educative.io/edpresso/what-is-the-difference-between-java-and-javascript
[^4]: Wikipedia - Ruby
[^5]: 11 Popular Programming Languages. https://www.varonis.com/blog/programming-languages/
[^6]: Summary of Bash Features. https://www.oreilly.com/library/view/learning-the-bash/1565923472/pr01s02.html
[^7]: Wikipedia - HTML
[^8]: 14 Different Programming Languages and Their Uses. https://mikkegoes.com/14-programming-languages-explained/
[^9]: Differences between C and C++. Tutorialspoint.
[^10]: Wikipedia - SQL
