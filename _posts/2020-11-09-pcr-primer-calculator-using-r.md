---
layout: post
title:  "Designing Primers using R"
date:   2020-11-09 12:54:04 -0700
categories: PCR primer melting temperature
---
Hello and welcome to my blog post about creating your own PCR primer melting temperature calculator using R! You might be asking your self, what is a PCR Primer? Why do I need to know the melting temperature of my PCR primer? Perhaps, you are here simply because you were assigned to read this blog post to determine the quality of its content based on some kind of grading scale. Nevertheless, all your questions and more will be answered here! So, without further ado, lets get into it.

## What is a PCR Primer?
A primer is a highly sophisticated tool that allows a scientist to conduct several laboratory experiments. This versatile tool is comprised of a single-stranded chain of nucleotides, typically ranging from 15 to 30 bases long. Scientists add additional bases to the single-stranded molecule to customize it for their specific polymerase chain reaction (PCR) experiment. For example, a fluorescent molecule can be attached to a PCR primer for use in RT-PCR experiments. While the application of these primers are numerous, we will be focusing on primers designed for PCR cloning.

What is PCR cloning, you ask? For our purposes, the application of PCR cloning is out of scope for this blog post. The important part here is to note that there will be additional sequences attached to the five prime side of a given PCR primer. This information is pertinent because the additional bases **WILL NOT** be include when calculating the melting temperature of our PCR primer. More on that once we begin coding.

## The Game Plan
Like all good scientists and coders, we must first plan out how we want to develop this calculator before we start coding in R. Spending quality time to plan out and design the code will save us time and effort in the future. When planning out a script or a simple block of code, I like to use *pseudocode*. Below you can see our pseudocode. As we venture into each section of the code, I will give more explanation to each step of our pseudocode and explain what that will look like in R.

**Overview**  
1. Adding libraries to the R script
2. Import the PCR primer data  
  - Use readr to access the primer data from a csv files  
  - Defensive coding: check the file for primer data   
    - If no primers are found in csv file, abort the script  
3. Loop: Calculate the melting temperature of each primer  
  - loop through each row of the csv file until we have processed all rows with sequence data
    - ensure the primer name (in column A) does not have any spaces in the name. If so, replace it with a "_"
    - capitalized all letters in the primer sequence (in column E) using stringr
    - lowercase all letters in the restriction site sequences (in column D) using stringr
    - capitalize all letters in the leading strand sequence using stringr
    - store the complete PCR primer (leading strand, restriction site, and primer sequence) together to a variable
    - store the complete PCR primer with "5'" and "3'" wrapped around the sequence to another variable
    - count the number of A's, T's, G's, C's, etc. in the annealing portion of the sequence to individual variables using stringr
    - if the sequence has ambiguous bases:
      - [Yes] calculate the minimum and maximum melting temperature
      - [No] calculate the melting temperature
    - create variables to hold the gc-percentage and annealing primer length
    - create a data frame using the variables we created
4. Export the results of the calculator to a folder as a new csv file
  - use readr to write the data frame to a csv file.
    - save the file using the row number and primer name
  - close the For Loop

Lets take a look at the expected input file for our script.  
![input file layout]({{ site.url }}/assets/pcr-primer-calculator-using-r-input-file.jpg)

For each row with sequencing information, we want to process and output the results of PCR primer.  
![output folder layout]({{ site.url }}/assets/pcr-primer-calculator-using-r-output-folder.jpg)

Make a note about each column. Reference the column inside the code, so that we can denote each code block and what field that code relates to.  
![output file results]({{ site.url }}/assets/pcr-primer-calculator-using-r-output-file-results.jpg)

Each output file will contain the entire PCR primer sequence (leading strand, restriction site and primer sequence), a count of each nucleotide of the *annealing* portion of the primer sequence, and the melting temperature of the primer sequence. Furthermore, we need to add in a minimum and maximum melting temperature section to the output file. I will explain why we need a minimum and maximum once we begin coding the nucleotide count code.

-------------------------------------------------------------------------------
## Creating our script in R
#### Section 1: Adding libraries to the R script  

Libraries were created to make coding easier for everyone. A library inside code is synonymous to a literal library. They are full of *books*. Each book you request from the library helps you accomplish a task. Imagine yourself as a computer, your human overlord demands that you take the integral of an infinite series that is both continuous and decreasing in a positive manner and needs to know if the function converges or diverges. What are you going to do? You will go to the library and request a Calculus textbook by Ron Larson. Once you have the book, you can tell your master the area under the curve of the infinite series is finite and will converge.

