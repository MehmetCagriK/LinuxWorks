# The Working Directory

Working directory is the directory where we are. When we issue commands, it is
the directory where the commands are going to happen. There is only one working
directory in one shell. **pwd** command prints the full path of present working
directory. Paths are seperated by forward slash in Unix.

# Listing Files and Directories

**ls** command by itself, lists the files and directories in present working 
directory. ls has couuple options. For example;

* ls -l: This version prints one line per file which includes the size of the
file or directory, its permissions, name, last modification date etc.
* ls -la: This option shows files and directories starting with `.`(dot). In 
addition, there will be `d` for directory or `-` for file character at the start
of each line for every file or directory to distinguish them from each other by
type.
** `.`        Current directory
** `..`     : Immediate parent of current directory. Can be used multiple times
seperated by forward slash for chain parenting.
** `.<name> : Invisible configuration files. These
* ls -lah: This option prints the size of files in human readable format.

# Moving Around Filesystem

To change the working directory, we can use `cd <directory_name>`. Meaning of 
`.` and `..` are explained section above. 

## Auto Complete in Shell

If you do not know the full name of an argument, option, file, directory or 
command or you are lazy,you can type enough characters to distinguish them from 
other ones, then press tab to bring whole name of the searched one. If you did
not type enough characters, you can double tab to list the possible options 
that match against these insufficient pattern.

When you are giving an argument to a command that accepts directory, you can 
either give absolute path and relative path. Absolute paths start with forward
slash and relative paths start without one. Relative paths are relative to the
present working directory. 

Note: A single forward slash means root directory. A path starting with forward
slash includes all path from the root.

Note: ~ is synonim for current user's home directory. For me, it was 
``/home/cagri.``

Note: ``cd -`` takes you back to the last directory you were in.

# Filesystem Organization

The typical Unix filesytem organization is like below;

* /         : Root
* /bin      : Unix binaries and  programs
* /sbin     : System binaries
* /dev      : Devices, like hdd, keyboard, mouse etc.
* /etc      : System configuration
* /home     : User home directories. You start here when you login to Unix.
* /lib      : Libraries of code
* /tmp      : Temporary Files, deletable generally.
* /var      : Various files, mostly used by system
* /usr/bin  : User programs, tools, libraries etc. These are not the files. 
* /usr/etc  : Files go to the home directory.
* /usr/lib
* /usr/local
