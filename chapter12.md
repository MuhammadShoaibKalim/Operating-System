# Chapter 12: What is Convoy Effect? | FCFS CPU Scheduling Algorithm

In this chapter, we explore the Convoy Effect and the First-Come, First-Served (FCFS) CPU scheduling algorithm. These concepts are integral to understanding how processes are managed and scheduled in an operating system, and the challenges associated with different scheduling strategies.

## 1. What is the Convoy Effect?

### Definition

- **Convoy Effect** refers to a situation in CPU scheduling where a set of shorter processes is delayed by a single long process, leading to inefficiencies and increased waiting time for other processes in the queue.

### How Convoy Effect Occurs

- The Convoy Effect typically occurs in scheduling algorithms that do not preempt processes, such as FCFS (First-Come, First-Served).
- When a long-running process occupies the CPU, all subsequent shorter processes must wait for the long process to complete before they can be executed.
- This creates a "convoy" of processes stuck behind the long process, leading to higher waiting times and reduced CPU utilization.

### Example Scenario

- Consider three processes: P1, P2, and P3, arriving in this order with CPU burst times of 10ms, 2ms, and 2ms, respectively.
- Under FCFS scheduling, P1 will execute first, occupying the CPU for 10ms. During this time, P2 and P3 must wait, even though they could complete quickly if given the chance.
- The waiting time for P2 and P3 is increased significantly due to P1, demonstrating the Convoy Effect.

### Impact of the Convoy Effect

- **Increased Waiting Time**: Shorter processes wait longer, leading to inefficiencies.
- **Lower CPU Utilization**: The CPU may spend time idle if processes are waiting for I/O, reducing overall system throughput.
- **Response Time**: The overall response time for processes increases, affecting system performance, particularly in interactive systems.

## 2. FCFS (First-Come, First-Served) CPU Scheduling Algorithm

### What is FCFS?

- **First-Come, First-Served (FCFS)** is one of the simplest CPU scheduling algorithms. In FCFS, processes are scheduled in the order of their arrival, without preemption. The first process that arrives is executed first, and so on.

### Characteristics of FCFS

- **Non-Preemptive**: Once a process starts execution, it runs to completion without being interrupted.
- **FIFO Queue**: Processes are maintained in a first-in, first-out (FIFO) queue. The process at the front of the queue is given CPU time.
- **Simple and Easy to Implement**: FCFS is straightforward to implement, requiring minimal system overhead.

### How FCFS Works

1. **Process Arrival**: Processes arrive in the queue in the order they are submitted to the CPU scheduler.
2. **Execution Order**: The CPU scheduler selects the process at the front of the queue and assigns CPU time to it.
3. **Completion**: Once the process completes execution, it is removed from the queue, and the next process in line is selected.

### Advantages of FCFS

- **Fairness**: Every process gets a turn based on its arrival order, ensuring that no process is starved of CPU time.
- **Simplicity**: Easy to understand and implement, with minimal overhead in managing the process queue.

### Disadvantages of FCFS

- **Convoy Effect**: As discussed, long processes can delay shorter ones, leading to inefficiencies.
- **Non-Optimal Turnaround Time**: The average turnaround time can be high, particularly in systems with processes of varying lengths.
- **Lack of Prioritization**: FCFS does not consider process priorities, leading to potentially inefficient scheduling in multi-user or real-time systems.

### Example of FCFS Scheduling

Consider the following processes arriving in the order:

| Process | Arrival Time | Burst Time |
|---------|--------------|------------|
| P1      | 0            | 5          |
| P2      | 1            | 3          |
| P3      | 2            | 8          |
| P4      | 3            | 6          |

- **Execution Order**: P1 → P2 → P3 → P4
- **Completion Time**:
  - P1 finishes at time 5
  - P2 finishes at time 8 (waited for P1 to complete)
  - P3 finishes at time 16 (waited for P2 to complete)
  - P4 finishes at time 22 (waited for P3 to complete)

### Calculating Metrics in FCFS

- **Waiting Time**: Time a process spends waiting in the queue.
  - P1: 0, P2: 4, P3: 6, P4: 10
  - Average Waiting Time = (0 + 4 + 6 + 10) / 4 = 5 ms
- **Turnaround Time**: Total time taken from submission to completion.
  - P1: 5, P2: 8, P3: 16, P4: 22
  - Average Turnaround Time = (5 + 8 + 16 + 22) / 4 = 12.75 ms

## Conclusion

The Convoy Effect and FCFS scheduling algorithm highlight some of the challenges in process scheduling. While FCFS is simple and fair, it can lead to inefficiencies like the Convoy Effect, where shorter processes are delayed by longer ones. Understanding these concepts
