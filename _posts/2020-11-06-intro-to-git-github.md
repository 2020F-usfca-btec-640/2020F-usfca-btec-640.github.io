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

While `git add` adds individual files to be tracked, `git commit` is basically telling Git to save the current status of all your added files. You have to add each individual file whose state you want to save, but you can commit a whole batch of file changes. Think of it as choosing which changes you want to save, adding those individually to a bucket, and then committing the entire bucket as one version or snapshot which you can refer to later.

Commit messages are intended to help you and any collaborators you might be working with better understanding what was packaged in this commit. You want to be as succinct and informative as possible. Commit messages are composed of a subject line and a optional body text.

**Some hallmarks of a good commit message:**
* Use active voice
  * E.g. "Fix spelling errors" is better than "Spelling errors fixed"
* Use the imperative mood
  * This is the same tense as when you're giving a command
  * Follows Git's default commit style
  * If written correctly, it should seamlessly fit into the template: "If applied, your commit message will *your commit message*"
  * E.g. "Add README.md" is better than "Added README.md"
* Keep the subject line to <50 characters
* Capitalize the subject online
* Wrap the body text, if used, at 72 characters for easier legibility

*For more tips on writing good commit messages, check out [Chris Beams' great post here](https://chris.beams.io/posts/git-commit/#imperative)

#### Checking Git status

You can also use the `git status` command to see a summary of which files are untracked, which have changes, and which have already been added and are ready to be committed. This will also let you know which branch you're on which I'll go more into detail below.

#### Managing Git branches

Git allows you to create different branches of your project. This is helpful if you want to, for example, retain a working copy of your code while you create a separate branch to try out something else. Branching is a neat way to keep efforts compartmentalized and allows you to chunk out your work if need be. For example, you might have your `main` branch that you retain while you work on a separate `bug-fix` branch. You can always merge branches back together to add those updates to your main branch. I won't go into too much detail here as that's another whole post in and of itself, but Git has some [helpful documentation here](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging) that explains this feature pretty well.

***

### How do I use Github?

As I mentioned before, Github is a platform that allows users to create a remote repository of their projects. To get started, [here's a great guide from Github](https://guides.github.com/activities/hello-world/) on how to get set up.

#### Understanding the Github workflow
