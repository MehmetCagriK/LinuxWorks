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

* ls: lists the name of the files in the current directory
* unzip: takes one argument. It unzips the file and lists the file names.
* cat: this command "concatenates" the file. It is useful for quickly checking
a file content.
* 

