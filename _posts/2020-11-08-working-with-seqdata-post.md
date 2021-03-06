---
layout: post
title:  "Welcome to Working with Sequence Data!"
date:   2020-11-08
categories: 1. ***Overview of FASTA/FastQ***, ***Basic of counting FASTA/FASTQ entries***, ***Trimming low-quality bases***, ***Overview of Parsing FASTA/FASTQ files***

---
![seq_image](https://i.ytimg.com/vi/fCd6B5HRaZ8/maxresdefault.jpg)

## **FASTA & FASTQ**  
*Overview of FASTA*  
- It is a text based format for representing either nucleotide sequences or peptide sequences where the base pairs or the amino acids are represented by using single-letter codes  
- Each sequence in the FASTA file represents the sequence for a chromosome
- The simplicity of the FASTA file format makes it easy to manipulate and parse the sequences to through programming languages such as R and Python  

*Overview of FASTQ*  
- A FASTQ file is a text file that contains the sequence data  
- It is a widely used format in sequence analysis which is generated directly from the sequence like Illumina, and it contains more information than FASTA  
- Each Illumina FastQ file format contains 4 pieces of information: The Sequence Identifier, Nucleotide sequence, Quality score Identifier line (a single "+" sign), and quality scores

### *FASTA*
- This format is used to store any kind of sequence data which  does not require the per-base pair quality score  
- FASTA sequence entries have two parts: ***a description and the sequence data, which is denoted by the greater than symbol***. ***The next part contains the sequence which begins on the next line after the description***
### FASTA Example
ENSMUG00000020122 | ENSMUST00000138518  
CCCTCCTACGTCAATAGCTAATCGCGCTAATCGCGATCGAAACTCGCAATCGCGCTA ATCTGCTCGATCGGCTAGCTAGCCCGGGAATCGCTAGCTGACTAGCGATCGACTCG   

### *FASTQ*  
- This sequence format is an extension on the FASTA by including the quality score for each base
- Most commonly used format to store high-throughput sequencing data
- ***The FASTQ format starts of with the description line beginning with @***
- ***Then the line after contains the sequence on many lines***
- ***The last line after the sequence contains information on the quality of the data. Each numeric base quality data is encoded utilizing the ASCII character scheme, which I will cover later***
### FASTQ Example
@DJB775P1:248:DOMDGACXX:7:1202:12362:49613
TGCTTACGTCGGTTCGATTTCCGGGAAATTCCCGTGTCCCTAACGCTTAAGCTAAATC  +  
JJJJJIIJJJJHIHHHGHFFFFFFCEEEEEDBD?DDDDDDDDBDDDABDCAFFFDDCH

### *Counting FASTA/FASTQ Entries*
Common command-line bioinformatics  
`$ grep-c "^>" egfr_flank.FASTA`  
5  
- The grep command counts the number of sequences with one line description that start with >.  

`$ wc -l untreated1_chr4.fq`  
817420 untreated1_chr4
- The wc -l command counts the total number of lines in the file

`$ bioawk -c fastx 'END{print NR}' untreated1_chr4`  
204355  
-  Bioawk is an extension of awk. Awk is a language that is able to conduct text processing and aids with data extraction. It can be adapted to extract and report specific parts of your data. Bioawk is one iteration of awk  
- In this function, utilizing -c fastx will help let bioawk know to parse input as FASTQ or FASTA
- In the file untreated1_chr4 there are four lines per sequence. Using bioawk is a robust way to parse and printout the actual number of sequences in the file.

### *Intro to Inspecting & Trimming Low-Quality Bases*
![quality_of_read](https://lh5.googleusercontent.com/_KAKU58ax51Y/TZQtBGsweyI/AAAAAAAAADA/MVEx7AStm_o/s800/per%20base%20sequence%20quality.png)
- When working with Illumina sequence bases' inaccuracies increases as you approach the 3' end of the sequence. If it goes unchecked it can be detrimental for the downstream analysis
- For this there are softwares that helps us easily visualize the quality of distributions.  
   - The most popular is the ***Java program FastQC (http://bit.ly/FastQC)***
   - If working with R you can utilize the Bioconductor package called ***qrqc (http://bit.ly/quick-qc)***  
- To install qrqc in R through the terminal
  - library(BiocInstaller)
  - biocLite(qrqc)  

**Two programs that will trim low-quality bases**
- sickle (http://github.com/najoshi/sickle)
- seqtk (http://github.com/lh3/seqtk)
- sickle & seqtk can be easily installable on Mac OS X with Homebrew  
Using the FASTQ file untreated1_chr4 as an example  

  `$ sickle se -f untreated1_chr4 -t sanger -o untreated1_chr4`  
  FastQ records kept: 202866  
  FastQ records discarded: 1489  

- Here the sickle program takes our input file through the -f command, -t is the signifies the quality type, -o generates our trimmed output  

- To make things neater, we can use **trimfq** command, which takes our argument and output in one go  

`$ seqtk trimfq untreated1_chr4 > untreated1_chr4.fq`  
- We can use ggplot to produce plots like shown below. It compares how effectively sickle vs trimfq can trim low-quality bases  
![comparing_sickle_trimfq](https://apprize.best/data/bioinformatics/bioinformatics.files/image084.jpg)  

### *FASTA/FASTQ Parsing*  
- Parsing is a method when you take one string of data and convert into a a more readable data format  
- This is done with FASTA/FASTQ files often using the parser readfq  
- Python has an implementation of it called *readfq.py* **(http://github.com/lh3/readfq)**  
- The parsing routine for readfq is **readfq import readfq**  
- Overall how readfq() works is it takes the file, and generates the FASTQ/FASTA entries. Then using readfq() it returns each FASTA/FASTQ entry containing the description of the sequence and quality of the sequence.  

***Parsing in R***  
- In R you can use the function `read.fasta(seqnir)`  
- Here you utilize the package seqinr
Example - `read.fasta(file = system.file("sequences/ct.fasta.gz" , package = "seqinr"))`
- After this line you can set parameters to obtain the data you want  
- To read FastQ files its **readFastq**, which comes from the *ShortRead* package  
- `readFastq(dirPath, pattern=character(0), ...)  "readFastq (dirPath, pattern=character(0), ..., seq file)"`  
- readFastq returns a single R object (ShortReadQ) containing sequences and qualities contained in all files in dirPath matching pattern.

***Ex of beginning of code using readfq()***  
`#!/usr/bin/env Python`  
`# nuccont.py -- tally nucleotides in a file`  
`import sys`  
`from collections import Counter`  
`from readfq import readfq`  

---
