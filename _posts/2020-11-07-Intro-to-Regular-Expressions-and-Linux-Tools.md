---
layout: post
title:  "Intro to Regular Expressions & Linux Tools: grep, sed, and awk"
date:   2020-11-07 12:54:04 -0700
categories: regular expressions grep sed awk
---
Written by: Katelyn Spilman

Hello! The purpose of this blog post is to provide beginning bioinformaticians with a high level introduction to the concept of regular expressions and how they can be used with the Linux command line tools `grep`, `awk`, and `sed` to search for (and even modify) text in files.

# What are Regular Expressions?
A regular expression is a way to describe complex patterns within text. Regular expressions are made up of building blocks of literal and special characters that allow you to parse text and match complex patterns.[^1]

Any literal character (alphabetical or numeric) will match that specific character. Literal characters are case sensitive, such that capitalized letters are not the same as lower case letters. Literal characters also include spaces, which will match a literal space. You can also use positional special characters `^` and `$` which mark the beginning or end of a line, respectively. In regular expressions, the "wildcard" character `.` stands for any single character. You can also specify how many times a character occurs in a regular expression using quantifiers `*` and `+`.[^2]

Below is a list of commonly used regular expression patterns. *(We'll see examples of how these patterns are used later on in this post.)*



**Commonly Used Patterns:**
- **.** : matches any single character
- **[A-Z]** : matches any capitalized letter
- **[a-z]** : matches any lower case letter
- **^** : matches the expression at the beginning of a line
- **$** : matches the expression at the end of a line
- **\*** : quantifier that matches the preceding character zero or more times
- **+** : matches the preceding character one or more time
- **[ ]** : matches any one set of characters
- **{n}** : matches the preceding characters *n* times

Take a look at this example showing a regular expression matching an e-mail address.

![regular expression example](https://ucarecdn.com/7b465367-f8ba-4033-972c-e373d278fdd2/)

While regular expressions are incredibly useful, it is true they can get pretty complicated as is shown in the above example, and can thus be tricky to learn.

![regular expressions meme](https://i.redd.it/fozqgb59a9p21.png)

A useful tool when beginning to work with regular expressions is [Regex 101][regex101]. It is an online interactive tester that allows you to write regular expressions and test them using sample text. (In fact, I used this tool when creating the examples found later in this post!)

[regex101]: https://regex101.com/

There are many tools that use regular expressions as part of their functionality, including the three Linux command line tools `grep`, `sed`, and `awk`.


# **grep**
## The Basics
`grep` is a command line tool that allows you to search for patterns within files. Aptly named, `grep` stands for **G**lobal **R**egular **E**xpression **P**rint. [^3]
`grep` will find and print lines in a file that match a pattern (a specific string of characters or regular expression). One notable feature of `grep` is that it is *really fast* because it works by streaming a file's data instead of adding file data to memory all at once.

So how do you use `grep`?


## Syntax
The basic structure of a `grep` command is shown below:

```bash
$ grep [options] "pattern" input-file
```
The first argument is the pattern we're searching for and the second is the input file we wish to search in.

There are also a number of different options that can be used to enable other capabilities of `grep`. For instance, you can find context about the matching line using the `-Bn` option, which prints *n* lines before the matching line, and the `-An` option, which prints *n* line after the matching line.

## Examples
As a simple example, let's say we want to search for some text within an example text file: `sample.txt`.

To view the contents of the `sample.txt` file, we can use the `cat` command:

```bash
$ cat sample.txt
cat
bat
apple
dog
first
Eat
blue
catnap
Green
```
If we want to find all instances within `sample.txt`
that exactly match the word "dog", we can use the following `grep` command:

``` bash
$ grep "cat" sample.txt
cat
catnap
```
Using regular expressions with `grep`, we can find more complex patterns that do not match exactly. The following command allows us to find all words that begin with any capitalized letter followed by any number of characters:

```bash
$ grep "^[A-Z].*" sample.txt
Eat
Green
```
In this case, this outputs two matches, "Eat" and "Green".

The `-c` option will print a count of all the lines matching a pattern in the input file.

```bash
$ grep -c "^[A-Z].*" sample.txt
2
```

More information about `grep` can be found in the [complete manual][grep manual], which can also be accessed from the terminal using the `info grep` command.

[grep manual]: https://www.gnu.org/software/grep/manual/


# **sed**
## The Basics
``sed`` is a command line **s**tream **ed**itor, similar to **grep** in that it finds matching text within a file. Additionally, **sed** allows you to replace the matches with something else.[^4] *(For the purposes of this post, we will focus on the use of the `sed` substitution command. Other commands can be found in the [complete manual][sed manual].)*

[sed manual]: https://www.gnu.org/software/sed/manual/sed.html#Invoking-sed


## Syntax
The basic structure of a `sed` command is shown below:
```bash
$ sed 's/pattern/replacement' input-file
```
Within single quotes, the command, followed by the pattern to be matched, and finally by what the match is to be replaced with are each separated by the `/` delimiter. This syntax is also shown in the picture below. The final argument is the input file to be searched. Note that the `s` indicates the substitution command.

![sed example](https://www.applegazette.com/wp-content/uploads/2017/11/what-is-sed-components.png)

### Examples

To see how `sed` works, let's return to the previous example using the `sample.txt` file. The following command will replace all occurrences of "cat" to "dog" in the `sample.txt` file:

```bash
$ sed 's/cat/dog/' sample.txt
dog
bat
apple
dog
first
Eat
blue
dognap
Green
# note the replacement of "cat" in the first and second to last lines with "dog"
```
The `-E` flag enables use of regular expression commands with `sed`.

Using regular expressions with `sed`, we can find matches to the pattern that begins with any number of lower case letters and ends with the letter 't'. We can capture different parts of this regular expression using `()`. The first captured variable `\1` is the beginning of the line that is any number of lower case letters. The second captured variable `\2` is the literal 't' at the end of the line. We can then switch the two captured variables as shown below.

```bash
$ grep "^[a-z]*t$" sample.txt
cat
bat
first
# here we use grep to show what the regular expression matches

$ sed -E 's/^([a-z]*)(t)$/\2\1/' sample.txt
tca
tba
apple
dog
tfirs
Eat
blue
catnap
Green
# notice that the regular expression is case sensitive so 'Eat' and `Green` were not modified
```
In this example, only the words that matched the regular expression ("cat", "bat", and "first") were replaced with the switched version of the word.

It is important to note when using `sed` we are not changing what is inside of the input file. In order to save the output of the `sed` command, you can redirect it from standard output (which goes to the screen) to a file, in which case the output will not be printed on the screen. The following command will save the output as shown in the previous example into a new output file:

```bash
$ sed -E 's/^([a-z]*)(t)$/\2\1/' sample.txt > output.txt
```
This is also true of `awk`.

# **awk**

## The Basics
Like `grep` and `sed`, `awk` can be used to find specific patterns within a file. Unlike `grep` and `sed`, `awk` finds lines within a file containing that specific pattern and can then perform actions on those matched lines once they are found. `awk` was designed to work with tabular data in plain text files.[^5]

## Syntax
```bash
$ awk 'selection_criteria{action }' input-file
```
The selection criteria which precedes the curly braces indicates the pattern you want to find within the input file. Within the curly braces is the action you want to perform on the lines containing that specified pattern.

### Example
In this example we'll look at a tabular plain-text file that contains data about chromosomes.

```bash
$ cat awk_data.txt
chr1    11    8
chr2    8     3
chr3    15    12
chr4    23    8
```
In the first column, the different chromosomes are listed. The second column indicates the number of SNPs found in each chromosome while the third column indicates the number of genes found on each chromosome.

We can use the following command to first find lines where the value in the third column (`$3`) is greater than 5, and then calculate the sum of these values. In other words, we can calculate the sum of the genes found on all chromosomes that have more than 5 genes. We use the syntax `BEGIN{}`to set a counter variable `s` equal to zero before `awk` streams through the file.

```bash
$ awk 'BEGIN{ s = 0}; $3 > 5 {s += $3}; END{ print s};' awk_data.txt
28
```

In this case, chromosomes 1, 3 and 4 have more than 5 genes. `awk` uses basic arithmetic to calculate the total sum of genes on these three chromosomes. We can double check that this answer is correct.

8 + 12 + 8 = 28


 For more information about `awk`, including how `awk` uses regular expressions, you can refer to the [Gawk: Effective AWK Programming][awk guide] guide.

 [awk guide]: http://www.gnu.org/software/gawk/manual

# Summary
`grep`, `sed`, and `awk` are very useful command line tools that every bioinformatician should be familiar with. All three tools can make use of regular expressions to describe complex patterns and any of them can be directly piped into other Linux commands, which make them all the more powerful!

To remember what each command line tool does, it may be helpful to consider the relationship between the three. In simplified terms,
- `grep`: used to find matching patterns within a file
- `sed`: used to find and replace matching patterns within a file
- `awk`: used to find matching patterns within a file and work with the matches

![but wait there's more](https://memegenerator.net/img/instances/57561191.jpg)

There are *a lot* more options, functionalities and complexities of `grep`, `sed`, and `awk` which were not covered in this post. If you want to learn more about these or about regular expressions, check out the links below!

# References
[^1]: https://gnosis.cx/publish/programming/regular_expressions.html
[^2]: https://www-users.york.ac.uk/~mijp1/teaching/2nd_year_Comp_Lab/guides/grep_awk_sed.pdf
[^3]: https://www.webservertalk.com/grep-regex
[^4]: https://www.applegazette.com/mac/what-is-sed-and-how-does-it-work/
[^5]: https://www.geeksforgeeks.org/awk-command-unixlinux-examples/
