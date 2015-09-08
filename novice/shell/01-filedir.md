---
layout: page
title: The Unix Shell
subtitle: Files and Directories
minutes: 15
---
> ## Learning Objectives {.objectives}
>
> *   Explain the similarities and differences between a file and a directory.
> *   Translate an absolute path into a relative path and vice versa.
> *   Construct absolute and relative paths that identify specific files and directories.
> *   Explain the steps in the shell's read-run-print cycle.
> *   Identify the actual command, flags, and filenames in a command-line call.
> *   Demonstrate the use of tab completion, and explain its advantages.

The part of the operating system responsible for managing files and directories is called the **file system**.
It organizes our data into files,
which hold information,
and directories (also called "folders", for example, on Windows systems),
which hold files or other directories.

Several commands are frequently used to create, inspect, rename, and delete files and directories.
To start exploring them,
let's open a shell window:

~~~ {.bash}
$
~~~

The dollar sign is a **prompt**,
which represents our input interface to the shell.
It shows us that the shell is waiting for input;
your shell may show something more elaborate.

Type the command `whoami`,
then press the Enter key (sometimes called Return) to send the command to the shell.
The command's output is the ID of the current user,
i.e.,
it shows us who the shell thinks we are:

~~~ {.bash}
$ whoami
~~~
~~~ {.output}
nelle
~~~

More specifically, when we type `whoami` the shell:

1.  finds a program called `whoami`,
2.  runs that program,
3.  displays that program's output, then
4.  displays a new prompt to tell us that it's ready for more commands.

Next,
let's find out where we are by running a command called `pwd`
(which stands for "print working directory").
At any moment,
our **current working directory**
is our current default directory,
i.e.,
the directory that the computer assumes we want to run commands in
unless we explicitly specify something else.
Here,
the computer's response is `/Users/nelle`,
which is Nelle's **home directory**:

~~~ {.bash}
$ pwd
~~~
~~~ {.output}
/Users/nelle
~~~

Make a note of what is output here - it will likely come in handy later!

> ## Home directory {.callout}
>
> The home directory path will look different on different operating systems.
> On Linux it will look like `/home/nelle`,
> on Git Bash on Windows it will look like `/c/Users/nelle`,
> and on Windows itself it will be similar to `C:\Documents and Settings\nelle`.
> Note that it may also look slightly different for different versions of 
> Windows.


> ## Alphabet Soup {.callout}
>
> If the command to find out who we are is `whoami`, the command to find
> out where we are ought to be called `whereami`, so why is it `pwd`
> instead? The usual answer is that in the early 1970s, when Unix was
> first being developed, every keystroke counted: the devices of the day
> were slow, and backspacing on a teletype was so painful that cutting the
> number of keystrokes in order to cut the number of typing mistakes was
> actually a win for usability. The reality is that commands were added to
> Unix one by one, without any master plan, by people who were immersed in
> its jargon. The result is as inconsistent as the roolz uv Inglish
> speling, but we're stuck with it now.

There are some helpful things to know which can save us some typing:

* Using the up and down arrow keys allow you to cycle through your previous commands - plus, useful if you forget exactly what you typed earlier!
* Ctrl-A and Ctrl-E will send the cursor to the start and end of a line respectively; much quicker than using the left/right arrow keys on a long line

There are others that can also help us --- we'll look at a few later on.

To understand what a "home directory" is,
let's have a look at how the file system as a whole is organized.
At the top is the **root directory**
that holds everything else.
We refer to it using a slash character `/` on its own;
this is the leading slash in `/Users/nelle`.

