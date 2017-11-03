# Profile, Login And Resource Files

Upon logging to a bash shell, first file that is "executed" is /etc/profile.
Let's check our personal configuration files. These files can be 
*~/.bash_profile*, *~/.bash_login*, *~/.profile*, *~/.login*. These are dot 
files, meaning they are not visible normally.

After reading /etc/profile, bash looks for the files above in our home 
directory in the given order. It reads the commands when it finds first match,
and ignores the rest.

When we first open a terminal windows, it is the login shell. When we type 
*bash* in terminal, a new subshell is opened. We can further configure subshell
to our like if we want, by saving the configuration in the *~/.bashrc* file. 
For convenience, to use the same configuration for both login shell and 
sub-shell, append the code below to the end of main configuration file(one of 
the four listed above);

```
# Lines starting with asterisk are comment lines.
# If you can find ~/.bashrc file, load everything in it.
if [ -f ~/.bashrc ]; then
   source ~/.bashrc
fi
```
After making this change, you can only edit ~/.bashrc file to make same 
configuration for every shell instance. But when we edit *~/.bashrc* file, it
is not automatically loaded. To enforce loading without reopening another 
terminal window, just type ``source ~/.bashrc``.

When we logout, commands in the *~/.bashlogout* file are executed.

# Setting Command Aliases

*alias* command shows us the list of currently set alias. To set an alias for
a command;
```
alias ll='ls -la'
```
You can set an alias for any name to execute any command we want. Just be 
careful not to use an existing command name. Aliases only last for current 
session. 

If we want permanent aliases, it is suggested to put them in *~/.bashrc*,
especially with the changes in section 1 to make it work everytime.

A fine usage of using aliases is preventing your typos with defining aliases. 
For example, if you type *pdw* instead of *pwd* most of the times, just define
``alias pdw=pwd``.

# Setting and Exporting Environment Variable

To return an environment variable's value, type ``$VAR_NAME``. To set an 
environment variable's value, type ``$VAR_NAME=<value>``.

Like aliases, setting environment variables are also temporary for the session.
You can put them into the *~/.bashrc* file to make environment variable setting
permanent. With this way, environment variables are visible to bash only, not 
to the processes started by bash. To make environment variables available to 
child processes, after defining them, add export <VAR_NAME> command.
```
MYNAME='Mehmet Cagri Kose'
export MYNAME
```

Environment variables are also used in a manner same as aliases, to force 
commands use some options when they are run. The example below also shows how
to define an environment variable and to export them in the same line;
```
# Maximum verbose option for less command
export LESS='-M'
```

# Setting Path Variable

PATH is a colon delimited list of file paths that Unix uses when it's trying to
locate a commmand that you want it to run. If you empty the PATH, Linux will 
not be able to locate and execute any command, because it does not know where 
to look. In that case, if you know the path of the command you can use it like;
```
/usr/bin/less lorem_ipsum.txt
```

You can modify the PATH to;
* remove a directory from the list to ignore it.
* add a directory you plan to put commands into.
* order of the paths, so you can prioritize paths between each other.

You can amend or append the current PATH easily by using $PATH;
```
# Use double quotes to grab the value of variable 
export PATH="/user/local/bin:$PATH"
export PATH="$PATH:/user/local/sbin"
```

# Configuring History with Variables

There are some environment variables that are used to configure history;
* HISTSIZE=<number>: Up to how many commands will be kept in history
* HISTFILESIZE=<number>: Up to how many kilobytes will history file size will be
* HISTCONTROL=[ignoredups,ignorespace,ignoreboth]: Ignores duplicate commands
(repeating-same) or commands starting with space. The latter is used especially
to hide a command from history like the ones including password etc.
* HISTIGNORE="command1:command2": Ignore a list of commands delimited by colon.
* HISTTIMEFORMAT='%b %d %I:%M %p': Try and see history format.

# Customizing the Command Prompt

You can configure the command prompt by setting ``PS1`` with formatting codes;

* \u: username
* \s: current shell
* \w: current working directory
* \W: name of the current folder

The list goes on and on, it is better for reader to check other formatting 
codes.

# Logout File

*~/.bash_logout* file houses the commands we want to run when we logout the 
terminal by typing ``exit`` command. These commands are not run when you close
the terminal window by other means.
