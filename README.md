# CPU Scheduling Algorithms Simulation

This project implements and compares three CPU scheduling algorithms: **First-Come, First-Served (FCFS)**, **Shortest Job First (SJF)**, and **Multilevel Feedback Queue (MLFQ)** using Python.  
The objective of the assignment was to simulate each algorithm’s scheduling behavior, calculate their performance metrics, and analyze differences in CPU utilization, waiting time, turnaround time, and response time.

[View Full Project Report (PDF)](./Chase_Moffat_Project_Report.pdf)

---

## Overview

The program simulates how a CPU scheduler handles multiple processes, each with defined CPU and I/O bursts.  
Each process is represented by a `Process` class that stores:
- CPU and I/O burst sequences  
- Process ID  
- Total burst time  
- Wait time  
- Turnaround time  
- Response time  

The simulation prints execution details such as the ready queue, I/O queue, and currently running process at each clock cycle, providing full visibility into the CPU scheduling behavior.

---

## Implemented Algorithms

### 1. FCFS (First-Come, First-Served)
A non-preemptive scheduling algorithm where processes are executed in the order they arrive.  
Since all processes in this project arrive at time 0, they are executed sequentially from P1 to P8.  
After each CPU burst, a process is sent to the I/O queue before returning to the ready queue for the next burst.

### 2. SJF (Shortest Job First)
A non-preemptive algorithm that selects the process with the shortest CPU burst time next.  
Each time a process completes its I/O burst and re-enters the ready queue, the queue is re-sorted based on the shortest remaining CPU burst.  
This reduces the average waiting time but may cause longer response times for larger jobs.

### 3. MLFQ (Multilevel Feedback Queue)
A more complex scheduler that dynamically adjusts process priority across three queues:
- Queue 1: Round Robin with a time quantum of 5  
- Queue 2: Round Robin with a time quantum of 10  
- Queue 3: FCFS queue  

Processes begin in the first queue. If their CPU burst exceeds the time quantum, they are demoted to the next queue.  
This approach balances responsiveness for short jobs with fairness for longer ones.

---

## Results Summary

| Algorithm | CPU Utilization | Avg Waiting Time | Avg Turnaround Time | Avg Response Time |
|------------|----------------|------------------|---------------------|-------------------|
| SJF        | 82.66%         | 133.50           | 469.63              | 27.13             |
| FCFS       | 85.21%         | 185.25           | 521.38              | 24.38             |
| MLFQ       | 92.47%         | 170.63           | 506.75              | 15.75             |

The MLFQ achieved the highest CPU utilization and lowest average response time, while SJF minimized waiting time but at the cost of higher response delays for longer processes.

---

## Discussion

The results demonstrate that the choice of scheduling algorithm can significantly affect CPU performance and process response times.  
SJF produced the shortest waiting times overall but performed worse in responsiveness.  
FCFS was straightforward but inefficient under mixed workloads.  
MLFQ provided the best overall balance, achieving the highest CPU utilization through dynamic process prioritization.

This project deepened understanding of how scheduling algorithms impact system efficiency, responsiveness, and fairness in operating systems.

---

**Author:** Chase Moffat  
**Course:** COP 4610 – Operating Systems  
**Date:** October 22, 2023
