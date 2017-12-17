#Introduction

Although standard linux distributions can be used for embedded systems, however 
doing this is contradictory to the nature of the embedded systems. Standard 
distributions require much more resource, runs too many processes, are hard to
manage and are far too complex than needed generally.

Project specific embedded linux distribution is a good solution for the problems
above. However, this method also has some disadvantages compared to standard 
distributions.

* Development and testing will take longer
* Needs more experienced personnel to handle boot loader, kernel and file system
compiling and setup
* Distribution will be hardware specific generally and when the underlying 
hardware changes, distribution shall be updated also.

Project specific distribution will require less resource.

All embedded Linux systems stand on these 4 elements

1. Boot loader
2. Linux Kernel
3. Root file system
4. Boot scripts

All these elements shall be handled manually to be more efficient and effective.

The main difference between various embedded systems is the location of the 
kernel and root file system. Kernel itself can be located on the MMC, SD Card,
USB Memory etc. Kernel can be loaded directly, over network or over serial 
connection. 

Root file system is the file system Kernel binds to when it is up. Root file 
system can also be anywhere, or even be embedded into the kernel. Kernel chooses
a mounting method depending of the location itself.

Boot loader on the other hand, can reside inside the device itself. There are 
many bootloaders nowadays and the most popular one for ARM systems is 
**u-boot.**

All these four elements including boot scripts make the system itself. The 
kernel and the root file system makes up the characteristic of the system. On
Raspberry Pi and Beagle Bone Black, the kernel and the root file system are both
located on the SD Card or MMC.

# Initramfs Supported Embedded System

These systems are one of the simplest embedded systems. The kernel is located on
the network and the root file system.

Initframs consists of creating root file system in the RAM and the having the 
kernel bind the root file system. Initramfs is set and bound at the startup.

With initframfs, the root file system might be embedded into the kernel or not.

Initframs is applied to make preparations before the kernel binding the root 
file system.

In this class;

1. u-boot, kernel and rootfs will be compiled and set up from the start
2. u-boot will be loaded from SD Card
3. with tftp, the kernel and the rootfs will be loaded from network
4. login will be completed

## Boot Loader

In this class, u-boot will be used. u-boot is developed with GPL license and is
defacto standard for the ARM devices.

u-boot consists of 2 main programs. First one is MasterLoader(MLO). MLO is a 
small and simple code piece. It can not run whole system up itself. It can be
loaded and started from a program within the ROM.

MLO allocates necessary addresses for second stage boot loader and raises the
peripherals. u-boot.bin is the second stage boot loader(also the main one) is 
loaded by MLO.

Second stage boot loaders have many capabilities, they can load kernel, dtb and
rootfs from the network or local devices. u-boot system is specific for each 
board. Not every command may be used in another board.

For all u-boot supported startup, there are three main programs, MLO, u-boot.bin
and mkimage which supports u-boot.bin. u-boot.bin requires a 64 bit header for 
each file that it will work on and mkimage prepares the files that will be 
worked on by the u-boot.bin. These headers include kernel address in RAM, 
control bytes etc.

To be able to start the board(Raspberry Pi), we will need MasterLoader, 
u-boot.bin and mkimage programs.

In the following sections, we will take the actions below;

1. Cross-compiler will be installed.
2. U-Boot's source code will be downloaded.
3. U-Boot's source code will be compiled with cross-compiler and MasterLoader,
u-boot.bin and mkimage programs will be created.
4. SD card will be paritioned with fdisk and file system will be created.
5. U-Boot programs and u-boot environment variables will be copied to the 
filesystem. 
6. System will be started and tests will be run at u-boot level.

### Cross-Compiler

Cross-compilers are programs that create code for different processor 
architecture than the native one. For example, I will be developing source
code on Ubuntu VirtualBox that runs on 64 bit processor and will compile it
for Raspberry Pi 3 which has 64 bit ARM processor.

Native compiler in Raspberry Pi creates executables for ARM processor. But 
developing on target computer(if possible) has some disadvantages;

1. Raspberry has limited resources compared to a desktop computer. Simple tasks
can be exhausting when developing a program on it.
2. Target computers shall be as clean as possible and installing development 
tools on them is contradictory. Especially for this cource, we will not use
standard distributions on the target computers so it will be extra difficult
to create a development environment on target

Compiler by itself is not enough to develop programs. We also need programs 
like debugger, linker, dump. All of these programs form the  **toolchain**.
Simplified story of a program proceeds like this;

1. Source code is compiled and object code is created.
2. Object code is linked together with linker and executable code is created.
3. Executable code gets debugged.

All of these operations look like a ring of chain, hence the name toolchain.
For Raspberry Pi,I used Linaro's toolchain for Raspberry Pi. It can be installed
by following the instructions below;
```
# Download the toolchain from linaro's website
$ wget https://releases.linaro.org/components/toolchain/binaries/latest/arm-linu
x-gnueabihf/gcc-linaro-7.1.1-2017.08-x86_64_arm-linux-gnueabihf.tar.xz

# Extract the archive
tar -Jxf gcc-linaro-7.1.1-2017.08-x86_64_arm-linux-gnueabihf.tar.xz 

# For simplicity, rename the directory name to a simpler one
mv gcc-linaro-7.1.1-2017.08-x86_64_arm-linux-gnueabihf toolchain

# To differentiate cross-compiler from native one, create an environment var.
export CC=~/raspberry/toolchain/bin/arm-linux-gnueabihf-gcc

# Check if you properly set the environment variable with version command
$ $CC --version
arm-linux-gnueabihf-gcc (Linaro GCC 7.1-2017.08) 7.1.1 20170707
Copyright (C) 2017 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

You can create a simple _hello.c_ and cross-compile it with 
``$CC hello.c -o hello``. 

### Downloading U-Boot

Now we can create MasterLoader, u-boot.bin and mkimage by compiling u-boot.






