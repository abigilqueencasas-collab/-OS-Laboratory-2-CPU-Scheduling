# OS-Laboratory-2-CPU-Scheduling

**Operating Systems Lab 2 - CPU Scheduling Algorithms**

| | |
|---|---|
| **Course** | BCA151 Operating Systems Lab |
| **Name** | Casas, Abigil Queen C. |
| **Course & Year** | Computer Application - 3 |
| **Date** | October 26, 2026 |
| **School** | Mindanao State University - Iligan Institute of Technology, College of Computer Studies |

---

## 1. About the Project

This repository contains a CPU Scheduling Simulator written in Python 3 and developed in GitHub Codespaces. It implements and compares five algorithms:

1. First-Come, First-Served (FCFS)
2. Non-preemptive Shortest Job First (SJF)
3. Non-preemptive Priority Scheduling
4. Round Robin (RR)
5. Preemptive Shortest Remaining Time First (SRTF)

For each algorithm the program prints a Gantt chart, a process table (CT, TAT, WT, RT), and the average waiting, turnaround, and response times.

## 2. Files

| File | Description |
|---|---|
| `cpu_scheduling.py` | The CPU scheduling simulator |
| `README.md` | This lab report |

## 3. How to Run

```bash
python3 cpu_scheduling.py
```

If `python3` is unavailable, use `python cpu_scheduling.py`.

## 4. Datasets and Assumptions

**Original dataset** (FCFS, SJF, Priority, Round Robin)

| Process | Arrival Time (AT) | Burst Time (BT) | Priority |
|---|---|---|---|
| P1 | 0 | 8 | 2 |
| P2 | 0 | 4 | 1 |
| P3 | 0 | 2 | 4 |
| P4 | 0 | 6 | 3 |

**Separate SRTF dataset**

| Process | Arrival Time (AT) | Burst Time (BT) | Priority |
|---|---|---|---|
| P1 | 0 | 8 | 2 |
| P2 | 1 | 4 | 1 |
| P3 | 2 | 2 | 4 |
| P4 | 3 | 1 | 3 |

**Assumptions**

- A smaller priority number means a higher priority.
- Round Robin uses a time quantum of 2 ms (unless stated otherwise in the experiment).
- SJF and Priority Scheduling are non-preemptive.
- FCFS uses arrival order, with process ID breaking arrival-time ties.
- SRTF uses its own dataset so that preemption can be demonstrated.

**Formulas**

| Metric | Formula |
|---|---|
| Turnaround Time (TAT) | TAT = CT - AT |
| Waiting Time (WT) | WT = TAT - BT |
| Response Time (RT) | RT = First CPU Start - AT |
| Average metric | Sum of metric values / number of processes |

---

## 5. Program Output (Screenshots)

Screenshots of the program running in GitHub Codespaces using the original dataset.

**FCFS and Non-preemptive SJF**

<img width="1277" height="892" alt="image" src="https://github.com/user-attachments/assets/13af4de5-7e4e-49f8-a455-21738502478b" />

&nbsp;

**Non-preemptive Priority and Round Robin (q = 2)**

<img width="1267" height="882" alt="image" src="https://github.com/user-attachments/assets/1f1d6b7a-7126-4e5e-bc91-0a0a448c007e" />

&nbsp;

**SRTF (separate dataset)**

<img width="793" height="416" alt="image" src="https://github.com/user-attachments/assets/3f4c7398-124a-4482-9f4a-71df37701e92" />

&nbsp;

---

## 6. Gantt Charts

**FCFS**

```
| P1 | P2 | P3 | P4 |
0    8    12   14   20
```

**Non-preemptive SJF**

```
| P3 | P2 | P4 | P1 |
0    2    6    12   20
```

**Non-preemptive Priority**

```
| P2 | P1 | P4 | P3 |
0    4    12   18   20
```

**Round Robin (q = 2)**

```
| P1 | P2 | P3 | P4 | P1 | P2 | P4 | P1 | P4 | P1 |
0    2    4    6    8    10   12   14   16   18   20
```

**SRTF**

```
| P1 | P2 | P3      | P4 | P2      | P1            |
0    1    2         4    5         8               15
```

Preemption points in SRTF:

