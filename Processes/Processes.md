#Operating-Systems 
# Process vs. Program

Understanding the distinction between a program and a process is crucial in computing:

- A **Program** is a static sequence of instructions; a **Process** is a dynamic execution instance of a program.

## Components of a Process

![[PartsOfAProcess.PNG]]

## Process Control Block (PCB)

A PCB is a specialized data structure that preserves all the essential details of a process, encompassing its state, program counter, CPU registers, memory boundaries, and more.

![[PCB.PNG]]

## States of a Process

Processes navigate through several states throughout their existence:

![[ProcessStates.PNG]]

- **New**: The process is in the phase of creation.
- **Ready**: The process is primed to run, awaiting CPU allocation.
- **Running**: The process is actively executing its commands on the CPU.
- **Waiting**: The process is in a dormant state, pending an external event such as I/O completion.
- **Terminated**: The process has concluded its execution and is in the process of exiting.

## Process Scheduling

The scheduling of processes is instrumental in enhancing CPU utilization by judiciously selecting processes for execution:

![[ScheduleQueue.PNG]]

- **Ready Queue**: This queue houses processes that are poised to run.
- **Waiting Queue**: This queue accommodates processes that are in a holding pattern, awaiting an event.

## Process Operations

Process operations in C provide fundamental tools for managing and controlling processes:

![[Operations.PNG]]

- `fork()`: Used to create a new child process.
- `getpid()`: Retrieves the process ID (PID) of the calling process.
- `exec()`: Replaces the current process image with a new program.
- `wait()`: Blocks the calling process until a child process exits.
- `exit()`: Terminates the calling process.

For a comprehensive understanding, refer to the [[Process API]] document.

# Inter-Process Communication (IPC)

Inter-Process Communication (IPC) mechanisms are pivotal for enabling processes to communicate and synchronize their operations efficiently. The two primary categories of IPC methods are **Shared Memory** and **Message Passing**. For more information regarding IPC read [[Inter-Process Communication| IPC programming in C]].

## Shared Memory

Shared Memory is a method of Inter-Process Communication (IPC) that allows multiple processes to access a common segment of memory. This method is efficient because processes can communicate by reading and writing data directly to a shared memory space.

### Core Functions

- `shm_open()`: Used to create or open a shared memory object.
- `mmap()`: Maps the shared memory object into the process's address space, enabling access.
- `shm_unlink()`: Removes the shared memory object name, marking it for deletion.

Shared Memory provides a fast and effective means of communication between processes by enabling direct access to a common memory area, facilitating rapid data exchange.

## Message Passing

Message Passing is a method of Inter-Process Communication (IPC) that allows processes to exchange data through messages. This mechanism includes various IPC methods such as Pipes, FIFOs (Named Pipes), and Message Queues.

### Pipe

Pipes are unidirectional communication channels that facilitate one-way communication. They are typically used within a parent-child process relationship.

### FIFO (Named Pipe)

FIFOs, also known as Named Pipes, are similar to pipes but exist as named entities within the file system. They support bidirectional communication and do not require a parent-child process relationship, allowing multiple processes to communicate through them.

### Message Queue

Message Queues are IPC mechanisms that allow processes to send and receive messages in a FIFO (first-in, first-out) manner. They enable the exchange of complete messages and do not require a continuous connection between processes.

#### Queue Operations

- `mq_open()`: Creates or opens a message queue.
- `mq_close()`: Closes a message queue descriptor.
- `mq_unlink()`: Deletes a message queue.

#### Message Transactions

- `mq_send()`: Sends a message to the queue.
- `mq_receive()`: Retrieves the oldest message from the queue.

These IPC methods provide processes with the means to communicate effectively, facilitating coordination and functionality in complex systems.