# Command Prompt

When you open a terminal window, you will see a command prompt. In Ubuntu 
format looks like below by default;
''cagri@cagri-UbuntuVB:~$''

This tells user that shell is ready to accept a command. You can enter 
command, if shell executes it correctly, shell will give another command 
prompt. There are couple shortcuts below;
 
* up and down arrows: to navigate through your command history.
* home: move cursor to the start of the line.
* tab: to autocomplete(if you typed enough characters to distinguish)
* tab tab: Will give you the list of the possible matches if single tab does
  not work 

# Command Structure:

Command structure is always the same in the form of;

''command option argument''

You can not change this order. Commands are always single words. 

Options are optional, as arguments are.Options modify the behavior in some way.
Options have hypen in front of them to give clue Unix that we are giving an
otion, not an argument.

* -v: This is a very common argument in Unix that returns the version of
  something, either a software or a command. --version does the same effect.

* We can have multiple options for same command. They can be written seperated 
by space or they can be combined together after a single dash(hyphen) as below;

'''
ls -l -a -h Desktop
ls -lah Desktop
'''

* Sometimes, options require arguments of their own. In that case, argument of
option can be typed seperately or without any character between option and its
argument as below;

'''
banner -w 50 'Hello World'
banner -w50 'Hello World'
'''

Banner takes an option -w as width of the banner, which in turn requires
argument as width.

* We can also have multiple arguments.
'''
cat file1.txt file2.txt
'''

* You can use double quotes instead of single quotes for giving arguments.

* You can put semicolons between commands to do several things at once
'''
echo'hello'; echo 'world'

# Kernel and The Shells
Kernel is the core of the OS in Unix. Doing low level operations like 
allocating time and memory to programs. Mac OS X uses Mach kernel.

And outside of that, there is the shell. It is the outer layer of OS. Shell
interacts with the user. It sends requests to the kernel, kernel does the job
and returns the output of the operation to the shell. Mac OS X uses bash shell 
by default but allows other options too. History of shell below;

1. sh  : Thommpson Shell(__1971__)
2. sh  : Bourne Shell, replaced Thompson Shell(__1977__)
3. csh : C Shell(__1979__)
4. tcsh: Tabbed C Shell(__1979__)
5. ksh : Korn Shell(__1982__)
6. bash: Bourne-Again Shell(__1987__)
7. zsh : Z Shell(__1990__)

These shells differ on tiny ways, like high end tasks(shell scripting).

Shell is not like an operating system, it is just a working environment. We can 
move between shells and even nest them inside each other. Typing **exit** will
exit the shell on top of the stack(last launched one).


# Manual Pages
Manual pages, or called man(because of the command **man** used to access them)
command will give us the manual pages for the argument you entered. It can be 
either a software or a command.

When you type ``man echo``, you will see first page of manual of the echo 
command. You can use f or space bar keys to see next page, b key to see former
page and q to quit manual. Quitting man removes the manual pages from the bash
window, so it does not crowd our view.

You can use man command with **-h** option to see what arguments you can 
provide to man command. One of the most important option is **-k**. That 
searches for the keyword given, same as apropos command. And it returns 
found commands that has the pattern in them as a list.

There is also **whatis** command. But this command directly matches the pattern
instead of searching the pattern in command manuals.