- At t = 1, P1 (7 ms remaining) is preempted by P2 (4 ms).
- At t = 2, P2 (3 ms remaining) is preempted by P3 (2 ms).
- At t = 3, P3 and P4 both have 1 ms remaining, and P3 continues because it arrived earlier.

## 7. Calculation Tables

**FCFS**

| PID | AT | BT | CT | TAT | WT | RT |
|---|---|---|---|---|---|---|
| P1 | 0 | 8 | 8 | 8 | 0 | 0 |
| P2 | 0 | 4 | 12 | 12 | 8 | 8 |
| P3 | 0 | 2 | 14 | 14 | 12 | 12 |
| P4 | 0 | 6 | 20 | 20 | 14 | 14 |

**Non-preemptive SJF**

| PID | AT | BT | CT | TAT | WT | RT |
|---|---|---|---|---|---|---|
| P1 | 0 | 8 | 20 | 20 | 12 | 12 |
| P2 | 0 | 4 | 6 | 6 | 2 | 2 |
| P3 | 0 | 2 | 2 | 2 | 0 | 0 |
| P4 | 0 | 6 | 12 | 12 | 6 | 6 |

**Non-preemptive Priority**

| PID | AT | BT | Priority | CT | TAT | WT | RT |
|---|---|---|---|---|---|---|---|
| P1 | 0 | 8 | 2 | 12 | 12 | 4 | 4 |
| P2 | 0 | 4 | 1 | 4 | 4 | 0 | 0 |
| P3 | 0 | 2 | 4 | 20 | 20 | 18 | 18 |
| P4 | 0 | 6 | 3 | 18 | 18 | 12 | 12 |

**Round Robin (q = 2)**

| PID | AT | BT | CT | TAT | WT | RT |
|---|---|---|---|---|---|---|
| P1 | 0 | 8 | 20 | 20 | 12 | 0 |
| P2 | 0 | 4 | 12 | 12 | 8 | 2 |
| P3 | 0 | 2 | 6 | 6 | 4 | 4 |
| P4 | 0 | 6 | 18 | 18 | 12 | 6 |

**SRTF (separate dataset)**

| PID | AT | BT | CT | TAT | WT | RT |
|---|---|---|---|---|---|---|
| P1 | 0 | 8 | 15 | 15 | 7 | 0 |
| P2 | 1 | 4 | 8 | 7 | 3 | 0 |
| P3 | 2 | 2 | 4 | 2 | 0 | 0 |
| P4 | 3 | 1 | 5 | 2 | 1 | 1 |

Sample manual check (FCFS, P2): P2 starts at 8 ms and finishes at 12 ms, so CT = 12, TAT = 12 - 0 = 12, WT = 12 - 4 = 8, and RT = 8 - 0 = 8. This matches the program output.

## 8. Comparison of Average Metrics (Original Dataset)

| Algorithm | Average WT | Average TAT | Average RT |
|---|---|---|---|
| FCFS | 8.50 ms | 13.50 ms | 8.50 ms |
| Non-preemptive SJF | 5.00 ms | 10.00 ms | 5.00 ms |
| Non-preemptive Priority | 8.50 ms | 13.50 ms | 8.50 ms |
| Round Robin (q = 2) | 9.00 ms | 14.00 ms | 3.00 ms |
| SRTF (separate dataset) | 2.75 ms | 6.50 ms | 0.25 ms |

---

## 9. Round Robin Time-Quantum Experiment

Dataset: original dataset.

| Quantum | CPU allocations | Average WT | Average TAT | Average RT |
|---|---|---|---|---|
| 1 | 19 | 9.50 ms | 14.50 ms | 1.50 ms |
| 2 | 10 | 9.00 ms | 14.00 ms | 3.00 ms |
| 4 | 6 | 9.00 ms | 14.00 ms | 5.50 ms |

**Round Robin, quantum = 1**

<img width="1470" height="419" alt="image" src="https://github.com/user-attachments/assets/2f4d507e-ed06-450f-b8e6-204d12bcc208" />

&nbsp;

**Round Robin, quantum = 2**

<img width="1128" height="402" alt="image" src="https://github.com/user-attachments/assets/24603e0a-ecd5-41c5-b2f0-f6346563acfb" />


&nbsp;

**Round Robin, quantum = 4**

