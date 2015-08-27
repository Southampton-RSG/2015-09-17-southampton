---
layout: page-md
title: Software Prerequisites
---

**Prior to the workshop, it is vital that you install the following software on your laptop!** There is little time during the workshop to deal with installation problems, so it makes the day run much more smoothly if you arrive with your software already installed.

## Help!

We maintain a list of common problems that can occur during installation and ways of solving them. Take a look at the [Configuration Problems and Solutions wiki page](https://github.com/swcarpentry/workshop-template/wiki/Configuration-Problems-and-Solutions) for help.

If you still have trouble, we will run a **Software Installation surgery from 12.00 until 17.00 on 10 September 2015**. This will take place in room 3013 (Simon Hettrick's office), Building 32, Highfield campus. You don't need to make an appointment: just turn up. 

## Text Editor

You are free to use your preferred text editor. If you don&#39;t have one, we recommend:

#### Windows

[Notepad++](https://notepad-plus-plus.org/download/).

#### Mac OS X, Linux

Nano, which is terminal based and is installed by default. You can verify you have this installed by typing the following at a terminal:</p>

~~~ {.code}
nano
~~~

Whilst in Nano, press CTRL+X to exit (this will prompt you to save or discard any modified file).


## Python

We teach with Python 3.4, since it is on a clear path to becoming the most widely used version. 

Go to the [Anaconda Python distribution](http://continuum.io/downloads#34) site. Based on your operating system ( Windows, Linux or MAC OS X) and corresponding architecture (34-bit or 64-bit), you need to select the icon for your operating system followed by `I WANT PYTHON 3.4*` on the right hand top corner of `CHOOSE YOUR INSTALLER` section.

Follow the instructions on the screen as well as `CHOOSE YOUR INSTALLER` section. 

The above installation provides `Python` plus `numpy`, `matplotlib` libraries and the `nose` framework required for the workshop.


## Git

In this workshop we will work with remote Git repositories hosted at Github. You should [create an account](https://github.com/join) there before the event.

#### Windows

Download and install [Git for Windows](http://git-scm.com/download/win). You can accept the default installation options. In this workshop we will use Git via the Git Bash command line, installed as part of this package.

#### Mac OS X

Git will be installed automatically the first time you try to run it.  Open  terminal and type:

~~~ {.code}
git
~~~

Follow the prompts to install the Apple command line development tools.

#### Linux

Install via a terminal like this:

Ubuntu 14.04LTS and derivatives:

~~~ {.code}
sudo apt-get install git
~~~

Fedora 22:

~~~ {.code}
su -
dnf install git
~~~

## Verify your setup

All of the exercises in this workshop will take place at the command line via the Bash shell.  In Mac OS X and Linux, this is your normal terminal environment.  In Windows, the Git Bash shell has been installed and can be accessed via the Git entry in the Start Menu.

We provide a simple Python script to test that the prerequisites have been correctly installed. You can retrieve and execute the test at the Bash prompt by typing (pasting) the following command:

~~~ {.code}
curl -L http://goo.gl/HuPJu3 | python3.4
~~~

You should see eight passes and no failures.  If anything fails, please contact us (emailing s.crouch@software.ac.uk, j.robinson@software.ac.uk and d.inupakutika@software.ac.uk) with details by **Thursday 10 September** at the latest.

## During the workshop

We will make use of the etherpad during the workshop (Etherpad allows a group to edit documents online collaboratively in real-time). Please use this to keep collaborative notes and ask (and answer!) each others questions.
