# Unix Groups

Unix group is a set of users. Each user belongs to a primary group and any
number of other groups as well. Groups are useful for associating a group of
users with a file. So, file's permissions can be set to allow group members to
access  files, directories or commands.

You can type ``groups`` to see which groups you belong to.

# File and Directory Ownership

Ownership is an essential part of multi-user environment.  It tells which files 
belong to you, which one you can access and can not. You can see ownership of 
the files and directories with ``ls -la``. It is the second column from the 
left. Third column is group that associated with file and directory.

Permissions of the files and directories can be set based on the group and the
 owner.
Ownership and group can be changed with commands below;

* ``chown kevin:staff ownershipt.txt``: Change both
* ``chown kevin ownershipt.txt``      : Change only owner
* ``chown :staff ownershipt.txt``     : Change only group
* ``chown kevin:staff dir1``          : Change both, only affects directory
* ``chown -R kevin:staff dir1``       : Change both, affects directory and all 
its contents.

Ownership changes are security concers for Unix. Therefore, you have to type
**sudo** before chown command.

# File and Directory Permissions

We can see permissions with ``ls -la`` command. In the first block, we will see
a string consists of **r**, **w**, **x**, **-** characters. Lets's inspect them;

* ``r``: Means read permission. Ability to see the content.
* ``w``: Means write permission. Ability to change the content.
* ``x``: Means execute permission. Execute permission is making executable 
files(scripts etc) runnable by user and for directories, it means ability to 
search inside them.

This string consists of 9 characters(refer to the list above). First three for 
current user, second three is for group and third three is everyone else. If 
one of these three does not have the permission, dash is written at that slow.

An example: ``rwxrw-r--``;
* User can read, write and execute
* User's group can read and write but can not execute
* Others can only read, can not write and execute

# Setting Permissions Using Alpha Notation

Alpha notation is the 9 character string that represents permissions.You can use
chmod command to change permissions;

* ``chmod ugo=rwx filename``: Give all categories all rights
* ``chmod u=rwx,g=rw,o=r filenmae``  : More strict permission
* ``chmod ug+w filename``: Add write permissions to user and group
* ``chmod u-x filename`` : Remove write permission of user
* ``chmod a+w filename`` : **a** represents all three categories.
* ``chmod g-w dir1`` : Removes write permission of group only on the directory.
* ``chmod -R g-w dir1`` : Removes write permisson of group from the directory
and all its contents recursively.

**=** sets, **+** adds and **-** removes.
# Setting Permissions Using Octal Notation

Although alpha notation is enough to change permissions, octal notation is also
another method of doing it and it is extremely popular.

* r = 4
* w = 2
* x = 1

The output of a set of rights for certain category is simply sum of equivalent 
numbers of those permissions. For example 4 + 2 + 1 = 7 means rwx permission.
5 means read and execute, 1 means only execute and so on. Example usage;

* ``chmod 755 filename``: Give user, group and others read and execute but only
write permission to user.

# The Root User

The root user is superuser account that can do **anything** on the system. This
user has all permission on all files, creates and deletes accounts etc. As the 
root user, you can create the user accounts, give them a password and allow them
to login later. In Ubuntu install, this is handled by installer.

# Sudo and Sudoers

**sudo** is a command that allows us temporarily to take place of root. sudo
does not mean super user do. It means substituting another user.Example usage;

* ``sudo ls -la": When you prefix a command with sudo, system asks for password.
It is not root password but user's own password. It makes sure we are admin 
before we do admin things. Password entry stays valid for about 5 minutes then 
the system asks again.

Only admin users can use sudo command. In Unix, there is a file called sudoers.

You can use sudo take priviledges of another user instead of root user.

``sudo -u lynda whoami``: Takes priviledges of lynda(effectively logins with 
lynda) and applies whoami command.

