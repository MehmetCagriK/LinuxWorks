# Standard Input and Standard Output

* stdin(Standard Input): Refers to the keyboard. The **main** way of giving 
input to the terminal. /dev/stdin is special file for standard input.
* stdout(Standard Output): Refers to the text windows inside terminal. The
**main** way of getting output from terminal. /dev/stdout is the special file
for standard output.

# Directing Output to A File

You can output of a command directly to a file by using right angle(>) after
command and giving filename. File will be created if it does not exist or will
be overwritten if exists. Right angle means instead of directing the output of
the command into the screen, direct the output to the file. A few use cases;

* echo "bla bla" > bla.txt: Writes "bla bla" into bla.txt
* cat bla.txt bla.txt > blabla.txt: Concatenates bla.txt with itself and writes
into blabla.txt file.

# Appending to a File

Use >> to append to the file instead of overwriting the content. Usage is;
```
cat new_file.txt >> old_file.txt
echo "end of file" >> file.txt
```

# Directing Input from A File

To direct input from a file, use left angle (<).

```
echo "2+3" > calc.txt
bc < calc.txt
5
```

Left angle means use the file on the right side of left angle as an **input**.

# Piping Output to an Input

Use | to pipe output of a command as input to another command.

```
echo "Hello world" | wc
1     2      12

echo "(2*4)" | bc
8

cat fruit.txt | sort | uniq
apple
pear
cranberries
```  

You can also direct output of piping into a file.
```
cat fruit.txt | sort | uniq > sorted_uniq_fruit.txt
echo sorted_uniq_fruit.txt
apple 
cranberries
pear
```

# Suppressing Output

```
echo "blabla" > /dev/null
```

Anything directed into /dev/null is lost.
