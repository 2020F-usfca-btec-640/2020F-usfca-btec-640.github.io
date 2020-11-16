---
layout: post
title:  "Beginner's Guide to Citing Open-Source Code in Rmarkdown"
date:   2020-11-09 17:45:35 EST
categories: rmarkdown bibtex .rmd .bib
---
# Why You Should Cite Open-Source Code
As a collaborative programmer at any experience level, it's important to use open-source tools that make your job easier.
Any script you write can fully utilize code that's been made available by experienced programmers.
An impressive library of useful code exists in the public domain, ready to be applied to the most mundane class assignment and the largest corporate research project alike.
These are tools anyone can use without fees or licenses in good faith that they will advance science and help us achieve our goals quicker and easier.
**Because of our respect for the providers of these tools, it's important to give them credit.**
You're *absolutely* aware at this point in your academic career that writing an original paper requires you to properly cite any words that aren't your own.
You're *probably* aware that multiple citation formats exist and each has an appropriate place in writing.
The same goes for lines of code that aren't your own!
While you won't be sued for using open-source tools without giving credit to their authors, **failure to do so is generally seen as bad practice in the community and may result in a negative reaction to your published code.**

Fortunately, there's a super easy tool for citing references in your markdown files that uses a plain text format with the .bib file extension!
Here we'll look at the components of a typical BibTeX file followed by some helpful tips for calling your references in Rmarkdown.
Finally I'll show you where you can find the information to populate your BibTeX entries.

I was introduced to this technique by my bioinformatics professor at the University of San Francisco, but I see myself using it in many projects in the future and I hope you will as well.

## BibTeX
BibTeX is a language that defines author information within a bibliography file when you write citations into your Rmarkdown file.
A bibliography file is a plain-text document with the .bib extension that utilizes BibTeX format for reference entries.
Defining the bibliography file in your Rmarkdown header and properly calling references in paragraphs instructs Rmarkdown to search for the .bib file. The BibTeX format lets Rmarkdown pull author information from your bibliography to populate your citations.
Here's some useful information paraphrased from bibtex.org:

There are four kinds of BibTeX entries, each beginning with the @ character:
* **@STRING** lets you define useful abbreviations to shorten your entries without re-typing long names and titles. This also helps maintain the 60 character limit:

  `@string { zjh = "Mr. Zachary John Houston" }`

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;which you can use in other BibTeX tags. Use the # symbol to combine strings:

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;`author = zjh # " and Dr. Naupaka Zimmerman"`

* **@PREAMBLE** defines the formatting of special text, though you *may* never use this type of entry.

* **@COMMENT** is used for descriptive text that BibTeX won't take into account.

* Actual **@ENTRIES** represent individual references. There are standards that Bib-TeX recognizes: @article, @book, @inproceedings etc.

Each BibTeX entry will have a type, a key, and several **Tags** that contain the citation information for the entry.
Here's a BibTeX entry for the `dplyr` package from one of my projects on GitHub:

`@Manual{dplyr,`\
&ensp;&ensp; `title = {dplyr: A Grammar of Data Manipulation},`\
&ensp;&ensp; `author = {Hadley Wickham and Romain François and Lionel {`\
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; `Henry} and Kirill Müller},`\
&ensp;&ensp; `year = {2020},`\
&ensp;&ensp; `note = {R package version 1.0.2},`\
&ensp;&ensp; `url = {https://CRAN.R-project.org/package=dplyr},`\
`}`

Here, the type is **@Manual**, with key **dplyr**. The title, authors, year, version, and url are all **Tags**.
Note that **Tag names** are not case sensitive.
You may also notice the **author Tag** goes over the 60 character line limit, so a concatenation is used.
It would be helpful for you to utilize a series of **@Strings** to abbreviate the names like so:

`@string { hw = "Hadley Wickham" }`\
`@string { rf = " and Romain Francois" }`\
`@string { lh = " and Lionel Henry" }`\
`@string { km = " and Kirill Muller" }`

That way the **author Tag** can look something like this:

`author = {hw # rf # lh # km}`

## Calling Your References
The **key** in the above example and all of your BibTeX entries is the signal to Rmarkdown to search your .bib file for the information to populate your reference in a paragraph.
The format for that call is `[@tag]`.
You can place the citation call in a paragraph of text easily using square brackets:

"This post was made possible by the information made available on bibtex.org [@bibtex]. Thanks guys!"

It's important to include your reference file in the header of your Rmarkdown file.
This allows Rmarkdown to search your repository for the .bib file and search it for your references.
The format is `bibliography: filename.bib` and should go in your **YAML header** adjacent to your title, name and parameters. Here's a typical YAML header for a simple Rmarkdown file:

`---`\
`title: "Analysis of COVID-era Apple Mobility Data"`\
`author: "Zachary Houston"`\
`date: "11/02/2020"`\
`output: html_document`\
`bibliography: references.bib`\
`params:`\
&ensp;&ensp; `state: "California"`\
&ensp;&ensp; `data: "data/raw_data/applemobilitytrends-2020-09-24.csv"`\
&ensp;&ensp; `seqdata: "output/sequence_summary.txt"`\
`---`

Notice that the entire header is contained by `---` above and below. This defines the header for Rmarkdown.

## Where Do I Find Author Information for Code?
Depending on what you're citing, it may be as simple as performing a search for the name of the tool or package.
Likely, you will find a GitHub repository with everything you'll need.
Many popular R packages have their own websites and/or entries on the CRAN website cran.r-project.org.
Here's an example for the `readr` package:

* GitHub: https://github.com/tidyverse/readr
* Package Website: https://readr.tidyverse.org/
* Cran Website: https://cran.r-project.org/web/packages/readr/index.html

The internet is your best friend in this situation.
However, you can also find information on packages directly in RStudio by using the `?` function on the **R Console**:

`?readr`

This will open the **Help** tab for the package.
All of these pages are helpful for citation information, but they also contain all of the **functions, arguments, and options** for the package you search.
Being able to quickly search for open-source tools will help you fully utilize them in your own coding projects.

### Thanks for reading and best of luck in your Rmarkdown writing!
For more information on BibTeX formatting, check out their website http://www.bibtex.org/.
You'll find helpful information to supplement this quick guide and links to other references and tools.
