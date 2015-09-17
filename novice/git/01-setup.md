---
layout: page
title: Version Control with Git
subtitle: 1. Setting Up Git
minutes: 10
---
> ## Learning Objectives {.objectives}
>
> *   Explain which initialization and configuration steps are required once per machine,
>     and which are required once per repository.

> ## Prerequisites {.prereq}
>
> In this lesson we use Git from the Bash Shell.
> Some previous experience with the shell is expected,
> *but isn't mandatory*.

## Get Started - The Scenario - Comedy Monsters plan a space mission

Lets walk through a (painfully contrived) little scenario to get some hands on experience using Git.

**Linux and Mac** users should open a **terminal**, windows users to should go to the Start Menu open GitBash from the Git group.

**Post-Its**

![Monsters](img/slides/version-control-with-git-slides - 09.jpg)
![in Space](img/slides/version-control-with-git-slides - 10.jpg)

We've have been hired by the **Transylvanian Space Agency**
to investigate if it is possible to send their next planetary lander to Mars.

**Switch out of fullscreen**

**Open Terminal** **Use other projector**


![Local Configuration](img/slides/version-control-with-git-slides - 11.jpg)

**Working individually**, we’ll start by exploring how version control can be used to keep track of what *one person* did and when.

## Setting Up ##

The first time we use Git on a new machine,
we need to configure a few things.

Make sure you're in your home directory (not another repository).

~~~ {.bash}
$ cd
~~~

Set some global options

~~~ {.bash}
$ git config --global user.name "Vlad Dracula"
$ git config --global user.email "vlad@tran.sylvan.ia"
~~~

(Please use your own name and email address instead of Dracula's.)

You can set your favourite text editor, following this table:

| Editor             | Configuration command                            |
|:-------------------|:-------------------------------------------------|
| nano               | `$ git config --global core.editor "nano -w"`    |
| Notepad++ (Win)    | `$ git config --global core.editor "'c:/program files (x86)/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"`|

(See the Etherpad)

Git commands are written `git verb`,
where `verb` is what we actually want it to do.
In this case,
we're telling Git:

*   our name and email address,
*   what our favorite text editor is, and
*   that we want to use these settings globally (i.e., for every project),

The three commands above only need to be run once:
the flag `--global` tells Git to use the settings for every project on this machine.

You can check your settings at any time:

~~~ {.bash}
$ git config --list
~~~

[Next - Creating a Repository](02-create.html)
