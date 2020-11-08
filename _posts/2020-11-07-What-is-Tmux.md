---
layout: post
title:  "What is Tmux?"
date:   2020-11-07 12:54:04 -0700
categories: Tmux Think Create Features
---
![Internet Image](https://github.com/tmux/tmux/raw/master/logo/tmux-logo-medium.png?raw=true)

Tmux is an essential program for working with remote servers over SSH. SSH will drop the connection if a person's network fails or if they don't interact with the window for an extended period of time. This is significant because anything the person was running will stop, regardless if it is done or not. So, in order to avoid this mess, a person must "hand off" the work to tmux. The program will allow the process to continue even after they disconnect, whether it be on purpose or on accident.

**Tmux interface: on the command line, plain text**


## Think About It This Way
Let's say a student and their team must complete a presentation in two days, but this student has to leave and cannot access the slides after the first day. In order to complete the task on time, they must use a program such as Google Slides. This will allow the student to hand off the presentation to another person who can complete the task while they are away.

*Tmux ≈ Google Slides + the team who will complete the task*


## How To Create And Connect To Tmux

1) Start a new session
*Note: You can have as many tmux sessions running at a time! The work is saved and stays the same when you leave a particular session*

![tmux screenshot]({{ site.url }}/assets/tmux-01.jpg)

![tmux screenshot]({{ site.url }}/assets/tmux-02.jpg)
*The green line at the bottom of the screen tells the user they are in a tmux session (includes name of file and what is running, in this case bash)*

2) You can split the screen horizontally and vertically

__Vertical Split__ (Control-b and %)
![tmux screenshot]({{ site.url }}/assets/tmux-03.jpg)

__Horizontal Split__ (Control-b and ")
![tmux screenshot]({{ site.url }}/assets/tmux-04.jpg)

3) Example: You can run something, detach, and it will continue running until it is complete.

__Run Bash Script__
![tmux screenshot]({{ site.url }}/assets/tmux-05.jpg)

![tmux screenshot]({{ site.url }}/assets/tmux-06.jpg)
*Note: Even if you detach, this will continue to run*

__Detach__
Use: Control-b and d; to exit the tmux session

You will exit the session and see the message below
![tmux screenshot]({{ site.url }}/assets/tmux-07.jpg)

You can check what sessions are running with `tmux ls`
![tmux screenshot]({{ site.url }}/assets/tmux-08.jpg)

__Reconnect__
Use...
![tmux screenshot]({{ site.url }}/assets/tmux-09.jpg)

As you can see below the session kept running and finished the loop
![tmux screenshot]({{ site.url }}/assets/tmux-10.jpg)

4) Use `exit` to leave the tmux session

Once you exit, the session should no longer be listed
![tmux screenshot]({{ site.url }}/assets/tmux-11.jpg)

*Note: The files in tmux are the same as the ones outside of tmux. tmux is just a middle man!*
![Internet Image](https://mk0industcomhmhlrip6.kinstacdn.com/wp-content/uploads/2015/02/middleman.jpg)


## Some Features

Switching Panes

1) Use: Control-b followed by the letter o

2) Can assign numbers to panes using: Control-b and q     
*To Select Pane: Quickly enter the number of the pane you would like to use*

![tmux screenshot]({{ site.url }}/assets/tmux-12.jpg)


## More Information
Check out [Tmux][github-tmux] on Github for more information on the program. See [tmux shortcuts & cheatsheet][tmux-shortcuts-cheatsheet] for commands that are commonly used.

[github-tmux]: https://github.com/tmux/tmux/wiki
[tmux-shortcuts-cheatsheet]: https://gist.github.com/MohamedAlaa/2961058
