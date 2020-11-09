---
layout: post
title:  "Welcome to Working with Sequence Data!"
date:   2020-11-08
categories:
---
## **FASTA & FASTQ**

### *FASTA*
- This format is used to store any kind of sequence data which  does not require the per-base pair quality score  
- FASTA sequence entries have two parts: ***a description and the sequence data, which is denoted by the greater than symbol***. ***The next part contains the sequence which begins on the next line after the description***
### FASTA Ex
> ENSMUG00000020122 | ENSMUST00000138518  
CCCTCCTACGTCAATAGCTAATCGCGCTAATCGCGATCGAAACTCGCAATCGCGCTA ATCTGCTCGATCGGCTAGCTAGCCCGGGAATCGCTAGCTGACTAGCGATCGACTCG   

### *FASTQ*  
- This sequence format is an extension on the FASTA by including the quality score for each base
- Most commonly used format to store high-throughput sequencing data
- ***The FASTQ format starts of with the description line beginning with @***
- ***Then the line after contains the sequence on many lines***
- ***The last line after the sequence contains information on the quality of the data. Each numeric base quality data is encoded utilizing the ASCII character scheme, which I will cover later***
### FASTQ Ex
> @DJB775P1:248:DOMDGACXX:7:1202:12362:49613
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

`$ bioawk -cfastx 'END{print NR}' untreated1_chr4`  
204355  
- In the file untreated1_chr4 there are four lines per sequence. Using bioawk is a robust way to parse and printout the actual number of sequences in the file.