For our script we will be using two libraries, readr and stringr.
```r
# load in the packages to help simplify our code
library("readr")
library("stringr")
```

#### Section 2: Import the PCR primer data

**Overview**  
2. **Import the PCR primer data**  
  - Use readr to access the primer data from a csv files  
  - Defensive coding: check the file for primer data   
    - If no primers are found in csv file, abort the script  

The readr library handles all the necessary coding for *streaming* in the input file into our script. Now we can interacting with our primer data!
```r
input_file <- "path/to/pcr_primer_input_file.csv"
primer_information <- readr::read_csv(input_file)
# the primer data has been stored in variable primer_information
# we will use this variable to access various parts of the data.
```

First we need to add a defensive coding block into our script to prevent empty input files from being processed. If we do not check for empty input files, then we might come across coding issues later on in the script. How do we prevent this? Lets count the number of rows in primer_information that have sequencing data and stop the function if there is less than 1 row.
```r
num_of_rows_in_data <- nrow(primer_information[, 1])
# we will save this number to a variable becuase we will need it again within
# our For Loop statment

# defensive coding block
if (num_of_rows_in_data <= 1) {
  stop("ERROR: No sequence data found in the csv file")
}
```

#### Section 3: Use a loop to calculate the melting temperature of each primers
**Overview**  
3. **Loop: Calculate the melting temperature of each primer**
  - loop through each row of the csv file until we have processed all rows with sequence data
    - ensure the primer name (in column A) does not have any spaces in the name. If so, replace it with a "_"
    - capitalized all letters in the primer sequence (in column E) using stringr
    - lowercase all letters in the restriction site sequences (in column D) using stringr
    - capitalize all letters in the leading strand sequence using stringr
    - store the complete PCR primer (leading strand, restriction site, and primer sequence) together to a variable
    - store the complete PCR primer with "5'" and "3'" wrapped around the sequence to another variable
    - count the number of A's, T's, G's, C's, etc. in the annealing portion of the sequence to individual variables using stringr
    - if the sequence does not has ambiguous bases:
      - [Yes] calculate the melting temperature
      - [No] calculate the minimum and maximum melting temperature
  - create variables to hold the gc-percentage and annealing primer length
  - create a data frame using the variables we created


The bulk of our script will be wrapped around a For Loop. The code is written this way because we need to process each line of sequence data at a time. Furthermore, we want to generate an output file for each sequences data we processed. The attributes of a For Loop fits perfectly for what we want to do.

Once we are in the loop, we want to remove any spaces within the primer name and replace them with "_". Additionally we can format the sequences how we would like and then piece together the entire PCR primer
```r
# the For Loop will start on row 1. Once the For Loop cycles back to the top
# of the loop, data on row 2 will be used and so forth
# the For Loop ends once row_num excessed the value of num_of_rows_in_data
for (row_num in 1:num_of_rows_in_data) {

  # replace " " with "_" in the primer name
  primer_name <- gsub(primer_information[row_num, 1],
                      pattern = " ",
                      replacement = "_")

  # capitalize and/or lowercase the sequences using stringr.
  # for appearance we want to make sure the sequence look uniform
  # the restriction site sequences will be lowercase. This will help
  # scientists to distinguish the leading strand and annealing sequence from
  # the restriction site sequence.
  annealing_seq <- stringr::str_to_upper(primer_information[row_num, 5])
  restric_site <- stringr::str_to_lower(primer_information[row_num, 4])
  lead_strand <- stringr::str_to_upper(primer_information[row_num, 3])

  # combine the sequences together using paste0
  whole_pcr_sequence <- paste0(lead_strand,
                               restric_site,
                               annealing_seq)

  # in the output file we want to have 5' and 3' noted with the sequence.
  # for ease, we will create a second variable to store this sequence
  pcr_sequence <- paste0("5; ",
                         whole_pcr_sequence,
                         " 3'")
```

For the next block of code we will begin counting up each nucleotide within the annealing sequence and storing the individual counts of each base. We must account for all plausible bases within the sequence. Not only will we counting the typical A's, T's, C's, and G's, but we need to count up all the ambiguous bases too.

