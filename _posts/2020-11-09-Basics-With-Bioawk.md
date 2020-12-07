---
layout: post
title:  "Basics with Bioawk!"
date:   2020-11-09 4:45:00 -0800
categories: Bioawk
---

# Basics with ~~Babish~~ Bioawk!
by Sahil Verma

## Taking the Awk out of Bioawk

Awk is a Unix/Linux coding language that allows coders to extract and manipulate data and generate reports based on the data. While it is a full fledged scripting language, it isn't as powerful as other languages, such as Python. Awk allows people to do data-processing tasks on tabular data. Awk does this by working on _records_ and _fields_. Since Awk works on tabular data, Awk views _records_ as rows and _fields_ as the columns for each record. In Awk, the entire record is stored to `$0`, the field's first value is assigned to `$1`, the second value is assigned to `$2`, and the pattern continues.

Awk programs are, generally, built using the following recipe:

`pattern {action}`

The _pattern_ is an expression or regular expression pattern, allowing people to filter for matched expressions, so that those only those patterns are acted upon. These _pattern-actions_ can be linked together into a chain by semicolons. By combining these two different concepts, _records_ and _fields_ with _pattern-actions_, Awk is able to survey a file line by line and split those lines into fields, compare those lines and fields to a pattern, and perform actions on those patters to manipulate data and generate reports.

Some common Awk functions are to filter reports and fields using RegEx, splitting strings (s) into tabular "chunks" with a specificed delimiter (d) and placing them into an array (x) via `split (s, x, d)`, `print` the content of the tabular data, changing the case of strings in a field via `tolower(s)` or `toupper(s)`

Now that we've lightly sautéed the awk, so to speak, let's add the "bio" back to "Bioawk."

## Bioawk: Making Biological Formats More Awk Since 2015

Like Awk, Bioawk processes data, but extends Awk's "flavor compounds" to common biological file formats, particularly FASTA/FASTQ, GTF/GFF, BED, SAM, and VCF file types. The beauty of Bioawk is that it will automatically set the variables for each field to particular parts of the bioinformatics files. Some examples of this are as follows:
```
bed:

    1:chrome 2:start 3:end 4:name 5:score 6:strand 7:thickstart 8:thickend
    9:rgb 10:blockcount 11:blocksizes 12:blockstarts`

gff:

    1:seqname 2:source 3:feature 4:start 5:end 6:score 7:filter 8:strand
    9:group 10:attribute

fastx:
    1:name 2:seq 3:qual 4:comment
```
Bioawk code ~tastes~ is built similarly to Awk, but by using bioawk's built in tools, we can specify the filetype we are using with the following syntax, using FASTX as an example: `bioawk -c fastx`

We will continue to use FASTA/FASTQ files as an example moving forward. As mentioned above, Bioawk has built in tooling to scan a file and "chunk" parts of the sequence file into their appropriate fields, the name of the sequence (`$name`), the sequence itself `($seq)`, comments about the sequence such as what the gene does, what chromosome it is on, etc. (`$comment`), and finally FASTQ files have an additional field for quality data about the sequence (`qual`). If we wanted to print the comments of all the sequences in a FASTA file, we could write the following:

`$ bioawk -c fasta '{print $comment}' example.fasta`

We can use Bioawk's built-in Awk functions to further split the comments into tabular data and print them with the following recipe:

`$ bioawk -c fasta '{split($comment,a,"&#124;"); print a}' example.fasta | head -n 10`

The above splits the comment of the sequences into tabular chunks, using "|" as the delimiter to separate chunks, and places them into an array, "a" and then print the first 10 rows of data using `head`.

Bioawk also has some built in functionality that bioinformaticians in particular will love so much, they'll come back for seconds! One of these functions is to reverse compliment a sequence using `revcomp()`.

`$ bioawk -c fastx '{print revcomp($seq)}' example.fasta | head -n 10`

These are but a few of the ways you can introduce the Bioawk cuisine to your daily ~meals~ workflow.

## Final Tasting Notes

Sometimes you head to your ~kitchen~ desk and you see a lot of things in your ~fridge~ code that are not appealing, consider ~ordering takeout~ googling stack overflow, and go back to the ~fridge~ code knowing very well that nothing has changed. But sometimes you _do_ check stack overflow and you realize there's a comment detailing Bioawk. Do yourself a favor and, consider adding Bioawk to your workflow. As soon as you start picking up the basics of Awk, you'll find yourself generating bioinformatics reports with ease using Bioawk!
