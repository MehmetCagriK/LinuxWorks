# Command Basics

Commands are actually programs. They are not big programs like Photoshop or 
Word but they still are program, although called commands generally. 

Commands are executable files reside in various places on the filesystem. Users
can also go to the directory that command file resides and execute there. One 
of the common places is /bin. There are many executable files in /bin folder.

Let's see some commands that are used to have information about commands;

* whereis <cmd_name>: Prints paths for binaries, sources and manuals
* which  <cmd_name> : Prints path for executable file(binary). Difference from
whereis that which uses PATH to print which version of the command will be 
used.
* whatis <cmd_name> : Prints simple information about the command
* <cmd_name> [-v, --version]: Prints the version of the command
* <cmd_name> [-h, --help]   : Prints the help page(simplified manual)
* q, ctrl q, ctrl x, escape: Exits the command
* ctrl c: Interrupts the program, hard way...
* **;** : semicolon can be used to seperate commands in the same line

# The PATH Variable

We know that commands are just executable files reside in various directories.
But how does Unix know where are those files? The answer to this is **PATH** 
variable. 

PATH variable simply holds a list of directories that Unix looks for when a 
command execution is needed. We can see current path with ``$PATH``;

```
/home/cagri/bin:/home/cagri/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:
/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
```

When Unix looks for a command in these directories, it searches from the first 
one to the last one. You can set the path with ``PATH=<path_list>``, without 
dollar sign before PATH. But changing this way 

If you remove a command's installed directory from the PATH variable, UNIX will
no longer be able find and execute them.

# System Information Commands

* date: Date which computer is set to, not UTC or anything.
* uptime: Prints the current time, total time elapsed from the start of the system,
 number of users that logged into Unix currently and load averages.
* who: Shows who is logged on, users may be duplicated(Not in Ubuntu, why?)
* users: List of distinct users
* uname[-mnrsvp]: Gives information about operating system.
** -s: kernel nameL -> Linux
** -n: network node hostnamec -> Cagri-UbuntuVB
** -r: kernel release ->  4.10.0-37-generic
** -v: kernel version -> # 41~16.04.1-Ubuntu SMP Fri Oct 6 22:42:59 UTC 2017
** -m: machine hardware name -> x86_64
** -p: processor -> x86_64
** -i: hardware platform -> x86_64
** -o: operating system -> GNU/Linux
* hostname: host that we are on   
* domainname: domain that we are on(in a network environment)

# Disk Information Commands

* df: Shows storage analysis of currently mounted disks like size, used 
space, available space percentage and mounted path.
* df -h: Shows size related information in 1024 version
* df -H: Shows size related information in 1000 version
* du: disk usage in the given path. Misbehaving in Ubuntu. Reports allocation
for that file.

# Viewing Processes

ps command is used to see process status. 

When we execute commands by Shell, it passes this request to the Kernel. Kernel
then allocates some memory and starts processes running on it. 
* ps: By default, it shows processes owned by user of the command
* ps -a: Processes owned by all users
* ps aux: All processes running on the Kernel. a means all processes, u means
putting user column and x means showing background processes. Output of this 
command is snapshot of that time. First column is user, then process id(unique
id given to processes), cpu percentage used, memory percentage used, virtual 
memory used and terminal.

# Monitoring Processes

Sometimes we want to track processed dynamically as the memory, CPU usage and
their existence changes. Command for that is top. top works differently in Unix
and Mac OS X. Fill this section later with Ubuntu usage.

# Stopping Processes

* ctrl c: It assumes process runs in terminal, you are in the process and tells
Unix to stop that process.
* kill <process_id>: Unix will try to kill but for some processes, this will not
kill process.
* kill -9 <process_id>:  Override Unix's careful approach, kill definitely.

# Text File Helpers

* wc: Prints the line, word and character count. For line, it counts line 
return.
* sort: Sorts the lines of the file and prints it. Does not modify. Capital 
letters and lowercase letters are treated different than each other. 
** -f: Ignores case of letters
** -r: Reverse sort
** -u: Sorted unique lines
* uniq: Ignores consecutive duplicate lines.
** -d: Prints consecutive duplicate lines
** -u: Prints non-duplicate lines

# Utility Programs

* cal / ncal: Shows current month's calendar.
** [month_num] [year_num]: Prints the month's and year's calendar.
** -y : Prints current year's calendar.
* nca: Rotates the day numbers and day names columns.
* bc: bench calculator
* expr: simpler calculator. ``expr 2 + 2``
* units: scientific unit converter

Author's note: Other than calendar and units, do not use these commands. Useless
things.

# Command History

We have seen up and down arrows are used to navigate between commands. There is
also a utility of Unix that saves bash commands into a history file. The file
is called *.bash_history* file in the home directory(~). This file is updated 
when bash is closed.

When you type ``history`` into bash, it will show you the list of commands with
numbers before them. You can use those numbers to reuse the command. Type 
exclamation point before the number of the command. When we hit up arrow, we will
see the actual command instead of the number.

You can type exclamation point before a part or full name of the command to 
return the most recent command starting with the argument. For example, 
``!vi`` will bring last command executed starting with vi.

* !3  : References history command 3
* !-2 : References command which was 2 back
* !cat: References most recent command starting with cat
* !!  : References previous command
* !$  : References previous command's arguments 