<img width="655" height="391" alt="image" src="https://github.com/user-attachments/assets/1b1b1def-2382-45d1-97e7-47541a9b3d0c" />


&nbsp;

**Observations**

- **Effect on CPU allocations:** A smaller quantum splits each burst into more slices, so the number of CPU allocations increases (6 at q = 4, 10 at q = 2, 19 at q = 1).
- **Lowest average waiting time:** q = 2 and q = 4 tie at 9.00 ms, while q = 1 is slightly higher at 9.50 ms.
- **Very large quantum:** When the quantum is at least as long as the longest burst (8 ms here), no process is preempted and Round Robin behaves exactly like FCFS (WT 8.50, TAT 13.50, RT 8.50).
- **Small-quantum overhead:** Every slice ends with a context switch in which the OS saves one process's state and loads another's. This work is pure overhead, so with a very small quantum the CPU spends a larger share of its time switching instead of running processes.

---

## 10. Modified Dataset (Step 23)

The burst times and priorities were changed, and the same modified dataset was used for FCFS, SJF, Priority, and Round Robin (q = 2). The SRTF dataset was kept separate.

| Process | Arrival Time (AT) | Burst Time (BT) | Priority |
|---|---|---|---|
| P1 | 0 | 5 | 3 |
| P2 | 0 | 9 | 4 |
| P3 | 0 | 3 | 1 |
| P4 | 0 | 7 | 2 |

| Algorithm | Gantt Chart |
|---|---|
| FCFS | P1 [0-5] \| P2 [5-14] \| P3 [14-17] \| P4 [17-24] |
| SJF | P3 [0-3] \| P1 [3-8] \| P4 [8-15] \| P2 [15-24] |
| Priority | P3 [0-3] \| P4 [3-10] \| P1 [10-15] \| P2 [15-24] |
| Round Robin (q = 2) | P1 [0-2] \| P2 [2-4] \| P3 [4-6] \| P4 [6-8] \| P1 [8-10] \| P2 [10-12] \| P3 [12-13] \| P4 [13-15] \| P1 [15-16] \| P2 [16-18] \| P4 [18-20] \| P2 [20-22] \| P4 [22-23] \| P2 [23-24] |
| SRTF | P1 [0-1] \| P2 [1-2] \| P3 [2-4] \| P4 [4-5] \| P2 [5-8] \| P1 [8-15] |

| Algorithm | Average WT | Average TAT | Average RT |
|---|---|---|---|
| FCFS | 9.00 ms | 15.00 ms | 9.00 ms |
| SJF | 6.50 ms | 12.50 ms | 6.50 ms |
| Priority | 7.00 ms | 13.00 ms | 7.00 ms |
| Round Robin (q = 2) | 13.00 ms | 19.00 ms | 3.00 ms |
| SRTF (separate dataset) | 2.75 ms | 6.50 ms | 0.25 ms |

Screenshots of the program output using the modified dataset.

**FCFS and Non-preemptive SJF**

<img width="631" height="804" alt="image" src="https://github.com/user-attachments/assets/97312add-62b5-4be4-a2b2-757fd5a3c182" />

&nbsp;

**Non-preemptive Priority and Round Robin (q = 2)**

<img width="1512" height="788" alt="image" src="https://github.com/user-attachments/assets/223376fa-6da6-4e38-9387-3a030f8bcb42" />

&nbsp;

**SRTF (unchanged, separate dataset)**


&nbsp;

---

## 11. Answers to the Laboratory Questions

**28. What is CPU scheduling, and why is it necessary?**
CPU scheduling is the operating system function that decides which process in the ready queue gets the CPU next. It is necessary because there are usually more ready processes than CPUs, and a good scheduling policy keeps the CPU busy and improves throughput and responsiveness.

**29. What is the difference between FCFS and SJF?**
FCFS runs processes in the order they arrive, regardless of their length. SJF picks the ready process with the shortest burst time.

**30. Why can SJF produce a lower average waiting time than FCFS?**
Running short jobs first means fewer processes wait behind long ones. In the lab data, FCFS made P3 (2 ms) wait 12 ms, while SJF ran it first. This gave SJF an average waiting time of 5.00 ms versus 8.50 ms for FCFS.

