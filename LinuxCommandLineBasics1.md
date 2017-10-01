### Command Line Interfaces

They generally work as

1. User types a command
2. System runs those commands
3. They system displays the output

Advantages of using command line interfaces.

1. A CLI(Command Line Interface) is programmable.
2. It is efficient in terms of network bandwidth.
3. You can use terminal edit files in distant system without having copying it 
   into local system.

### Virtual Machine
Virtual machines are softwares; that simulate a computer. The operating system
installed on your physical computer is called host OS(in my case, it was 
Windows 10) and operating system installed on virtual machine is called guest 
OS.

Virtual machines are used for;

1. Ensuring all developers work on identical environment with correct programs
are installed and correct configurations are done
2. Isolating programming projects from everything else on programmer's computer.
The user can configure their guest OS without disrupting their regular OS
3. Simulate environments that software will be deployed to.

#### Vagrant

Vagrant is a program that makes VMs more convenient to use. With it, you can 
automatically configure your Virtual Machine installation and configuration
by following the instructions in the __Vagrantfile__.

Instead of using a software program with a more standard visual user interface,
many programmers use CLIs for their flexibility.

After installing Vagrant and VirtualBox into your computer, do the followings;

1. Open the terminal
2. Change to a directory you want to work with(arbitrary)
3. Create a Vagrantfile or download a sample
4. Type ``vargant up`` and enjoy the rest. 
