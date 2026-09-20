# Passwords
## Problem with Passwords
- What happens when a password is stored as is? 
	- If the database is hacked, the hacker gets hold of all the passwords 
	- People reuse passwords
## Solution is Using Cryptographic Hashes
- **~={cyan}Store the hash=~**, not the **password.**
- Hash functions can also give fixed length outputs from arbitrarily long input.
## Breaking hashes
- Cryptographic hashes are **~={yellow}efficient and are designed to be efficient=~**

# Introduction to System Security Essentials
## Operating Systems
- most users use windows/Linux/OSX  | Android / IOS
- why do we need a os
- can't we directly open an application
## Memory Access
- we can run multiple apps at the same time within our OS
- most application access store and retrieve information to and from the physical memory.
## Libraries
- are mechanism made by dev which can help as share code.
- otherwise devs will have to write everything from scratch.

## More of OS.
### X86 Computer Architecture
- Northbridge
	- connects mem, graphics and cpu together
- Southbridge
	- connects i/o devices

- In modern systems, northbridge is integrated within the CPU. 
### Concurrency
- We can run multiple apps at the same time
- running all those program needs CPU, hard disk, mem.
- we use device drivers and system api to manage them.
### Process, Virtual Memory and Files
- os provides abstraction for the resources like convenient API,
	- Files are abstraction for I/O.
	- Virtual mem are abs for physical mem and I/O.
	- Process are abstraction for CPU, physical mem and I/O.

- OS allow apps to use these API so that they can access hardware.

## Processes
- its a abstraction provides by the OS for running programs
	- The mem, CPU state and I/O information all together runs as a process.

- With process one could
	- **Create**
	- **Destroy**
	- **control other mechanism using process.**
	- **get status of the process**
	- **wait for process to complete**

### Process in Memory
- it has 3 things
	- **code** and **static data** is loaded into mem.
	- **stack** which is used for function parameters, local variables.
	- **Heap** is used for dynamic memory management

	- Both **heap** and **stack** shrinks or grows based on the program execution.
### Process states
- During the execution of the program it can switch b/w states.
	- **Running**
	- **ready**
	- **Blocked**

- **Process can be suspend and then resumed.**
	- process can be blocked and suspended.
	- process can be unlocked and scheduled
## System call
### Privilege levels
- certain operation can only be done by OS
	- eg, user program can not have direct access to hardware.

- How can this be implemented use privilege level
	- OS and kernel on ring 0
	- application in ring 3
	- 1 and 2 for device drivers.

### System calls
- for privileged operation we will use system calls.
- System calls are specified using system call numbers and the corresponding function within the kernel is executed

- eg;
	- Applications request for privileged operations using system calls 
	- OS sets up trap table which stores information about the handlers 
	- Syscalls save the process state and transfer control over to the handler 
	- The state is restored, and control is given back after the syscall execution