#Operating-Systems 
1. **Memory vs. Disk**: In computing terminology, "memory" typically refers to Random Access Memory (RAM), whereas "disk" refers to the hard disk. These are two distinct types of storage used in computers.

2. **Role of Registers**: Registers are a critical component in a computer's architecture. They are used by the Central Processing Unit (CPU) to perform operations. Registers are faster than both RAM and hard disk storage but have a much smaller capacity.

3. **Function of Memory**: Memory (RAM) is used to store both instructions and data. It plays a vital role in the execution of programs, allowing for quick access to the information that the CPU requires for processing tasks.

Here's an expanded and corrected version of your notes on contiguous and non-contiguous memory allocation:

## Contiguous Allocation
In contiguous allocation, memory is allocated in a single continuous block. This method can be divided into two types:

1. **Fixed Partitioning (Static Partitioning)**: The memory is divided into fixed-sized partitions. Each partition can hold only one process. The size of the partitions is predetermined and remains constant, which can lead to issues like internal fragmentation if a process's size is smaller than its assigned partition.

2. **Variable Partitioning (Dynamic Partitioning)**: In this method, memory is allocated dynamically, based on the exact size of the process. It's more flexible and efficient compared to fixed partitioning. However, it can lead to external fragmentation over time as processes are loaded and removed, leaving behind small unused gaps in memory.

## Non-Contiguous Allocation
Non-contiguous allocation allows processes to be stored in multiple memory blocks that are not necessarily adjacent. This method addresses some of the limitations of contiguous allocation:

1. **Logical vs. Physical Address Space**: Non-contiguous allocation often involves the use of logical and physical address spaces. The logical address space is the view of the memory from the process’s perspective, while the physical address space refers to the actual memory locations in RAM. This separation allows the operating system to more flexibly manage memory.

2. **Placement in RAM**: In non-contiguous allocation, processes are divided into smaller parts, such as pages or segments, which are then placed in various locations in RAM. This approach reduces fragmentation and allows for more efficient use of memory. It also enables techniques like paging and segmentation, which help in managing memory more effectively and allow for processes to be larger than the total available physical memory.

Overall, non-contiguous allocation is more flexible and efficient for managing memory in modern computing systems, as it allows for better utilization of available memory and supports multitasking and large application sizes.

