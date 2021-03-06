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

Since not all setups will be identical, and having several tools setup already is a prerequisite for this workflow, see the bottom of this post for my dependencies.

#### Login
* Open VPN app on your PC, e.g. Global Protect
 * Enter your institutional account's username and password
* Open Git Bash and initialize SSH connection
 * Provide server-specific username and password, given to you by your instructor or IT admin for cloud computing
 * e.g. `ssh Last_Name_Example@server_name.insitution.edu -p port_number`; enter provided password

#### Shorten bash prompt
 * Often, the bash prompt becomes unwieldy in length
 * Try shortening it to just user and path: `PS1='\u:\W\$ '`
 * Or, just path: `PS1='\W\$ '`

#### Configure git in container
* Find the right folder: `~`
* Clone `git clone https://github.com/user/repo`
* Set user `git config --global user.name “Full Name”`
* Set email `git config --global user.email “preferred@email.com”`
* Create new branch `git branch example-branch`
* Switch to new branch `git checkout example-branch`
* Add something, e.g. README `git add README.md`
* Commit `git commit -m “Initialize example branch”`
* Uncommit `git reset --soft HEAD~1`
* Push `git push`
* Enter GitHub username and password
* Check `git config --list`

#### Restore git session from different machine
* Pull down changes made on the same branch `git pull`
* Pull down changes made on branch `master` on the remote `origin` and integrate them into your local HEAD branch: `git pull origin master`
* List branches `git branch -a`
* Switch to a branch `git checkout example-branch`

#### Manage persistent work sessions
Tmux is essential in bioinformatics, where genome sequence files can be massive and take hours or days to process. Tmux creates a resilient work session that persists and will process your data continuously, even if the SSH connection is closed. It has a great [cheat sheet][cs]. It is also the topic of a great independent [blog post][tmuxblog].
 * List any open sessions `tmux ls`
 * Attach to existing session `tmux a <session if more than one>`
 * Create new session `tmux new -s session-name`
 * Kill a section `tmux kill-ses -t session-name`
 * Split pane vertically `ctrl+b`, `%`
 * Split pane horizontally `ctrl+b`, `”`
 * Switch panes `ctrl+b`, `o`
 * Close current pane `ctrl+b`, `x`
 * Detach from session `ctrl+b`, `d`

#### Build a bash script in nano
* Create empty script `touch script_name.sh`
* Open script `nano script_name.sh`
* Proceed with your analysis!
---------
#### Dependency information for this tutorial
* Institutional login: [University of San Francisco][usf]
 * The University of San Francisco hosts several servers available to graduate and undergraduate students. I am a biotechnology Master's student, class of 2022.
* VPN: [Global Protect][global-protect] for Windows 10
 * Many institutions require virtual private networks to login to their servers, allowing your workstation to imitate a local machine for cluster access.
* git version control: [GitHub][github]
* bash shell: [Git Bash][git-bash]
* Session management: [Tmux][tmux]
* Container admin: [Docker][docker]
* SSH credentials: contact your IT admin
* Instruction: Dr. Naupaka Zimmerman. Check out his extensive [GitHub page][drz]
[usf]: https://www.usfca.edu/arts-sciences/graduate-programs/biotechnology
[global-protect]: https://www.paloaltonetworks.com/products/globalprotect
[github]:[https://github.com/]
[git-bash]:[https://gitforwindows.org/]
[tmux]:[https://github.com/tmux/tmux/wiki]
[tmuxblog]:[https://github.com/2020F-usfca-btec-640/2020F-usfca-btec-640.github.io/blob/main/_posts/2020-11-07-What-is-Tmux.md]
[cs]:[https://tmuxcheatsheet.com/]
[docker]:[https://www.docker.com/]
[drz]:[https://github.com/naupaka]