Inside that directory are several other directories, e.g.:
`bin` (which is where some built-in programs are stored),
`data` (for miscellaneous data files),
`Users` (where users' personal directories are located),
`tmp` (for temporary files that don't need to be stored long-term),
and so on:

![The File System](fig/filesystem.svg)

We know that our current working directory `/Users/nelle` is stored inside `/Users`
because `/Users` is the first part of its name.
Similarly,
we know that `/Users` is stored inside the root directory `/`
because its name begins with `/`.

Underneath `/Users`,
we find one directory for each user with an account on this machine, e.g.:
`/Users/imhotep`,
`/Users/larry`,
and ours in `/Users/nelle`,
which is why `nelle` is the last part of the directory's name.

![Home Directories](fig/home-directories.svg)

> ## Path {.callout}
>
> Notice that there are two meanings for the `/` character.
> When it appears at the front of a file or directory name,
> it refers to the root directory. When it appears *inside* a name,
> it's just a separator.

Let's see what's in our home directory by running `ls`,
which stands for "listing" (the `...` refers to other files and directories that have been left out for clarity):

~~~ {.bash}
$ ls
~~~
~~~ {.output}
2015-09-17-southampton Misc                   Solar.pdf
Applications           Movies                 Teaching
Desktop                Music                  ThunderbirdTemp
Development            Notes.txt              VirtualBox VMs
Documents              Pictures               bin
Downloads              Pizza.cfg              mbox
...
~~~

Of course, this listing will depend on what you have in your own home directory.

<!-- ![Nelle's Home Directory](fig/homedir.svg) -->

`ls` prints the names of the files and directories in the current directory in alphabetical order,
arranged neatly into columns.
We can make its output more comprehensible by using the **flag** `-F`,
which tells `ls` to add a trailing `/` to the names of directories:

~~~ {.bash}
$ ls -F
~~~
~~~ {.output}
2015-09-17-southampton/ Misc/                   Solar.pdf
Applications/           Movies/                 Teaching/
Desktop/                Music/                  ThunderbirdTemp/
Development/            Notes.txt               VirtualBox VMs/
Documents/              Pictures/               bin/
Downloads/              Pizza.cfg               mbox
...
~~~

Here,
we can see that the home directory contains a number of **sub-directories**.
The names that don't have trailing slashes,
like `notes.txt`, `pizza.cfg`, and `solar.pdf`,
are plain old files.
And note that there is a space between `ls` and `-F`:
without it,
the shell thinks we're trying to run a command called `ls-F`,
which doesn't exist.

> ## What's In A Name? {.callout}
>
> You may have noticed that all of these files' names are "something dot
> something". This is just a convention: we can call a file `mythesis` or
> almost anything else we want. However, most people use two-part names
> most of the time to help them (and their programs) tell different kinds
> of files apart. The second part of such a name is called the
> **filename extension**, and indicates
> what type of data the file holds: `.txt` signals a plain text file, `.pdf`
> indicates a PDF document, `.cfg` is a configuration file full of parameters
> for some program or other, and so on.
>
> This is just a convention, albeit an important one. Files contain
> bytes: it's up to us and our programs to interpret those bytes
> according to the rules for PDF documents, images, and so on.
>
> Naming a PNG image of a whale as `whale.mp3` doesn't somehow
> magically turn it into a recording of whalesong, though it *might*
> cause the operating system to try to open it with a music player
> when someone double-clicks it.

Now let's take a look at what's in our repository materials directory, `2015-09-17-southampton`, by running `ls -F 2015-09-17-southampton`.

i.e.,
the command `ls` with the **arguments** `-F` and `2015-09-17-southampton`.
The second argument --- the one *without* a leading dash --- tells `ls` that
we want a listing of something other than our current working directory:

~~~ {.bash}
$ ls -F 2015-09-17-southampton
~~~
~~~ {.output}
CONDUCT.md              _config.yml             prerequisites.html
CONTRIBUTING.md         _includes/              prerequisites.md
CUSTOMIZATION.md        _layouts/               reference.html
DESIGN.md               css/                    schedule.html
FAQ.md                  deck.js/                setup/
...
~~~

The output shows us that there are many text files and sub-directories.
Organising things hierarchically in this way helps us keep track of our work:
it's a bit like using a filing cabinet to store things. It's possible to put hundreds of files in our home directory,
just as it's possible to pile hundreds of printed papers on our desk,
but it's a self-defeating strategy.

Notice, by the way, that we spelled the directory name `2015-09-17-southampton`.
It doesn't have a trailing slash:
that's added to directory names by `ls` when we use the `-F` flag to help us tell things apart.
And it doesn't begin with a slash because it's a **relative path**,
i.e., it tells `ls` how to find something from where we are,
rather than from the root of the file system.

> ## Parameters vs. Arguments {.callout}
>
> According to [Wikipedia](https://en.wikipedia.org/wiki/Parameter_(computer_programming)#Parameters_and_arguments),
> the terms argument and **parameter**
> mean slightly different things.
> In practice,
> however,
> most people use them interchangeably or inconsistently,
> so we will too.

Typing `ls -F 2015-09-17-southampton` is a bit painful, so a handy shortcut is to type in the first few letters and press the *TAB* key, e.g.

~~~ {.bash}
$ ls -F 201
~~~

Pressing *TAB*, the shell automatically completes the directory name:

~~~ {.bash}
$ ls -F 2015-09-17-southampton/
~~~

This is known as *tab completion* on any matches with those first few letters.
If there are more than one files or directories that match those letters, the shell will show you both --- you can then enter more characters (then using *TAB* again) until it is able to identify the precise file you want and finish the tab completion.

If we run `ls -F /2015-09-17-southampton` (*with* a leading slash) we get a different response,
because `/2015-09-17-southampton` is an **absolute path**:

~~~ {.bash}
$ ls -F /2015-09-17-southampton
~~~
~~~ {.output}
ls: /2015-09-17-southampton: No such file or directory
~~~

The leading `/` tells the computer to follow the path from the root of the file system,
so it always refers to exactly one directory,
no matter where we are when we run the command.
In this case, there is no `data` directory in the root of the file system.

What if we want to change our current working directory?
Before we do this,
`pwd` shows us that we're in `/Users/nelle`,
and `ls` without any arguments shows us that directory's contents (as before):

~~~ {.bash}
$ pwd
~~~
~~~ {.output}
/Users/nelle
~~~
~~~ {.bash}
$ ls
~~~
~~~ {.output}
2015-09-17-southampton Misc                   Solar.pdf
Applications           Movies                 Teaching
Desktop                Music                  ThunderbirdTemp
Development            Notes.txt              VirtualBox VMs
Documents              Pictures               bin
Downloads              Pizza.cfg              mbox
...
~~~

We can use `cd` followed by a directory name to change our working directory.
`cd` stands for "change directory",
which is a bit misleading:
the command doesn't change the directory,
it changes the shell's idea of what directory we are in.

~~~ {.bash}
$ cd 2015-09-17-southampton
~~~

`cd` doesn't print anything,
but if we run `pwd` after it, we can see that we are now in `/Users/nelle/2015-09-17-southampton`.
If we run `ls` without arguments now,
it lists the contents of `/Users/nelle/2015-09-17-southampton`,
because that's where we now are:

~~~ {.bash}
$ pwd
~~~
~~~ {.output}
/Users/nelle/2015-09-17-southampton
~~~
~~~ {.bash}
$ ls -F
~~~
~~~ {.output}
CONDUCT.md              _config.yml             prerequisites.html
CONTRIBUTING.md         _includes/              prerequisites.md
CUSTOMIZATION.md        _layouts/               reference.html
DESIGN.md               css/                    schedule.html
FAQ.md                  deck.js/                setup/
...
~~~

We now know how to go down the directory tree:
how do we go up?
We could use an absolute path:

~~~ {.bash}
$ cd /Users/nelle
~~~

but it's almost always simpler to use `cd ..` to go up one level:

~~~ {.bash}
$ pwd
~~~
~~~ {.output}
/Users/nelle/2015-09-17-southampton
~~~
~~~ {.bash}
$ cd ..
~~~

`..` is a special directory name meaning
"the directory containing this one",
or more succinctly,
the **parent** of the current directory.
Sure enough,
if we run `pwd` after running `cd ..`, we're back in `/Users/nelle`:

~~~ {.bash}
$ pwd
~~~
~~~ {.output}
/Users/nelle
~~~

Let's go back into the repository directory:

~~~ {.bash}
$ cd 2015-09-17-southampton
~~~

The special directory `..` doesn't usually show up when we run `ls`.
If we want to display it, we can give `ls` the `-a` flag:

~~~ {.bash}
$ ls -F -a
~~~
~~~ {.output}
./                      Makefile                novice/
../                     README.md               prerequisites-ref.html
.git/                   SETUP.md                prerequisites.html
.gitignore              _config.yml             prerequisites.md
CONDUCT.md              _includes/              reference.html
CONTRIBUTING.md         _layouts/               schedule.html
CUSTOMIZATION.md        css/                    setup/
...
~~~

`-a` stands for "show all";
it forces `ls` to show us file and directory names that begin with `.`,
such as `..` (which, if we're in `/Users/nelle/2015-09-17-southampton`, refers to the `/Users/nelle` directory).
As you can see,
it also displays another special directory that's just called `.`,
which means "the current working directory".
It may seem redundant to have a name for it,
but we'll see some uses for it soon.
Finally, we also see a file called `.bash_profile`. This file usually contains settings to customize the shell (terminal). For this lesson material it does not contain any settings. There may also be similar files called `.bashrc` or `.bash_login`. The `.` prefix is used to prevent these configuration files from cluttering the terminal when a standard `ls` command is used.

> ## Orthogonality {.callout}
>
> The special names `.` and `..` don't belong to `ls`;
> they are interpreted the same way by every program.
> For example,
> if we are in `/Users/nelle/2015-09-17-southampton`,
> the command `ls ..` will give us a listing of `/Users/nelle`.
> When the meanings of the parts are the same no matter how they're combined,
> programmers say they are **orthogonal**:
> Orthogonal systems tend to be easier for people to learn
> because there are fewer special cases and exceptions to keep track of.

![File System for Challenge Questions](fig/filesystem-challenge.svg)

> ## Relative path resolution {.challenge}
>
> If `pwd` displays `/Users/thing`, what will `ls ../backup` display?
>
> 1.  `../backup: No such file or directory`
> 2.  `2012-12-01 2013-01-08 2013-01-27`
> 3.  `2012-12-01/ 2013-01-08/ 2013-01-27/`
> 4.  `original pnas_final pnas_sub`

> ## `ls` reading comprehension {.challenge}
>
> If `pwd` displays `/Users/backup`,
> and `-r` tells `ls` to display things in reverse order,
> what command will display:
>
> ~~~
> pnas-sub/ pnas-final/ original/
> ~~~
>
> 1.  `ls pwd`
> 2.  `ls -r -F`
> 3.  `ls -r -F /Users/backup`
> 4.  Either \#2 or \#3 above, but not \#1.

> ## Exploring more `ls` arguments {.challenge}
>
> What does the command `ls` do when used with the `-s` and `-h`
> arguments?
