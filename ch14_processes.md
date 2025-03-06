# Chapter 14 - Processes

## Program
A program is a set of instructions, along with any internal data used while carrying the instructions out. Programs may also use external data. 
Internal data might include text strings inside the program, which are used to display user prompts. External data might include data from a database. 
Programs may consist of machine level instructions run directly by a CPU or a list of commands to be interpreted by another program. 
Programmers use various languages (such as C, C++, Perl, and many more) to code instructions in a program.

Many user commands, such as ls, cat and rm are programs which are external to the operating system kernel, or shell (in other words, they have their own executable program on disk).

## What is a process?

*What Is a Process?*
A **process** is an instance of a program in execution. It may be in a number of different states, such as running or sleeping.

- Linux creates a new process for every program that is executed or run
- Several processes may be executing the same program at the same time
- The primary purpose of the operating system is to manage the execution of processes on behalf of users

Process Attributes:
- The program being executed
- Context (state): a snapshot of itself by trapping the state of its CPU registers, where it is executing in the program, what is in the process' memory, and other information
- Permissions
- Associated resources

## Process Resource Isolation

When a process is started, it is isolated in its own user space to protect it from other processes. This promotes security and creates greater stability.

Processes do not have direct access to hardware. Hardware is managed by the kernel, so a process must use system calls to indirectly access hardware. 
System calls are the fundamental interface between an application and the kernel.

## Ulimit

ulimit is a built-in bash command that displays or resets process resource limits

A system administrator may need to change some of these values in either direction:

- To restrict capabilities so an individual user and/or process cannot exhaust system resources, such as memory, cpu time or the maximum number of processes on the system.
- To expand capabilities so a process does not run into resource limits; for example, a server handling many clients may find that the default of 1024 open files makes its work impossible to perform.

ou can set any particular limit by running the following command:

**$ ulimit [options] [limit]**

as in

**$ ulimit -n 1600**

which would increase the maximum number of file descriptors to 1600.

## Creating Processes

An average Linux system is always creating new processes. This is often called forking; the original parent process keeps running, while the new child process starts.

Often, rather than just a fork, one follows it with an exec, where the parent process terminates, and the child process inherits the process ID of the parent. 
The term fork and exec is used so often, people think of it sometimes as one word.

## Creating Processes in Command Shell (Bash)

When a user executes a command in a command shell interpreter, such as bash, the following takes place:

- A new process is created (forked from the user's login shell)
- A wait system call puts the parent shell process to sleep
- The command is loaded onto the child process's space via the exec system call, replacing bash
- The command completes executing, and the child process dies via the exit system call
- The parent shell is re-awakened by the death of the child process and proceeds to issue a new shell prompt
- The parent shell then waits for the next command request from the user, at which time the cycle will be repeated.

## Managing Jobs

**$ jobs**
1 -  Running    updatedb &
2 +  Stopped    sleep 10

Job IDs can be used with bg and fg.

The command:

**$ jobs -l**

will provide the PID for the job.

## Process State

Processes can be in one of four states:

- Running
- Waiting (Sleeping)
- Stopped
- Zombie

## Daemons

Daemons
A daemon process is a background process whose sole purpose is to provide some specific service to users of the system. Here are some more information about daemons:

- They can be quite efficient because they only operate when needed
- Many daemons are started at boot time
- Daemon names often (but not always) end with d, e.g. httpd and systemd-udevd
- Daemons may respond to external events (systemd-udevd) or elapsed time (crond)
- Daemons generally have no controlling terminal and no standard input/output devices
- Daemons sometimes provide better security control
- Some examples include xinetd, httpd, lpd, and vsftpd

## Process Monitoring

### Process Monitoring Tools

To monitor processes, Linux administrators make use of many utilities, such as ps, pstree and top, all of which have long histories in UNIX-like operating systems.

Here is a list of some of the main tools for process monitoring.

| Tool | Purpose |
|-----|--------|
|**top**|	Process activity, dynamically updated|
|**uptime**|	How long the system is running and the average load|
|**ps**|	Detailed information about processes|
|**pstree**|	A tree of processes and their connections|
|**mpstat**|	Multiple processor usage|
|**iostat**|	CPU utilization and I/O statistics|
|**sar**|	Display and collect information about system activity|
|**numastat**|	Information about NUMA (Non-Uniform Memory Architecture)|
|**strace**|	Information about all system calls a process makes|

### Basic Troubleshooting Methods

- Characterize the problem
- Reproduce the problem
- Always try the easy things first
- Eliminate possible causes one at a time
- Change only one thing at a time; if that does not fix the problem, change it back
- Check the system logs (/var/log/messages, /var/log/secure, etc.) for further information

### Viewing Process States with ps

To see every process on the system using standard syntax:
          ps -e
          ps -ef
          ps -eF
          ps -ely

       To see every process on the system using BSD syntax:
          ps ax
          ps axu

       To print a process tree:
          ps -ejH
          ps axjf

       To get info about threads:
          ps -eLf
          ps axms

       To get security info:
          ps -eo euser,ruser,suser,fuser,f,comm,label
          ps axZ
          ps -eM

	   To see every process running as root (real & effective ID) in user format:
          ps -U root -u root u

       To see every process with a user-defined format:
          ps -eo pid,tid,class,rtprio,ni,pri,psr,pcpu,stat,wchan:14,comm
          ps axo stat,euid,ruid,tty,tpgid,sess,pgrp,ppid,pid,pcpu,comm
          ps -Ao pid,tt,user,fname,tmout,f,wchan

       Print only the process IDs of syslogd:
          ps -C syslogd -o pid=

       Print only the name of PID 42:
          ps -q 42 -o comm=
		  
### Customizing the ps output

Using the -o option, followed by a comma-separated list of field identifiers, allows the user to print out a selected list of ps fields:

- pid: Process ID
- uid: User ID of process owner
- cmd: Command with all arguments
- cputime: Cumulative CPU time
- pmem: Ratio of the process's resident set size to the physical memory on the machine, expressed as a percentage

