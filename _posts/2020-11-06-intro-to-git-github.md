---
layout: post
title:  "An Intro to Git and Github"
date:   2020-11-06 10:13:04 -0700
categories: git github version control
---
# An Intro to Git and Github

Hi there! This post is intended to serve as a brief beginner's introduction to the concept of Git and a sampling of some of the most commonly used workflows for this nifty tool. Here we go!

***

### What is Git and Github?

Git is essentially a free and open source version control system. After installing it on your machine, you can capture versions of your project throughout the process. This way, if anything goes awry or even if you want to experiment around, you'll always have (if you exercise best practices of course) a well-documented timeline of all these previous states.

Github is a separately managed platform that essentially hosts your Git repositories remotely. This provides a relatively stable backup of any local repositories you may have that you can pull down from any other machine. It also enables programmers to work openly with others for easier collaboration.

***

### How do I use Git?

To get started with Git, you'll first need to download it [here](https://git-scm.com/downloads). Instead of repeating it here, there are several helpful tutorials online such as [this one from Atlassian](https://www.atlassian.com/git/tutorials/install-git) that offer comprehensive walkthroughs on how to install Git onto your machine.

#### Creating a repository

Once you have Git installed, you'll need to create your first repository. In a Terminal window, using the command line, navigate to the directory that you want to enable version control for. Once you initiate this, Git will track any changes that may occur with any of the files within that directory. Use the following command to make your current directory into a Git repository:  

`git init`

This creates a `.git` subdirectory within that working directory that allows Git to track your changes.

#### Tracking files

While Git can track the files within your directory, you will still need to manually tell Git which file changes should be saved. To do so, you'll need to enter the following command:

`git add FILE.txt`

Here, you replace `FILE.txt` with whatever file you want to track. This `git add` functionality tells Git that you care about this file and want any changes you make in it to be tracked. Next, you'll need to actually save these changes by using the following:

`git commit -m "Add commit message here"`

While `git add` adds individual files to be tracked, `git commit` is basically telling Git to save the current status of all your added files. This can include

You can also use the `git status` command to see a snapshot of which files have changes
