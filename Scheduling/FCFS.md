#Operating-Systems #non-preemptive 
The First-Come, First-Served (FCFS) scheduling algorithm is one of the simplest types of CPU scheduling algorithms used in operating systems. Here’s how it works:

1. **Basic Concept**: FCFS schedules processes in the order they arrive in the ready queue. The first process to arrive is the first one to get the CPU for execution. It's akin to a typical queueing system in everyday life, such as a line at a bank or grocery store.

2. **Non-Preemptive Nature**:
   - Once a process starts executing, it runs until completion or a blocking event (like an I/O operation). It is not preempted for another process.
   - New arriving processes are added to the tail of the queue.

3. **Implementation**:
   - It's implemented using a FIFO (First In, First Out) queue. Processes are added to the rear of the queue and taken from the front.
   - It’s simple to implement because it requires minimal process management overhead.

4. **Advantages**:
   - **Simplicity and Fairness**: Due to its straightforward approach, it is easy to understand and implement. Every process gets a chance to execute in the order of their arrival.
   - **Predictability**: It's easier to predict which process will be executed next.

5. **Disadvantages**:
   - **Convoy Effect**: Shorter processes may get stuck waiting behind longer processes, leading to inefficient CPU utilization. This is known as the "convoy effect."
   - **No Consideration for Process Priority**: FCFS does not consider process priority. A high-priority process will have to wait if it arrives after a low-priority process.
   - **Longer Average Waiting Time**: Compared to other more sophisticated algorithms, FCFS can lead to longer average waiting times, especially in a system with a mix of short and long tasks.

6. **Use Cases**:
   - FCFS is suitable for environments where tasks do not vary significantly in their execution times or where the arrival rate is low.
   - It's often used in batch processing environments where the execution order is crucial.

7. **Performance Metrics**:
   - In terms of metrics like average waiting time and average turnaround time, FCFS may not perform as well as other algorithms like Shortest Job First or Round Robin, particularly in systems with a diverse range of process execution times.

In summary, FCFS is a simple, fair, and easily implementable scheduling algorithm. However, its efficiency can be low in certain scenarios, especially where process execution times vary widely, leading to the potential for long wait times and poor CPU utilization.