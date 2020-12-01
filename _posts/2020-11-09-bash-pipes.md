---
layout: post
title:  "Bash pipes: more useful than Mario's"
date:   2020-11-09 12:54:04 -0700
categories: bash pipes
---
by Hannah Hayes

You’re a budding bioinformatician and you are learning all of these amazing commands in bash to explore and modify your data. But you want a way to combine these commands without creating an endless amount of output files to work upon. Or you are trying to modify your data in a particular way, but you can't find that one *perfect* program that would accomplish your task.

Luckily for you, Unix shell has modular workflows, allowing for programs to talk to one another, through **pipes**.

Not unlike the pipes in Super Mario, these pipes can easily transport your data from one command to another. However, unlike Mario's pipes, bash pipes are simple to master and won't send you unexpectedly to your villain's lair.

![mario pipe](https://thumbs.gfycat.com/FreeThoughtfulAmericancrayfish-poster.jpg)

### How it works   
Bash pipes are denoted with the `|` symbol, not to be confused with a lower case L or capital i.

Instead of displaying the output on the terminal screen or redirecting the output to a new file (with `>`), a bash pipe will feed the output of one command directly to the input of another. As long as your commands can understand the same type of data, then you can use this on almost any Unix program. Bash pipes allow you to combine simple commands to make them into more complex tools to analyze your data.

```bash
$ program1 inputfile.txt | program2
```
In this example, `program1` will process the data in `inputfile.txt` in some way and only the output created by  `program1` will be handed to `program2` to process in another way.  

### Pros of modular workflows
* Computational Efficiency
  * reading and writing to the disk can be very slow particularly when using large datasets such as sequence data
* Helpful in Debugging
  * because each component is independent, it is easier to find mistakes in intermediate results
* Customizable
  * easily swap and add components
* Optimizable
  * combine the best-suited programs for your specific set of tasks

### Cons
* A pipe is only as good as its weakest link
  * If one part of your pipe-line has a bug, the entire thing will not fail unless the last command in the pipe fails.
  * However, because pipes are modular, you can test each part in succession to ensure that there are no bugs.
  * If you are writing a bash script, it is important to add `set -eou pipefail` at the top of your script so that pipes error out if one component of your pipe fails.

### Tee Pipes
It may be useful to see intermediate outputs in a file format to identify bugs in the pipeline. With the `tee` program, you can divert a copy of your pipeline's output in a file while still passing it to the next step, just like a plumbers T-pipe.

```bash
$ program1 inputfile.txt | tee intermediate-file.txt | program2 > results.txt
```

### Common examples
Adding `| head` or `| tail` to the end of your pipeline can be used to show only the first or last 10 lines of your output, respectively. This can be particularly useful when you are checking an intermediate step working with a large dataset, such as sequence data, and printing the entire output to the terminal screen can take a lot of time and space. If you want to print more or less than 10 lines of the output you can use `| head -n 20`, replacing with the desired number of lines.

`| wc -c`, `| wc -l`, `| wc -m` will give you the word, line, or character count of your output, respectively.

`| sort` will sort lines from your output. Use `| sort -n` for numeric sorting and `| sort -r` to reverse the order. The `sort` program automatically organizes data from least to greatest for numerical values. `| sort -u` will sort and return unique values of your output.

`| uniq` will compare adjacent lines of your output and writes a copy of each unique line. `| uniq -c` will add the count of how many times a line was repeated. *Note*: if you want to see how many times something was repeated in your entire file, you will need to sort it first, which is an excellent use of a pipe! `sort file.txt | uniq -c`

`| cut -f 1,4` will retrieve data from selected columns from a tab-delimited file, in this case columns 1 and 4. For data that is not tab-delimited, use `| cut -d \, -f 1,4` to indicate the delimiter, in this case it would be comma-delimited.  

Now, let's put some of these examples together. Imagine you have a comma separated dataset with 5 columns and many many rows, some of which repeated. Let's say that you would like to a tally of the unique values are in the first column. You would like an output table with the tallied values sorted from greatest to least; you could use:  
```bash
cut -d \, -f 1 inputfile.csv | sort | uniq -c | sort -rn
```
The first  `cut -d \, -f 1` separates the first column of the comma delimited data set `inputfile.csv` and hands it to the `sort` program. The `sort` program then sorts the values only from the first column from least to greatest and hands the sorted list to the `uniq` program. The `uniq -c` program then identifies and tallies repeated values in adjacent lines. The final `sort -rn` program takes the unsorted table of unique values and the number of occurrences of each and sorts it by the number of occurrences from greatest to least.

The modular nature of bash pipes can help you easily perform any number of processing steps on your data!  

### References
Buffalo, V. (2015). *Bioinformatics data skills: Reproducible and robust research with open source tools*. O'Reilly Media, Inc.
