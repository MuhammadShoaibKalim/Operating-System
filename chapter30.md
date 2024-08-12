# Chapter 30: What is Thrashing? | Important Interview Questions

## 1. What is Thrashing?
- **Definition**: Thrashing occurs when a system spends more time swapping pages in and out of memory than executing actual processes, leading to severe performance degradation.
- **Causes**: 
  - Insufficient physical memory.
  - High degree of multi-programming.
  - Poor page replacement algorithms.
- **Detection**: How to detect thrashing using performance monitoring tools.

## 2. Prevention and Solutions
- **Reducing Degree of Multi-programming**: Limiting the number of processes in memory.
- **Working Set Model**: Ensuring that processes have enough pages in memory to avoid excessive page faults.
- **Load Control**: Adjusting the load on the system to prevent thrashing.

## 3. Important Interview Questions
- **Sample Questions**:
  - Explain thrashing and how to prevent it.
  - What is the difference between paging and segmentation?
  - How does the LRU page replacement algorithm work?
  - Explain the concept of virtual memory and its advantages.
- **Answer Guide**: Detailed answers to common interview questions related to thrashing and memory management.

## Conclusion
- Summary of thrashing, its impact on system performance, and strategies to prevent it.
