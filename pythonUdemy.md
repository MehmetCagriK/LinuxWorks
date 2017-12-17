# Introduction

## Python 2 vs Python 3

* Python 2: 
** Started in 2000
** Python 2.7 was released in 2010
** will lose support in 2020

* Python 3
** Released in 2008
** More library support

Since Python 2 is used more than Python 3 currently by a large margin **currently**,
this course will use Python 2 with Python 3 differences stated here and there.
There are multiple reasons why Python 2 is used more now;

* Dependencies
* Large base of legacy code
* Management

## IDLE

When you install Python, you can type **python**  in the terminal to open live
interpreter to quick try python commands. For more complex programming, you 
better write scripts and save them with **.py** extension.

## Python 

### Numbers in Python

We will focus on floating point numbers and integers. Only thing to mention 
here is division in Python 2 is integer division and in Python 3, it is true
division. You can circumvent this feature by casting one of the numbers of 
division operation into float by ``float(number)`` call, if you divide an
integer number with another integer number.

You can also import features of Python 3 with;
```
from __future__ import division
3 / 2 = 1.5
```

You can take a number's power with ``num**power`` syntax.

Order of operations is same as standard amongst languages. If you want to force
an order, use paranthesis. 

Python is dynamically-typed language. You can create variables by simply using
equals to sign, followed by the value.
```
# Statements below will not cause a problem.
var = 4
var = 'a'
var = "Hello"
```


