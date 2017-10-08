### Command Line Interfaces

They generally work as

1. User types a command
2. System runs those commands
3. They system displays the output

Advantages of using command line interfaces.

1. A CLI(Command Line Interface) is programmable.
2. It is efficient in terms of network bandwidth.
3. You can use terminal edit files in distant system without having copying it 
   into local system.

### Virtual Machine
Virtual machines are softwares; that simulate a computer. The operating system
installed on your physical computer is called host OS(in my case, it was 
Windows 10) and operating system installed on virtual machine is called guest 
OS.

Virtual machines are used for;

1. Ensuring all developers work on identical environment with correct programs
are installed and correct configurations are done
2. Isolating programming projects from everything else on programmer' s computer.
The user can configure their guest OS without disrupting their regular OS
3. Simulate environments that software will be deployed to.

#### Vagrant

Vagrant is a program that makes VMs more convenient to use. With it, you can 
automatically configure your Virtual Machine installation and configuration
by following the instructions in the __Vagrantfile__.

Instead of using a software program with a more standard visual user interface,
many programmers use CLIs for their flexibility.

After installing Vagrant and VirtualBox into your computer, do the followings;

1. Open the terminal
2. Change to a directory you want to work with(arbitrary)
3. Create a Vagrantfile or download a sample
4. Type ``vargant up`` and enjoy the rest. Vagrant will download Linux OS.

Note: You will use Virtual Box to run virtual machine and Vagrant to configure 
it. Vagrant is a software that configures virtual machine and lets you share 
files between virtual machine's file system and host computer(physical)

### Terminal

You can think the terminal as an alternative interface to communicate with
computer. Graphical UIs generally have commonly used commands but most of
the commands do not need graphical interface.

The terminal is a program that draws text on a window and allows you to type 
things in on a keyboard. It is just a terminal emulator, like the old school 
ones. But terminal does not know what to do with those commands you typed. It
needs another program, shell, to do the real work.

When you type some text into the terminal and press enter, shell interprets is
as a command. Then shell decides which program to run, run it and sends the 
output back into the terminal. The shell is not only option to use terminal 
programs with. Linux and Mac OSX use GNU Bash as default but other options 
exist like seashell etc.

You can also use Shell without a terminal. You can write shell commands into
a file and arrange your computer to run the Shell program on that file. This is
called shell scripting.

Commands consist of name and arguments. First word is name of the command and 
the rest is argument list(if exists). Some useful commands are;

* date: prints the date and time
* expr <math_expression>: calculates mathematical expression
* echo: echoes the arguments back
* uname: prints out the operating system's name

### Filenames in Linux
Files don' t have to have particualar extension at the end of a filename. There
is no hard rule about it. But there are couple filetypes with certain 
extensions.

* .pem(privacy enchanced mail): crypto key
* .sh: shell scripts.You can do anything with shell script what you can do with 
CLI.

### Some Common Commands

* ls: Lists the name of the files in the current directory
* unzip: Takes one argument. It unzips the file and lists the file names.
* cat: This command "concatenates" the file. It is useful for quickly checking
a file content.
Note: When typing arguments or commands, press tab key to use auto-complete
feature. Double tab will bring the list of the files that are matched by the
pattern.
* wc: This is the word count program. It prints the lines, words and bytes are
in the file.
* diff: Compares files and tells you how they differ. The output starting with 
< belongs to the left file and the output starts with the > right belongs to 
the right file. 
* rm: The program that is used to remove files/directory in the argument given.
* Ctrl C: This command is generally used to interrupt ongoing process of the
current running program. It stops the process prematurely.
* Ctrl d: This command is used to signify the end of file. This is more 
graceful than Ctrl c.
* less: This program is generally used to read longer files. It prints one page
at a time.
** <: Left angle is used to navigate to the start of the file.
** >: Right angle is used to navigate to the end of the file. 
** /<text_pattern>: Press enter to execute a search. Use n to go to next 
occurrence and N to go to first occurrence. You can use regular expressions to
search better.
** 
** q: quit

### Manual Pages

You don' t have to remember every detail about a command. All common shell 
programs come with the manual.

Files starting with "." are generally used for caching, configuration and other
things that you do not immediately care about. Shell hides them by default.

### File System

There are two kinds of objects in Linux filesystem: files and directories.
In Linux, filename rules are pretty flexible. Only constraint is that you can't
have / (forward slash) in your filenames. 

When you write a filename that contains spaces or punctuation like !#$()[]%& ;
you shall put the filename in single quotes or prece every special character 
with a backslash. The latter is called escaping while former is called quoting.

At the top of filesystem tree, there is root: top level directory. In Linux, 
you can have multiple discs and multiple partitions. But unlike Windows, in 
Linux there are no seperate top level directories for drives like( C:, D:).
All files are under placed under the root/ . 

In Linux, directories are seperated with forward slash where, in Windows, 
directories(folders) are seperated with backslashes. Every directory starts
with forward slashes.

In shell, or any other program; there is a term called working directory. It 
can be thought as directory shell is looking at. Many commands like ls, rm, mv
etc takes default argument as current directory if the user does not provide 
one.

Absolute paths are paths starting from all the way up the root to the file 
itself. But using absolute paths all the time can be harder. Instead, we can
use relative paths(relative to the current working directory).

Absolute paths start with forward slash while relative paths don't.You can use
tilde to access home.

You can use forward slash to access root.

cd without arguments takes user to home directory.

These commands are unusually short. There are 2 reasons for this. The most 
important is that old systems had much lower bandwidth so shortening command
names helps. Secondly they are faster to type.

Use mkdir to  create directories. You can use rmdir to delete a directory(if
it is empty). But if it is not, there is another called command called rm with
argument -r to recursively remove the the directory.

### Globbing

Globbing is the technique to match files by name in Unix shell. A few pattern 
samples are given below;

* *: Matches any number of characters.
* ?: Matches any single character.
* {pat_1, pat_2}: Matches either one of patterns. Can be used n times.
* [aeiou]: Matches any single one of the characters inside the bracket.

Note: Filenames in Linux are case sensitive. It also applies for Globbing also. 
