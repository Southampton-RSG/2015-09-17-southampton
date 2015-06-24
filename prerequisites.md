---
layout: page-md
title: Software Prerequisites
---

Prior to the workshop (or using the training material yourself), you should ensure you have the following software installed on your laptop - please do this as soon as you can.


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

We teach with Python 2.7, since it is still the most widely used version. We will also employ the numpy and matplotlib libraries and the nose unit testing framework.

#### Windows

We recommend the [Anaconda Python distribution](http://continuum.io/downloads). This provides Python plus the required libraries and frameworks

#### Mac OS X

Mac OS 10.9 Mavericks and 10.10 Yosemite ship with Python 2.7, numpy and matplotlib installed by default. You will need to install nose. Open a terminal and enter the following command:

~~~ {.code}
sudo easy_install nose
~~~

If you intend to use an earlier version of Mac OS X, please contact us before the event (emailing both s.crouch@software.ac.uk and j.robinson@software.ac.uk).

#### Linux

Most distros include Python 2.7 by default. Install the libraries in a terminal like this:

Ubuntu 14.04LTS and derivatives:

~~~ {.code}
sudo apt-get install python-numpy python-matplotlib python-nose
~~~

Fedora 22:

~~~ {.code}
su -
dnf install numpy python-matplotlib python-nose
~~~

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
curl -L http://goo.gl/HuPJu3 | python
~~~

You should see eight passes and no failures.  If anything fails, please contact us (emailing both s.crouch@software.ac.uk and j.robinson@software.ac.uk) with details by Thursday 18 June at the latest.

## During the workshop

We will make use of this etherpad during the workshop (Etherpad allows a group to edit documents online collaboratively in real-time). Please use this to keep collaborative notes and ask (and answer!) each others questions.