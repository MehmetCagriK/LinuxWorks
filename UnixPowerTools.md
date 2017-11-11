# grep: Searching For Matching Pattern

**grep** stands for global regular expression print. This command outputs all
lines that matching a regular expression. Regular expressions are created for
Unix.

Let's see simple usage of grep and couple options;
* grep apple fruit.txt: Search the file for lines matching "apple"
* grep -i: Case insensitive match.
* grep -v: Inverse match, outputs the line not matching.
* grep -w: Matches whole words.
* grep -c: Outputs match count.
* grep -n: Print the line number before lines.

To demonstrate the effects of options above, check the output below;
```
$ grep apple fruit.txt 
apple
pineapple
apple


$ grep -i Apple fruit.txt 
apple
pineapple
apple

$ grep -w apple fruit.txt 
apple
apple

$ grep -wn apple fruit.txt 
5:apple
13:apple

$ grep -c apple fruit.txt 
3

```
# grep Multiple Files

We can grep whole directories like below;

* -R is for recursive
```
$ grep -Rn apple .
./fruit.txt:5:apple
./fruit.txt:6:pineapple
./fruit.txt:13:apple
./unique_sorted_fruit.txt:1:apple
./unique_sorted_fruit.txt:7:pineapple
./sorted_fruit.txt:1:apple
./sorted_fruit.txt:2:apple
./sorted_fruit.txt:9:pineapple
```
* -h is to print matching lines without filenames
```
$ grep -Rh apple .
apple
pineapple
apple
apple
pineapple
apple
apple
pineapple
```

* -l is to print filenames that have matching lines only
```
$ grep -Rl apple .
./fruit.txt
./unique_sorted_fruit.txt
./sorted_fruit.txt
```

* -L is to print filenames that have not matching lines
```
$ grep -RL apple .
./.DS_Store
./new_file.txt
./lorem_ipsum.txt
./overwrite_test2.txt
./calculation.txt
./joined.txt
./dir_content.txt
./people.txt
./recent_history.txt
./newer_file.txt
./hello_world.txt
./short_file.txt
./ownership.txt
```

* You can also narrow down target files by using wildcard expressions in names
```
$ grep -R apple ./\*fruit.txt
./fruit.txt:apple
./fruit.txt:pineapple
./fruit.txt:apple
./sorted_fruit.txt:apple
./sorted_fruit.txt:apple
./sorted_fruit.txt:pineapple
./unique_sorted_fruit.txt:apple
./unique_sorted_fruit.txt:pineapple

```
You can also use powerful function of piping command outputs into grep input.
```
# Run history command first, then pipe its output into grep for "history"
$ history | grep history
    2  history
   62  history | grep history
```

# grep: Coloring the Output

``--color`` option can be used to color the matching patterns. 
* --color=always: Puts special characters around matching patterns, so bash 
will know what to color
* --color?auto: Since color tampers with the matching words, piping output of
grep to somewhere can be risky. Auto does not color when output is 
piped-directed out somewhere.

# Introduction to Regular Expressions

When using regex, it is a good practice to put single quotes around the regex 
patterns because, some of the regex special characters mean something to Unix.

* .: Single wildcard character
* \*: Preceeding element can occur zero or more times.
* +: Preceeding element can occur one or more times. 'Extended RE'
* ?: Preceeding element can occur zero or one times. 'Extended RE'
* |: OR operator. 'Extended RE'
* [abc]: Either a, b or c. Single match.
* [^abc]: Match any character that is not a, b or c.
* A-Z: From A to Z
* a-z: From a to z
* (jpg|gif|png): Match either jpg, gif or png.
* ^Hello: Start of the line anchor.
* end$: End of line anchor.
* 0-9: From 0 to 9

Note: +, ? and | belongs to extended regular expression. Use -E with grep to use
E.R.E. .

# Translating Characters


