---
layout: post
title:  "Guide to Organizing Projects"
date:   2020-11-08 12:54:04 -0700
categories: guide projects organization folder
---
Once you have an idea of what you want to do for your projects, it's important to organize your working directory. If your project is organized well and everything is documented, anyone who's unfamiliar with your project should be able to look at your files and understand what you did and why. Organize everything the way that if you come back to that project in couple months or years you will able to understand what you did and why.

## Directory Layout
There are couple of reasons to have a certain structure for your project:
1. Achieve reproducibility with minimal effort.  
2. Optimize the time looking for the files by organizing folders based on the input and output files.  
3. Improve the quality of the project with detailed explanations and notes as the work progresses.

Basic directory layout may look like this:
* data/
  * raw/
  * clean/
* code/
  * functions/
    * 01_process-data.R
    * 02_create-figures-using-processed-data.R
  * archived/
* output/
  * data-exploration-figures/
  * final-figures/
  * descriptive-title-for-output-file-batch/

This is just a basic example and as you progress on your project your directories will evolve. Typically, files in the directory 'data/raw/' should not be changed or edited for reproducibility sake.

## File Naming
Once we have the basic structure down, let's talk about naming your files.

1. Files should be named consistently.
2. Avoid using special characters or spaces in a file names.
3. Use dashes and underscores instead of slashes, periods or spaces.
4. Use date format YYYY-MM-DD.
5. File names should be concise and descriptive.

Some other things to consider when naming files according to [Stanford's Data Management Services](https://library.stanford.edu/research/data-management-services/data-best-practices/best-practices-file-naming):
* Project or experiment name or acronym
* Location/spatial coordinates
* Researcher name/initials
* Date or date range of experiment
* Type of data
* Conditions
* Version number of file
* Three-letter file extension for application-specific files

## Version Control
As project gets more complicated and you start collaborating with other professionals, version control is something to consider. There is a software that helps you keep track of changes done by you or fellow collaborators. To learn more about that, please check out the following blog posts:
* [Introduction to GitHub]({ site.url }) by Sami
* [Basics of Git and Github]({ site.url }) by Sarah
* [How to/why write good commit messages]({ site.url }) by Jordan

Note: links will be added later to those sections on the blog.

## References
* [A Quick Guide to Organizing Computational Biology Projects by William Stafford Noble](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1000424#s8)
* [Best Practices Organizing Data Science Projects by Florencia Mangini](https://www.thinkingondata.com/how-to-organize-data-science-projects/)
* [How To Keep Your Research Projects Organized, Part 1: Folder Structure by Ties de Kok](https://towardsdatascience.com/how-to-keep-your-research-projects-organized-part-1-folder-structure-10bd56034d3a)
* [Best Practices For File Naming from Stanford Libraries](https://library.stanford.edu/research/data-management-services/data-best-practices/best-practices-file-naming)
