---
layout: post
title:  "Getting Back Into Headless Cloud Computing"
date:   2020-11-08 6:54:04 -0700
categories: bash ssh tmux vpn headless
---
## Getting Back Into Headless Cloud Computing
#### Use Case
This tutorial answers the question, "How do I log back into a remote server and analyze data without a graphical user interface, again?"

This is adapted from some notes I used when I was several months into a bioinformatics class and wanted to pick back up where I'd left off in the headless cloud environment.

Since not all setups will be identical, and having several tools setup already is a prerequisite for this workflow, see the bottom of this post for my software dependencies.

#### Login
* Open VPN app on your PC, e.g. Global Protect
 * Enter your institutional account's username and password
* Open Git Bash and initialize ssh connection
 * Provide server-specific username and password, given to you by your instructor or IT admin for cloud computing
 * e.g. `ssh Last_Name_Example@server_name.insitution.edu -p 8036 > provided-password`

#### Shorten bash prompt
 * Often, the bash prompt becomes unwieldy in length
 * Try shortening it to just user and path: `PS1=’\u:\W\$ ‘`
 * Or, just path: `PS1=’\W\$ ‘`

#### Configure git in container
* Find the right folder: `~`
* Clone `git clone https://github.com/user/repo`
* Set user `git config --global user.name “Full Name”`
* Set email `git config --global user.email “preferred@email.com”`
* Create new branch `git branch example-branch`
* Switch to new branch `git checkout example-branch`
* Add something, e.g. README `git add README.md`
* Commit `git commit -m “Initialize example branch”`
* Push `git push`
* Enter GitHub username and password
* Check `git config --list`

#### Restore git session from different machine
* Pull down branches made elsewhere `git pull`
* List branches `git branch -a`
* Switch to a branch `git checkout example-branch`

#### Manage persistent work sessions
 * List any open sessions `tmux ls`
 * Initiate new session `tmux a <session if more than one>`
 * `tmux new -s learning-tmux`
 * Split `ctrl+B, %`
 * Split `ctrl+B, ”`
 * Switch panes `ctrl+B`, `ctrl+O`

#### Build a bash script in nano
* Create empty script `touch script_name.sh`
* Open script `nano script_name.sh`
* Proceed with your analysis!
---------
#### My dependencies for this tutorial
* Institutional login: [University of San Francisco][usf]
* VPN: [Global Protect][global-protect] for Windows 10
* git version control: [GitHub][github]
* bash shell: [Git Bash][git-bash]
* Session management: [Tmux][tmux]
* Container admin: [Docker][docker]
* ssh credentials: contact your IT admin

[usf]: https://www.usfca.edu/arts-sciences/graduate-programs/biotechnology
[global-protect]: https://www.paloaltonetworks.com/products/globalprotect
[github]:[https://github.com/]
[git-bash]:[https://gitforwindows.org/]
[tmux]:[https://github.com/tmux/tmux/wiki]
[docker]:[https://www.docker.com/]
