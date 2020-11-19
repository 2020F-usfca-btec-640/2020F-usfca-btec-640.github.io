---
layout: post
title:  "Introduction to GitHub!"
date:   2020-11-09 12:54:04 -0700
categories: GitHub Introduction Basics
---
# Introduction to GithHub
**by Sami Darrow**

![GitHub Logo](https://upload.wikimedia.org/wikipedia/commons/thumb/9/95/Font_Awesome_5_brands_github.svg/124px-Font_Awesome_5_brands_github.svg.png)

Hello! In this blog post I will be going through a brief introduction to GitHub. I’ll be touching on what GitHub is, what it’s used for, and how useful it can be to anyone that codes! Hopefully if you are reading this you find it helpful!

## What is GitHub
GitHub is a that is used by software developers that allows for ***collaboration*** on projects and also provides a platform for ***version control***. Below I briefly describe why the ability to collaborate and version control are important. Further on in the post I will go into more detail about each aspect.
  * **Collaboration:** You can push projects that you are working on from your computer to GitHub. This allows other that you are working with to see what you have done to the code for your project.
  * **Version Control:** Having a way to keep track of what edits you made to your code and when can be very useful if and when your code breaks. As long as you have a recent commit on GitHub, you can go back and recover your working code.

#### A Short History Lesson
GitHub was founded by Chris Wanstrath, P.J. Hyett, Tom Preston-Werner, and Scott Chacon in February 2007. Within the first three years of the site being available for public use, over 1 million repositories had been added to the site.

The main purpose behind GitHub was to provide a place for collaboration, version control, and a graphical interface that allowed software developers to visualize what they were doing this Git. Git itself is a version control software and is what GitHub was built around.

## The Importance of the Ability to Collaborate

![collaborate](https://glip.com/content/dam/glip/us/en/images/pages/use_cases/development/development-content.svg)

When working on a project, especially if you are working in a team, sharing the work you have done with each other is important. GitHub allows software developers to share their code and each person who is working on the project can do their own work without messing up the other persons progress.

Say there are two people working on a project: Person 1 is the main coder who develops the base line code for everyone to work off of. Person 2 is a contributor that can also work on the code and provide feedback and maybe make some slight changes to what Person 1 has done. The basic workflow that would go into this two-person project would be as follows:
  * **Person 1:** Creates working code for what the project calls for and pushes this code to GitHub
  * **Person 2:** Fork the code onto their GitHub account and copy the code onto their machine. Make changes to the code. Push code to their GitHub. Open a pull request from the original code.
  * **Person 1:** Look at Person 2’s pull request. If the code is good, approve the pull request and merge the changes into the main project

This is just the very basics of what two people can do when working collaboratively through GitHub *(there is a lot of jargon in there that I will cover in the Version Control section of this post)*. But the key takeaway is that GitHub allows people to work collaboratively in a way that allows people to do their own work and not mess with each other’s progress.

## The Importance of Version Control

![version control]({{ site.url }}/assets/version_control.png)

It is very important that you keep track of what you’ve done and what works when writing code. Version control goes hand-in-hand with collaborative coding. As previously mentioned, GitHub is great for collaborative projects because of its version control ability. If Person 2 were to work directly on the code that Person 1 was developing, that would break the code and ruin the whole project.

GitHub allows for version control in several ways, some of which are detailed below. For continuity’s sake, I will be referencing the two-person project I detailed in the previous section:
  * **The ability to fork a repository:** Person 2 can go to person 1’s GitHub profile and find the repository that has their project in it. They can then fork this repository to their GitHub account.
    * This basically means that they copy the project to their GitHub account so they can use it as their own and not mess with what Person 1 is doing.
    * Additionally, you have the ability to create new branches in a project. This acts as an effective form of version control as well. A new branch essentially a copy of the original code but it will not effect any of the code on the main branch.
      * Some command when working with branches are as follows:
        * Creating a new branch: `git checkout -b <name-of-new-branch>`
        * Switching to an existing branch: `git checkout <name-of-existing-branch>`
        * Preview all existing branches: `git branch`


  * **Pushing Code to GitHub:** if you are working on the command line this can be done through the command ‘git push’ followed by the name of the file that you would like to push to GitHub. This allows Person 2 to take whatever they were working on and put it onto GitHub for Person 1 to see.
    * This step is not inherently about version control, but it is an important step that needs to be taken to maintain project continuity.

      *Note that when a new version gets added to GitHub, in order for the other person to get that new version they have to pull that info from GitHub. To do this the command `git pull` can be used.*


  * **Creating a pull request:** Person 2 can create a pull request that will notify Person 1 that they made some changes to the existing code. When looking at the work Person 2 submitted, Person 1 can decide whether it will be helpful or whether it will harm the existing code.
    * If they determine that it would harm the existing code, they would not merge it to the main repository. This is where version control is important because without it, the whole project could have been messed up.
    * Typically, Person 2 would have created their own branch with their own work. If Person 1 deems the code to be helpful they can merge that branch with the main code.
      * Once a branch is merged it can either be kept or deleted. If more changes are intended to be made to this branch it should **not** be deleted. If all the code is approved by Person 1 and no changes are intended to be made to the branch then the branch can be deleted

Speaking outside of the scope of team projects, GitHub can be used as version control for personal projects as well. You can push commit and push things to git as you work on your code to ensure that you have a copy of your project somewhere other than your own machine. If you wanted to compare GitHub’s version control capacity to something it would be like writing a final essay for a class and having it both on your computer and also on your Google Drive account.

## Main Takeaway
GitHub is a great tool that allows people to work collaboratively and offers a great interface for version control. Without GitHub, both of these things would be possible, but it would be much more difficult to achieve them in the seamless way that GitHub allows.

#### I hope that this blog post explained GitHub well and hopefully now you know what GitHub is and why it is so helpful!
