# Concurrency

Ability of the CPU to execute multiple instructions at the same time.

We achieve this ability by using threads .

| Process                                      | Threads                                        |
| -------------------------------------------- | ---------------------------------------------- |
| More time is required for context switching. | Lesser time is required for context switching. |
| Allotted a isolated memory space.            | Share the same memory space.                   |
| Lesser efficient in communication.           | More efficient in terms of communication.      |
| Takes more time to terminate.                | Takes lesser time to terminate.                |

## Threads

Execution of smallest sequence of programmed instructions that can be executed by the schedular independently .

Light weight process

We try to achieve parallelism in the execution of a process.

Every thread has its own TCP ( Thread Control Block ) .

## Critical Section

It is the region of the code or instructions that needs to be executed atomically , because multiple threads are trying to access that region.

## Race Condition

This condition occurs when two or more threads try to access and change the shared data , there is no sequence between the execution of threads i.e. both the threads are racing to do change in the data.

Solutions :

1. Make are the operations in the Critical Section as atomic.
2. Implement Mutual Exclusion between two processes.
3. Bounded wait : Their should be no indefinite waiting , Every thread should be allotted a limited time.

To achieve Synchronization

1. **Mutual Exclusion :**
   1. Suppose two process P1 and P2 wants to enter the critical section ( CS ) , Initially P1 enters the critical section then P2 can not enter the critical section until P1 is done executing and Vice-Versa.
2. **Progress :**
   1. Any process should not , prevent any other process from entering the Critical Section ( even if the critical section is empty ) .
3. **Bounded Wait :**
   1. Their should be a time bound or counter on how much time or no of times a process can enter the critical section.
   2. If this condition is not met then it could happen that some of the process may starve.
4. **No assumption related to h/w or speed :**
   1. Solution should be cross platform , should not depend upon any hardware requirements.

## Lock Variable

We try to solve the problem of critical section using only one variable.

```cpp
do ( ) {
accquire lock
cs
release lock
}

while(lock == 1); // any process will enter into a infinite loop until lock is opened.
lock = 1;
cs
lock = 0;

```

This solution does not guarantee mutual exclusion.

## Peterson Solution

This Solution Guarantees Mutual Exclusion, Process and Bounded wait ( Give Change to each process ).

```cpp
Section(Process){
int other ;
other = 1 - process;
interested[other] = true;
turn = process;
while(interested[other] == true && turn == process);
CS....
CS....
interested[process] = false;
```

## Turn variable

Valid only for 2 processes.

Run in User Mode ( No kernel Interaction required ).

We take a common variable turn.

```cpp
Process P0
while(turn != 0){
CS...
turn = 1

Process P1
while(turn!=1){
CS...
turn = 0
```

Guarantees mutual exclusion , Bounded wait .

Does not Guarantees Progress .
