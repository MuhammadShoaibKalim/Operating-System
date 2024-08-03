# Chapter 13: Shortest Job First (SJF) Priority Algorithm | Round Robin Scheduling Algorithm

In this chapter, we discuss two important CPU scheduling algorithms: the Shortest Job First (SJF) Priority Algorithm and the Round Robin Scheduling Algorithm. These algorithms are used to determine the order in which processes are executed, balancing factors like process priority, fairness, and system responsiveness.

## 1. Shortest Job First (SJF) Priority Algorithm

### What is SJF?

- **Shortest Job First (SJF)** is a CPU scheduling algorithm that selects the process with the shortest estimated CPU burst time for execution. It is designed to minimize the average waiting time of processes.

### Types of SJF

1. **Non-Preemptive SJF**:
   - Once a process is selected, it runs to completion without being interrupted by other processes.
   
2. **Preemptive SJF (Shortest Remaining Time First - SRTF)**:
   - The current running process can be preempted if a new process arrives with a shorter CPU burst time.

### Characteristics of SJF

- **Optimal in Terms of Average Waiting Time**: SJF provides the minimum average waiting time for a given set of processes, which is why it is considered an optimal scheduling algorithm in this respect.
- **Starvation**: Processes with longer CPU bursts may suffer from starvation, especially if there are many shorter processes arriving.

### Example of Non-Preemptive SJF

Consider the following processes:

| Process | Arrival Time | Burst Time |
|---------|--------------|------------|
| P1      | 0            | 7          |
| P2      | 2            | 4          |
| P3      | 4            | 1          |
| P4      | 5            | 4          |

**Execution Order**:
- P1 starts at time 0 and runs for 7ms.
- P3 arrives at time 4 but P1 is still running, so P3 waits.
- P1 finishes, and P3 (with the shortest burst time) runs next.
- After P3, the process with the next shortest burst time, P2, is selected.
- P4 runs last.

### Metrics Calculation

- **Waiting Time**:
  - P1: 0ms, P2: 7ms, P3: 3ms, P4: 7ms
  - Average Waiting Time = (0 + 7 + 3 + 7) / 4 = 4.25ms
- **Turnaround Time**:
  - P1: 7ms, P2: 11ms, P3: 4ms, P4: 11ms
  - Average Turnaround Time = (7 + 11 + 4 + 11) / 4 = 8.25ms

### Advantages of SJF

- **Optimal Average Waiting Time**: Minimizes the overall waiting time for processes, making it very efficient in terms of process scheduling.
- **Efficient Resource Utilization**: By prioritizing shorter tasks, SJF ensures that more processes are completed quickly.

### Disadvantages of SJF

- **Starvation**: Long processes may experience indefinite waiting if shorter processes keep arriving.
- **Difficult to Implement**: Requires precise knowledge of the burst times, which is often not available.

## 2. Round Robin Scheduling Algorithm

### What is Round Robin?

- **Round Robin (RR)** is a preemptive CPU scheduling algorithm where each process is assigned a fixed time slice or quantum. After this time slice expires, the process is preempted and the CPU is assigned to the next process in the ready queue.

### Characteristics of Round Robin

- **Time Quantum**: A fixed unit of time that determines how long a process can run before being preempted.
- **Fairness**: Every process gets an equal share of CPU time, making RR a fair scheduling algorithm, especially in time-sharing systems.
- **Preemption**: RR is inherently preemptive, as each process can be interrupted after its time slice.

### Example of Round Robin

Consider the following processes with a time quantum of 3ms:

| Process | Arrival Time | Burst Time |
|---------|--------------|------------|
| P1      | 0            | 7          |
| P2      | 1            | 4          |
| P3      | 2            | 9          |
| P4      | 3            | 5          |

**Execution Order**:
- P1 runs from 0-3ms, then is preempted.
- P2 runs from 3-6ms, then is preempted.
- P3 runs from 6-9ms, then is preempted.
- P4 runs from 9-12ms, then is preempted.
- P1 resumes from 12-13ms and finishes.
- P2 resumes from 13-14ms and finishes.
- P3 resumes from 14-15ms, then is preempted.
- P4 resumes from 15-16ms and finishes.
- P3 resumes and finishes at 19ms.

### Metrics Calculation

- **Waiting Time**:
  - P1: 10ms, P2: 4ms, P3: 10ms, P4: 7ms
  - Average Waiting Time = (10 + 4 + 10 + 7) / 4 = 7.75ms
- **Turnaround Time**:
  - P1: 13ms, P2: 8ms, P3: 19ms, P4: 12ms
  - Average Turnaround Time = (13 + 8 + 19 + 12) / 4 = 13ms

### Advantages of Round Robin

- **Fairness**: Each process gets a fair share of CPU time, making it ideal for time-sharing systems.
- **Predictable**: Processes know when they will get CPU time, leading to predictable scheduling.

### Disadvantages of Round Robin

- **Overhead**: The frequent context switches can lead to higher overhead, especially if the time quantum is too small.
- **Response Time**: Larger time quantums can lead to longer response times, affecting the system's interactivity.

### Optimal Time Quantum

- Choosing the right time quantum is crucial in RR scheduling. A very small time quantum can lead to excessive context switching overhead, while a large time quantum can degrade the performance of the scheduling algorithm, making it similar to FCFS.

## Conclusion

The Shortest Job First (SJF) Priority Algorithm and the Round Robin Scheduling Algorithm are both widely used in different types of operating systems. SJF is optimal for reducing waiting times but can cause starvation, while Round Robin offers a fair, predictable scheduling method, particularly suited for time-sharing environments. Understanding these algorithms allows for better selection and tuning based on system requirements and workloads.
