# Naming Files

There are some rules and best practices for naming files in Unix;

* Maximum of 255 characters allowed
* Avoid special characters like /()%`+(!^+% Even if they are legal characters, 
you will need to escape them in order to tell Unix they are regular characters
in the filename. This creates needless typing.
* Unix is case sensitive by default. Using lowercase filenames is good practice.
* Spaces are allowed but you need to escape them with backslash(\). You can also
put filenames with spaces between quotes to tell Unix the filename is between
quotes. Underscore instead of space is a good practice.
** Autocomplete feature automatically escapes special characters with backslash.
* Using file endings like(.txt, .md etc) is suggested. It helps to differentiate
them from directories and commands. 

# Creating Files

There are three methods to create a file in Unix

* Unix text editors
* Direct output to a file
* touch

**touch** is a command that changes file access and modification times. It takes
filename argument; if it exists it modifies access and modification time to 
current time. If it does not exists, it creates an empty file with given name. 
Use man touch command to see what you can do with it!

# Unix Text Editors

There have been couple text editors in the history of Unix

* ed   : Earliest text editor, not user friendly.
* vi   : First visual text editor.
* vim  : Vi Improved. Modal.
* emacs: Editor macros, steep learning curve thanks to all those macros.
* nano : A simple text editor. 

# Reading Files

You can use any text editor to read contents of a file but that would be 
overkill. There is simpler methods to just read files

* cat  : Shorter for concatenate, this command concatenates file contents back to
back in given order. But you will most probably use it to read single files. cat
is fine to use shorter files.
* more : more is created to read longer files and paginates it. But it lacked
reversing to earlier pages and it is replaced by less(mostly).
* less : less is an improvement of more. You can traverse files in both 
directions and it loads only one page to memory at a time, this it is more 
efficient then more. man command uses less. You can use **g** key to go to the 
start of the file. You can use **G** to the end of the file.

# Reading Portions of Files

We can use the commands below to read head or tail of the file

# head: Displays lines from beginning of the file.
# tail: Displays lines from the end of the file.
## tail -f: Follows the tail of the file. It will track the end of the file.
Whenever there is a change, it will print it. It is an ongoing process. You can
use **ctrl c** to stop following.

# Creating Directories

# mkdir dir_name: Creates a directory in the current path. Does not create a 
directory  if the name already exists.

By default, mkdir works on the current directory. But you can give it a path 
like "mkdir <path>/dir_name" to create a directory in the given path. If this 
path does not exist, the command will give a warning. To force shell to create
parent directories that do not exist, use **-p** option as below;

```
mkdir -p dir1/dir2/dir3/dir4/test_dir
```

You can use -v option to give a feedback from this command. Try it yourself.

# Moving and Renaming Files and Directories

**mv** command is used for both moving and renaming files. Let's see the use 
cases below;

# ``mv file1.txt dir1/``: Moves file1.txt into the dir1 directory. If dir1 does
not exist,it won't move.
# ``mv file1.txt dir1`` : This one is tricky. If dir1 does not exist as a 
directory in current directory, it will rename file1.txt to dir1. If there is 
a directory called dir1 in current directory, it will move file1.txt into that 
directory.
Author's note: Trying an extra slash does not kill the user. So, to increase
readability , just use extra slash to tell readers that you want to move into
a directory. Also use better names for files and directories.
# ``mv file1.txt file2.txt`` : Rename the file.

You can give path before filenames when using mv command. There are important
options to use with **mv** command;

# -n: no overwriting if there is a file with same name.
# -f: force overwriting, this is turned on by default.
# -i: interactive overwriting: ask user before overwriting.
# -v: verbose, print more info about the command.

# Copying Files and Directories

**cp** is the command to go when you want to copy files and directories.
Usage of it is the same as mv. 
To move files;
``cp [path]/source_file [path]/target_file``

To move directories, use -R option.
``cp -R [path]/source_dir [path]/destination_dir``

cp has same options as mv. Also, -f option is turned on by default.

# Deleting Files and Directories

When you delete a file in Unix, it is gone for good. Moving files to **.trash**
is not same as deleting in Unix. Moving to **.trash** gives user a time to 
reconsider their life choices and file's future.

``rm file_to_del``   : Deletes files given.
``rmdir dir_to_del`` : Deletes the empty directory.
``rm -R dir_to_del`` : Deletes the directory and contents recursively.

**rmdir** is safer option to delete directories and it takes no argument to 
delete directories that are not full. Use **rm -R** with caution.

# Hard Links

Hard links are weird concept to understand at the start. When you create a 
hard link to a file, it is exactly a dynamic copy of the original file if 
original file changes but not if it is deleted. Hardlinks also track the 
original file if they are moved.

Hardlinks will retain the last data in the original file after the deletion of
the original file. This makes sense in a multi-user linux environment. Changes
made to the original file will be tracked by users who have hardlink to the 
original file but if a user deletes the original file, users will still retain
last version of the file.

Hardlink files are also large in size. This comes with the ability of tracking
files throughout the file system and retaining last data.

* ``ln file_to_link hard_link_name``: Simple command to create a hardlink.
* Reference to a file in the filesystem.
* Does not break when file is moved
* Does not break when file is deleted.
 
# Symbolic Links

Symbolic links are easier to understand.

* ``ln -s target_file symlink``
* Are just a reference to a file or a directory
* Breaks if moved
* Breaks if deleted
* Resurrects if target is brought back

Symbolic links have relatively lower in size compared to hardlinks. Size is 
same as the path of the original file in bytes.

Symlinks have **l** prefix, as opposed to **d** or**-**. They are printed in ls 
like below;

``symlink -> file_path``


# Searching in Files and Directories

Find is an extremely complex but useful tool to search for files in the 
filesystem. The most basic usage of find is below;

``find directory_path expression``

Expression can be A LOT of things  and that gives **find** its power. Let's see
basic search by name.

``find ~/Downloads chrome_setup``: Searches for a file named exactly 
"chrome_setup" under Downloads directory. 

We can also use wildcard expressions to use better expressions.

* \*: Any number of  characters
* ? : A single character
* [abc]: One of the characters in the brackets

``find ~/Downloads -name chrome*``
``find ~/Downloads -name chrome?setup``
``find ~/Downloads -name chrome[_-]?*``

Another nice usage is excluding some path;

``find ~/Downloads -name chrome* -and -not -path *SetupFiles*``


