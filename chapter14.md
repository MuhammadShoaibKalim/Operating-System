# Chapter 14: Multilevel Queue Scheduling Algorithm | MLFQ | Comparison of CPU Scheduling Algorithms

In this chapter, we explore advanced CPU scheduling techniques such as the Multilevel Queue Scheduling Algorithm and Multilevel Feedback Queue (MLFQ). These algorithms are designed to handle different types of processes with varying priorities. Additionally, we will compare different CPU scheduling algorithms to understand their strengths and weaknesses.

## 1. Multilevel Queue Scheduling Algorithm

### What is Multilevel Queue Scheduling?

- **Multilevel Queue Scheduling** is a CPU scheduling algorithm that divides the ready queue into multiple queues based on specific criteria, such as process type, priority, or memory size. Each queue has its own scheduling algorithm, and processes are permanently assigned to a queue based on their attributes.

### Key Characteristics

- **Queue Hierarchy**: The ready queue is divided into multiple levels, each with its own scheduling algorithm.
- **Fixed Queue Assignment**: Once a process is assigned to a queue, it remains there until completion.
- **Scheduling Algorithms**: Different queues can use different scheduling algorithms, such as FCFS, SJF, or Round Robin.

### Example of Multilevel Queue Scheduling

Consider a system with three queues:

1. **System Processes**: Highest priority, scheduled using FCFS.
2. **Interactive Processes**: Medium priority, scheduled using Round Robin.
3. **Batch Processes**: Lowest priority, scheduled using SJF.

Processes are placed into these queues based on their type. System processes are always given CPU time first, followed by interactive processes, and finally, batch processes.

### Advantages

- **Separation of Concerns**: Different types of processes can be handled separately, optimizing scheduling for each type.
- **Priority Management**: High-priority processes are handled more quickly, ensuring critical tasks are not delayed.

### Disadvantages

- **Starvation**: Lower-priority queues may suffer from starvation if higher-priority queues are always busy.
- **Inflexibility**: Processes are fixed in their assigned queue, which may not always be optimal as the process characteristics change.

## 2. Multilevel Feedback Queue (MLFQ)

### What is MLFQ?

- **Multilevel Feedback Queue (MLFQ)** is an advanced version of the Multilevel Queue Scheduling Algorithm, where processes can move between queues based on their behavior and CPU burst characteristics. This dynamic adjustment aims to optimize scheduling by adapting to the needs of different processes.

### Key Characteristics

- **Dynamic Queue Assignment**: Processes can move between queues based on their recent CPU usage or wait time.
- **Aging Mechanism**: Processes that wait too long in a lower-priority queue may be moved to a higher-priority queue to prevent starvation.
- **Feedback Mechanism**: If a process uses too much CPU time, it may be moved to a lower-priority queue.

### How MLFQ Works

1. **Multiple Queues**: Similar to the Multilevel Queue, MLFQ has multiple queues with different priority levels.
2. **Initial Placement**: A new process starts in the highest priority queue.
3. **Execution and Feedback**:
   - If the process uses its entire time slice in the current queue, it is moved to a lower-priority queue.
   - If the process finishes quickly, it remains in the same queue or is moved up.
4. **Preemption**: A process in a lower-priority queue can be preempted by a process in a higher-priority queue.

### Example of MLFQ

Consider an MLFQ system with three queues:

1. **Queue 1**: Highest priority, Round Robin with a time quantum of 5ms.
2. **Queue 2**: Medium priority, Round Robin with a time quantum of 10ms.
3. **Queue 3**: Lowest priority, FCFS.

Processes start in Queue 1. If a process exceeds its time quantum, it is moved to Queue 2, and so on. If a process in Queue 3 waits too long, it may be moved to Queue 2.

### Advantages

- **Flexibility**: Processes are dynamically adjusted based on their behavior, improving overall system performance.
- **Prevention of Starvation**: Aging mechanisms ensure that lower-priority processes eventually get CPU time.

### Disadvantages

- **Complexity**: MLFQ is more complex to implement and manage compared to simpler scheduling algorithms.
- **Overhead**: The frequent movement of processes between queues can introduce scheduling overhead.

## 3. Comparison of CPU Scheduling Algorithms

### FCFS (First-Come, First-Served)

- **Advantages**: Simple to implement, fair in terms of arrival time.
- **Disadvantages**: Convoy effect, non-preemptive, can lead to long waiting times.

### SJF (Shortest Job First)

- **Advantages**: Optimal average waiting time.
- **Disadvantages**: Starvation of longer processes, requires knowledge of CPU burst time.

### Round Robin

- **Advantages**: Fair, good for time-sharing systems, responsive.
- **Disadvantages**: Context switching overhead, time quantum selection is critical.

### Priority Scheduling

- **Advantages**: Prioritizes critical processes.
- **Disadvantages**: Starvation of lower-priority processes, aging required to prevent starvation.

### Multilevel Queue

- **Advantages**: Handles different types of processes separately, good for systems with diverse workloads.
- **Disadvantages**: Inflexibility, potential starvation.

### MLFQ (Multilevel Feedback Queue)

- **Advantages**: Dynamic, prevents starvation, adapts to process behavior.
- **Disadvantages**: Complex to implement, requires careful tuning of parameters.

## Conclusion

The Multilevel Queue and Multilevel Feedback Queue (MLFQ) scheduling algorithms provide sophisticated methods for managing diverse process workloads in modern operating systems. While Multilevel Queue scheduling offers clear separation of process types, MLFQ introduces dynamic feedback mechanisms that enhance flexibility and responsiveness. Understanding these algorithms, along with the strengths and weaknesses of different scheduling approaches, is essential for optimizing CPU utilization and ensuring efficient process management in various computing environments.
