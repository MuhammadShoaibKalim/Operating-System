# Chapter 11: Context Switching | Medium Term Scheduling | Orphan/Zombie Process

In this chapter, we delve into key concepts related to process management in an operating system: Context Switching, Medium Term Scheduling, and the specifics of Orphan and Zombie Processes. These concepts are essential for understanding how an OS efficiently manages multiple processes and maintains system stability.

## 1. Context Switching

### What is Context Switching?

- **Context Switching** is the process of saving the state of a currently running process and restoring the state of another process so that it can resume execution. This enables multitasking, allowing multiple processes to share a single CPU efficiently.

### Steps Involved in Context Switching:

1. **Save the State**: The current state (context) of the running process is saved into its Process Control Block (PCB). This includes the CPU registers, program counter, and other process-specific data.

2. **Switch the Process**: The OS updates its process management data structures to reflect the change in which process is currently running.

3. **Restore the State**: The state of the new process to be executed is loaded from its PCB into the CPU registers and program counter.

4. **Resume Execution**: The new process resumes execution from where it was paused.

### Overheads of Context Switching:

- **Time Consumption**: Context switching is a relatively expensive operation because it involves saving and loading multiple registers and memory states.
- **Performance Impact**: Frequent context switching can degrade system performance due to the time spent on the switch itself rather than on productive execution.

### Context Switching Scenarios:

- **Preemptive Multitasking**: When the OS preempts a running process to switch to another process, often due to a higher-priority process needing CPU time.
- **I/O Operations**: When a process is waiting for I/O, the OS can switch to another process that is ready to run.

## 2. Medium Term Scheduling

### What is Medium Term Scheduling?

- **Medium Term Scheduling** is the process of temporarily removing (or suspending) a process from main memory and placing it into secondary storage (like a hard disk) to free up memory for other processes. This process is also known as **swapping**.

### Purpose of Medium Term Scheduling:

- **Memory Management**: To manage limited RAM resources effectively, especially when running multiple processes that exceed available physical memory.
- **Improve System Responsiveness**: By suspending less critical processes, the OS can allocate more resources to high-priority or active processes.

### Steps in Medium Term Scheduling:

1. **Identify Candidates for Swapping**: The OS identifies processes that are idle or have low priority, making them candidates for swapping out of main memory.
2. **Save Process State**: The state of the process is saved to disk, including its memory image and PCB.
3. **Swap Out**: The process is moved to secondary storage, and the OS updates its data structures to reflect the process's new state.
4. **Swap In**: When the process is ready to resume, it is loaded back into main memory from secondary storage, and execution resumes from where it was paused.

### Trade-offs:

- **Performance Impact**: Swapping processes in and out of secondary storage can introduce latency, especially if the storage device is slow.
- **Memory Optimization**: Helps in optimizing the use of limited main memory, enabling the system to handle more processes concurrently.

## 3. Orphan and Zombie Processes

### Orphan Process

- **Definition**: An **Orphan Process** is a process whose parent has terminated or exited, leaving it without a parent process to monitor or manage it.
  
- **Adoption by Init Process**: In UNIX-like operating systems, orphan processes are adopted by the init process (PID 1), which becomes their new parent. This adoption ensures that the orphaned process can still complete its execution properly.

- **Handling Orphans**: The OS ensures that orphan processes do not disrupt system stability by adopting them into a system process like init, which can then handle their termination and cleanup.

### Zombie Process

- **Definition**: A **Zombie Process** is a process that has completed execution but still has an entry in the process table. This entry remains because the process’s parent has not yet read the exit status of the process.

- **Characteristics**:
  - The process has released its resources (memory, file descriptors) but retains its PCB in the process table.
  - It remains in this state until the parent process retrieves its exit status using system calls like `wait()`.

- **Why Zombies Occur**: Zombie processes occur because the OS needs to store the exit status of the process so that the parent process can read it. If the parent process does not read the status, the zombie persists.

- **Handling Zombies**:
  - **Reaping**: The parent process is responsible for calling `wait()` to retrieve the exit status, allowing the OS to remove the zombie process from the process table.
  - **Killing Parent**: In some cases, if the parent process is killed, the init process will adopt the zombie, allowing it to be reaped and removed.

### Differences Between Orphan and Zombie Processes:

- **Orphan Process**: Still active and executing, but without a parent. It is adopted by the init process.
- **Zombie Process**: No longer active; it has completed execution but remains in the process table waiting for its parent to read its exit status.

## Conclusion

Context Switching, Medium Term Scheduling, and the management of Orphan and Zombie processes are critical aspects of an operating system’s process management functionality. They ensure efficient CPU utilization, effective memory management, and proper cleanup of processes, contributing to overall system stability and performance.
