# Chapter 05: System Calls (Theory and Practical)

System calls are the interface between the operating system and user programs. They allow a program to request services from the kernel, which manages the hardware and system resources. Understanding system calls is essential for working with low-level programming, system programming, and understanding how operating systems operate under the hood.

## What are System Calls?

### Theory:
- **Definition**: A system call is a mechanism that allows user-level processes to request services from the operating system's kernel. It provides a controlled entry point into the kernel, ensuring system security and stability.
- **Purpose**: System calls are used to perform a variety of tasks such as file operations, process management, communication, and more.
- **Execution Flow**: When a system call is made, the CPU switches from user mode to kernel mode to execute the requested operation, and then switches back to user mode.

### Common Types of System Calls:
1. **Process Control**:
   - `fork()`: Creates a new process.
   - `exec()`: Replaces the current process image with a new process image.
   - `exit()`: Terminates a process.
   - `wait()`: Waits for a process to finish execution.

2. **File Management**:
   - `open()`: Opens a file.
   - `read()`: Reads data from a file.
   - `write()`: Writes data to a file.
   - `close()`: Closes a file.

3. **Device Management**:
   - `ioctl()`: Manages device-specific operations.
   - `read()`, `write()`: Also used for device I/O operations.

4. **Information Maintenance**:
   - `getpid()`: Retrieves the process ID.
   - `alarm()`: Sets an alarm clock for the process.
   - `gettimeofday()`: Gets the current time.

5. **Communication**:
   - `pipe()`: Creates a communication pipe between processes.
   - `shmget()`: Allocates a shared memory segment.
   - `msgsnd()`, `msgrcv()`: Used for message passing between processes.

## Practical Aspects of System Calls

### How to Use System Calls in Programming:

