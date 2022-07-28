# Linux

- [Linux](#linux)
  - [What is a “/proc” file system?](#what-is-a-proc-file-system)
  - [What is a Zombie Process?](#what-is-a-zombie-process)
  - [What is the load average?](#what-is-the-load-average)
  - [Commands](#commands)
    - [How do you view the files in the current directory?](#how-do-you-view-the-files-in-the-current-directory)
    - [How do you view the current kernel version?](#how-do-you-view-the-current-kernel-version)
    - [How do you view the current running processes?](#how-do-you-view-the-current-running-processes)
    - [Where are common log files located?](#where-are-common-log-files-located)
    - [How do you view available memory?](#how-do-you-view-available-memory)
    - [How do you view current CPU load?](#how-do-you-view-current-cpu-load)
    - [How do you view current disk usage](#how-do-you-view-current-disk-usage)
  - [Scenario Based Questions](#scenario-based-questions)

## What is a “/proc” file system?

- Proc file system is a pseudo or virtual file system that provides an interface to the kernel data structure. It generally includes useful information about processes that are running currently. It can also be used to change some kernel parameters at runtime or during execution. It is also regarded as a control and information center for the kernel. All files under this directory are named virtual files

## What is a Zombie Process?

- Zombie Process, also referred to as a defunct or dead process in Linux, is a process that has finished the execution, but its entry remains in the process table. It usually happens due to a lack of correspondence between parent and child processes.

## What is the load average?

- As the name suggests, is the average system load on Linux servers being calculated over a given period of time. The load average of Linux servers can be found using “top” and “uptime” commands. It is simply used to keep track of system resources. It is represented by a decimal number starting at 0.00. It tells you the load that the system has been under.
- This should be at roughly 1.0 per CPU.

## Commands

### How do you view the files in the current directory?

- `ls`

### How do you view the current kernel version?

- `uname -a`

### How do you view the current running processes?

- ps aux

### Where are common log files located?

- /var/log

### How do you view available memory?

- `free`
- `top`

### How do you view current CPU load?

- `top`

### How do you view current disk usage

- df -h
- pvdisplay
- lvdisplay
- lsblk

## Scenario Based Questions

- Sometimes they will ask scenario based questions like:
  - A developer tells you the app server is reporting a 503, how do you investigate
  - Walk through how to resolve it
    - SSH to the server
    - Use systemctl to check the service
    - Check the application logs
    - Investigate error messages
    - etc
- Be comfortable navigating around linux