**31. How does Priority Scheduling determine the next process?**
It selects the ready process with the highest priority, which in this lab is the smallest priority number. Ties are broken by arrival time, then process ID.

**32. What is starvation? Which algorithms can experience it?**
Starvation happens when a process waits indefinitely because other processes keep being chosen ahead of it. Priority Scheduling (low-priority processes) and SJF/SRTF (long processes) can cause starvation. FCFS and Round Robin do not, because every process eventually gets its turn. Aging, which gradually raises the priority of waiting processes, is a common fix.

**33. How does Round Robin improve responsiveness for interactive processes?**
Because of the fixed time quantum and rotating queue, each process gets the CPU within a bounded time, so interactive processes receive quick responses. In this lab, Round Robin's average response time was 3.00 ms compared with 8.50 ms for FCFS.

**34. What is the effect of changing the Round Robin time quantum?**
A smaller quantum improves response time but increases the number of context switches. A larger quantum reduces overhead but makes Round Robin behave like FCFS, which hurts responsiveness.

**35. How does SRTF differ from non-preemptive SJF?**
SRTF is the preemptive version of SJF. If a newly arrived process has a shorter remaining time than the running process, it takes over the CPU. In non-preemptive SJF, the running process always finishes first.

**36. Why do preemptive algorithms require the operating system to save and restore process context?**
A preempted process must later resume exactly where it stopped. The OS therefore saves its registers, program counter, and other state in its process control block (PCB), and restores them when the process runs again.

**37. Does the algorithm with the lowest average waiting time always provide the best user experience?**
No. SJF has the lowest average waiting time but can starve long jobs and needs burst times to be known in advance. Interactive users care more about response time, where Round Robin performs better, so fairness and responsiveness also matter.

**38. Why is it important to use the same dataset when comparing algorithms?**
The results depend heavily on the arrival times, burst times, and priorities. With identical input, any difference in the metrics comes from the algorithm itself and not from the data.

**39. What role does GitHub play in managing and submitting your laboratory work?**
GitHub stores the project in a repository with version history, lets me commit and sync my code from Codespaces, serves as a backup, and gives my instructor a link to review and verify my work.

---

## 12. Analysis and Conclusion

This activity implemented FCFS, SJF, Priority, Round Robin, and SRTF in Python and compared them using completion, turnaround, waiting, and response time. On the original dataset, SJF gave the lowest average waiting time (5.00 ms) and turnaround time (10.00 ms), while FCFS and Priority were equal at 8.50 ms and 13.50 ms. Round Robin had a slightly higher average waiting time (9.00 ms) but the best average response time (3.00 ms), which suits interactive systems. On the separate dataset, SRTF achieved an average waiting time of 2.75 ms, showing the benefit of preempting a long process when shorter ones arrive.

The quantum experiment showed the trade-off in Round Robin: a smaller quantum lowered response time (1.50 ms at q = 1) but needed many more CPU allocations, which means more context-switching overhead in a real system.

Using the modified dataset (BT 5/9/3/7, Priority 3/4/1/2), SJF again gave the lowest average waiting time (6.50 ms) among the four algorithms, followed by Priority (7.00 ms) and FCFS (9.00 ms). Round Robin had the highest average waiting time (13.00 ms) because processes were repeatedly interrupted, but it kept the best average response time (3.00 ms). This shows that the best algorithm depends on the goal: SJF minimizes waiting, while Round Robin favors responsiveness. The lowest waiting time is also not always the best choice, since SJF and SRTF risk starving long processes and Priority scheduling risks starving low-priority ones.

Finally, using GitHub Codespaces made it easy to develop, run, and version the program in the browser, and committing the work to GitHub provides a record that can be submitted and reviewed.

---

## 13. Required Deliverables Checklist

- [x] GitHub repository link: *(paste your repository link here)*
- [x] Completed Python source code (`cpu_scheduling.py`)
- [x] Screenshot of the program running in Codespaces (Section 5)
- [x] Gantt charts for all five algorithms (Section 6)
- [x] Calculation tables showing CT, TAT, WT, and RT (Section 7)
- [x] Comparison table of average metrics (Sections 8 and 10)
- [x] Results of the Round Robin time-quantum experiment (Section 9)
- [x] Answers to the laboratory questions (Section 11)
- [x] Brief analysis and conclusion (Section 12)
