# Operating Systems ( continuation )

## Process Lifecycle

**Waiting Queue** :

Processes in Wait State.

Dispatcher :

The module of OS that gives control of CPU to a process selected by STS.

## Context Switching

→ Most of the time sharing system have a Medium Term Schedular .

→ When the degree of multi-programming increases then , some of the process present in the ready queue are moved to a storage space called swap space by MTS , this process is called Swapping .

→ Swap-In and Swap-Out is done by MTS.

> Context Switching is done by kernel.

It is a mechanism provided by operating systems in which one single CPU can share multiple processes. It is done by storing the state of the current process and resuming the execution of the other stored process state in the memory .

## Orphan Process

A child process is running even after its parent process is terminated or completed without waiting for the child process execution is called orphan process.

Init is the first process in the OS.

### Zombie Process

A process that has completed its task but still present in the Process table entry .

### Process Scheduling

It is the activity of the process manager that handles the removal of the process from the running phase and selection of another process on the basis of algorithm.

**Types of Scheduling Algorithm**:

1. Preemptive Scheduling :
   1. A process leaves the CPU either it is terminated or placed in the waiting state for some I/O or process’s time quantum is over.
   2. More CPU Utilization .
   3.
2. Non-Preemptive Scheduling :
   1. A process leaves the CPU either it is terminated or placed in the waiting state for some I/O processes .
   2. No reference with time quantum.
   3. Process Starvation is bound to happen.

### FCFS

First Come First Serve

The process which came at the earliest is provided to the Dispatcher and then Sequentially all the other process are executed along the way.

Problem : Convoy Effect ⇒ Situation where many processes , who needs cpu for short period of time are waiting to get executed , are blocked by one process holding the resource for a long time.

> Response Time = { CPU Allotted first time - Arrival Time } .

### SJF

Shortest Job First

Process with least Burst time will get the CPU First .

Types :

1. Non-Preemptive

   Criteria : Arrival Time & Burst Time .

   > Arrival time is given precedence over the Burst Time.

   > At any time if the burst time is equal then check for Arrival Time.

   Flow : CPU has to apply heuristic to get the burst time of the process before executing them.

   If a job having the latest arrival time enters the scheduler then it has to be dispatched to the CPU , which may lead to convoy effect .

2. Preemptive

   Criteria : is same .

   Every time time stamp , we check weather another with lesser Burst time has entered the Scheduler .

   If a process with less burst time enters then we preempt the current process and execute that one .

   else we continue executing the current process.

## Priority Scheduling

[https://youtu.be/rsDGfFxSgiY](https://youtu.be/rsDGfFxSgiY)

Preemptive

Criteria : Priority

> Higher the number higher the priority.

At a given current time if two process enters the scheduler then the once with the higher priority will be executed by the CPU.

When all the process have arrived then only criteria left to compare becomes priority .

Drawback : Suppose there are two types of processes in the queue , first one have a higher priorities and second one having lower priorities , then at some point of time it may happen that processes having lower priorities may not get the CPU , because of higher priorities processes , this condition is called Indefinite waiting or Extreme starvation.

## Round-Robin Algorithm

Most Popular Algorithm.

Criteria : Arrival Time + Time Quantum .

Designed for Time Sharing Systems.

Preemptive

At every time we check the no of processes entered the scheduler then , according to that sequence we add those processes into the queue .

Once a process is done executing

if it is still left for processing then we add the process at the back of the queue.

else we continue executing next ones.

Drawback : Larger no of overheads occur.

Lesser is the time quantum more context switching .

## Multi-level Queue Scheduling

It says that their must be a different queue for every process , each queue can have different scheduling algorithm .

All the queues are connected to the CPU .

Different Queue for each types of process Higher priority process ( RR ) , Medium priority process ( SJF ) , less priority process ( FCFS ) .

This Scheduling is used in most of the recent operating systems.

Drawback : This Scheduling may be vulnerable to process starvation i.e. the queue with the least priority may suffer starvation.

### Feedback - Queue Scheduling

Here queues are classified as high and low priority queues , if a process take longer time to execute then it is pushed into the low priority queue.

Each process is assigned a specific time quantum in a priority queue.
