# Introduction

## Archive Files

**.tar** extension indicates that whatever comes before it is packaged into a
tape archive, referring to old storage method. It is a popular packaging method
in the Linux community. **.gz** means it is compressed. It stands for GNU zip.

**tar** command is used for handling tar balls(nickname for tar archives.)
```
tar -zxvf some_file.tar.gz
# z: unzip 
# x: extract the files
# v: verbose(more output)
# f: use the file given in the argument
```

## Python

We can use **virtualenv** to isolate multiple python environments. It is not 
really far from the philosophy of containers. This is great for doing 
experiments(Author's note: Anything that empowers the developer is great).

To setup virtual environment in your computer;

```
# Install virtual environment
$ sudo apt-get install python-virtualenv

# Change to the directory you want to create virtual environments
$ cd /var/some\_dir

# Create a virtual environment with any name you desire
$ virtualenv venv

# You can select which python version to use withing your virtual environment.
$ virtualenv -p /user/bin/python2.7 venv

# Activate the virtual environment. Run the command from the directory that 
# includes the virtual environment directory you just created(some\_dir).
$ . /venv/bin/activate


# Confirm that after running the command above, command prompt has (venv) prefix
(venv) pi@raspberrypi:/var/some\_dir $ 

# To deactivate. Confirm that you lost venv prefix after deactivating.
$ deactivate
```

Virtual environment will be created that can contain all executables needed for
a python project and also a copy of **pip** to install packages. When you are 
in an activated virtual environment(confirm by virtual environment name at the 
start of command prompt) pip will install packages only for this virtual 
environment.

## Raspberry Pi Pin Controls With Python

You can use two methods to refer to the pins inside your python scripts

1. GPIO or BroadComm way: Just count the pins from the start, you do not need
reference manual with this way.
2. BCM(BroadComm System On a Chip) way: Hard to memorize or find out without a
guide.

After deciding the method, make the proper setup at the start of your script.
```
import RPi.GPIO as GPIO

# for BroadComm SOC method
GPIO.setmode(GPIO.BCM)

# For physical numbering(GPIO or BroadComm way)
GPIO.setmode(GPIO.BOARD)

# Set the pin as output or input
GPIO.setup(pin_number, [GPIO.OUT/GPIO.IN])

# Read the input level at the input pin
if GPIO.input(pin_number):

# Control the output level of the output pin
GPIO.output(pin_number, [GPIO.HIGH/GPIO.LOW])

# Clean up: Revert all pins to their default states
GPIO.cleanup()
```

Long pin of the LEDs will be connected to GPIO pins or any other positive 
potential source. And short leg will be connected to the ground or lesser
potantial source.