![Ambiguous base chart]({{ site.url }}/assets/pcr-primer-calculator-using-r-ambiguous-chart.jpg)
[Source](https://www.dnabaser.com/articles/IUPAC%20ambiguity%20codes.html)

```r
  # get a count of each nucleotide within the sequence
  g_cnt <- stringr::str_count(annealing_seq, "G")
  c_cnt <- stringr::str_count(annealing_seq, "C")
  t_cnt <- stringr::str_count(annealing_seq, "T")
  a_cnt <- stringr::str_count(annealing_seq, "A")

  # get a count of each ambiguous base within the sequence
  y_cnt <- stringr::str_count(annealing_seq, "Y")
  r_cnt <- stringr::str_count(annealing_seq, "R")
  w_cnt <- stringr::str_count(annealing_seq, "W")
  s_cnt <- stringr::str_count(annealing_seq, "S")
  k_cnt <- stringr::str_count(annealing_seq, "K")
  m_cnt <- stringr::str_count(annealing_seq, "M")
  d_cnt <- stringr::str_count(annealing_seq, "D")
  v_cnt <- stringr::str_count(annealing_seq, "V")
  h_cnt <- stringr::str_count(annealing_seq, "H")
  b_cnt <- stringr::str_count(annealing_seq, "B")
  n_cnt <- stringr::str_count(annealing_seq, "N")
```

Now that we have a count of each possible base for a given annealing primer sequence, we can calculate the melting temperature of each primer. Below is the equation for finding the melting temperature of a given sequence. As you can see, the melting point is decided by the amount of A-T bases and G-C bases. But how do ambiguous bases fit into the equation? This is a tricky question to answer because ambiguous bases can become other bases during PCR (refer to the *Ambiguous base chart* for each ambiguous base to see which nucleotide that base could become). We will need to calculate two melting temperatures; a minimum and maximum temperature for sequences with ambiguous bases. To calculate the minimum temperature, we will count the ambiguous bases that could potentially become an A or T base as an A or T nucleotide. The ambiguous bases that can **only** become a G or C will be counted as a G or C nucleotide. For calculating the maximum temperature, we will flip the ambiguous assumption, in which ambiguous bases that could potential become a G or C base will be counted as a G or C nucleotide. And ambiguous bases that can **only** become an A or T base will be counted as an A or T nucleotide. To make this concept easier to conceptualize, I have include the pseudocode before the code block.

> Melting Temp = 2 * (A + T) + 4 * (G + C)  

**Pseudocode for calculating melting temperature**  
if there are no ambiguous bases in the sequence,
 - then calculate the melting temperature of the sequence

else (there are ambiguous bases in the sequence)
 - calculate the min & max melting temperature of the sequence

```r
  # get a count of the ambiguous bases
  ambiguous_cnt <- y_cnt + r_cnt + w_cnt + s_cnt + k_cnt +
    m_cnt + d_cnt + v_cnt + h_cnt + b_cnt + n_cnt

  if (ambiguous_cnt ==  0) {
    melting_temp <- (2 * (a_cnt + t_cnt)) + (4 * (g_cnt + c_cnt))

    # min_melting_temp & max_melting_temp should be NA-ed because there
    # are no ambiguous bases for this sequence.
    min_melting_temp <- ""
    max_melting_temp <- ""

  } else {
    # calculate the minimum melting temperature
    # refer to the ambiguous base chart to determine which ambiguous bases
    # can become A's, T's, C's, or G's.
    # store the count to variable for ease/human readable code.
    max_at_cnt <- a_cnt + t_cnt + y_cnt + r_cnt + w_cnt + k_cnt + m_cnt +
      d_cnt + v_cnt + h_cnt + b_cnt + n_cnt

    min_gc_cnt <- c_cnt + g_cnt + s_cnt

    # calculate the minimum melting temperature
    min_melting_temp <- (2 * max_at_cnt) + (4 * min_gc_cnt)

    # calculate the maximum melting temperature by finding the max count of
    # G and C bases in the sequence.
    max_gc_cnt <- c_cnt + g_cnt + y_cnt + r_cnt + s_cnt + k_cnt + m_cnt +
      d_cnt + v_cnt + h_cnt + b_cnt + n_cnt

    min_at_cnt <- a_cnt + t_cnt + w_cnt

    # calculate the max melting temperature
    max_melting_temp <- (2 * min_at_cnt) + (4 * max_gc_cnt)

    # melting_temp should be NA-ed because we are using the min & max
    # melting temperatures for this sequence
    melting_temp <- ""
  }
```
Voila! We have created the code to calculate the melting temperature of our PCR primers! Before we wrap this project there are a couple more things we need to think about before finishing. We should include the G-C content percent in our code. The G-C percentage in a sequence is import for scientists to know. Like the melting temperature, G-C content can change the properties of the primer. Furthermore, we can add more data points that we think will be useful for scientists to know about their PCR primer, like the length of the annealing sequences.

```r
  # save the length of the annealing sequences to a variable
  annealing_seq_length <- stringr::str_length(annealing_seq)

  # lets calculate the G-C content percentage
  gc_percent <- ((g_cnt + c_cnt)/annealing_seq_length)

  # I want to use the row_num in the output file name. I want row numbers
  # less than 10 to have a zero before the row number.
  if (row_num < 10) {
    print_num <- paste0("0", row_num)
  } else {
    print_num <- row_num
  }
```

#### Section 4: Exporting our results to a new csv file
**Overview**
4. **Export the results of the calculator to a folder as a new csv file**
  - use readr to write the data frame to a csv file.
    - save the file using the row number and primer name
  - close the For Loop

Lastly, we need to create a data frame to store our individual variables in. Once the variables are linked together in a data frame, we can save the information to a csv file. If you created more variables and want to have them saved to the output file, make sure you include the variable name in the data frame.
```r
  # create and fill the data frame with our calculations/saved variables
  seq_output <- data.frame(primer_name,
                          pcr_primer,
                          g_cnt, c_cnt,
                          t_cnt, a_cnt,
                          y_cnt, r_cnt,
                          w_cnt, s_cnt,
                          k_cnt, m_cnt,
                          d_cnt, v_cnt,
                          h_cnt, b_cnt,
                          n_cnt,
                          gc_percent,
                          annealing_seq_length,
                          melting_temp,
                          min_melting_temp,
                          max_melting_temp)

  # save the data frame to a csv file using the row number and primer name
  # as the filename.
  # similarly to streaming in data, readr allows us to stream out our data
  # frame to an output folder of your choosing.
  readr::write_csv(seq_output,
                  path = paste0("path/to/output/",
                                print_num,
                                "_",
                                primer_name,
                                "_processed.csv"))
# end of For Loop
}
```
Congratulations! You have completed our PCR primer melting temperature calculator!

#### Conclusion
Thank you for following along in this blog post. I hope you have learned something new about primer design and R code. If you would like to continue working on this project, I have written a couple of questions addressing areas of this script that could be more robust.

**Coding Challenges**
- Defensive Coding
  - What if someone adds an incorrect base to their sequence (For Example: "X")? Explore the stringr library for potential solutions to this issue. [stringr documentation link](https://www.rdocumentation.org/packages/stringr)
  - **Extra Challenging:** Our script assumes all sequences are 5' to 3'. Add a new column to the input file named "5' (Y/N)". This column is meant for the user to say "Yes" to indicate the sequence is 5' to 3'. A "No" answer indicates the sequence is 3' to 5'. *If* the answer in that column is "No" *then* reverse the sequence from 3'-to-5' to 5'-to-3' at the start of the r script. The stringr document will help you manipulate the sequence.

- PCR Primer Design
  - For many PCR primers the ideal melting temperature is ~ 60 C. To better help scientists design PCR primers, tell them to add more bases (*if* the temperature is below 60) or remove some bases (*if* the temperature is above 60). Only tell them to add or subtract bases if the sequence **does not** have ambiguous bases.
  - The annealing sequence of a PCR primer should range somewhere between 15 to 30 nucleotides long. Use the variable annealing_seq_length to determine if the annealing sequence is too short or long. Add variable "seq_length_check" to the data frame. This variable should store "too_short" if the sequence is too short, "too_long" if the sequences is too long, or "" (blank) if the sequence length falls between 14 and 31 bases.
  - **Extra, Extra Challenging:** Often times PCR primers have a Forward strand and a Reverse stand. The two PCR primers are used together during a PCR experiment. This means both annealing primers need to have similar melting temperatures. First, check each primer has a Forward and Reverse sequence (assume the primer name of each forward and reverse sequence are identical, and that each primer are next to each out; i.e. primer 1 forward is in row 1 and primer 1 reverse is in row 2, and so on). Once you have set this up in the script, calculate both annealing strands and check if the melting points of both strands are similar temperatures (+/- 2 degrees). Indicate if the sequences have accepted melting temperatures or not in the output file. Do not compare minimum or maximum melting temperatures. Skip the comparison for sequences with ambiguous bases.
