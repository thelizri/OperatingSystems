#Operating-Systems
![[Structure.PNG]]
# User Mode and Kernel Mode:

- **User Mode:** 
  - Programs in user mode have limited privileges and cannot directly interact with hardware or system memory. This restriction enhances system stability and security by preventing user programs from performing potentially harmful operations.

- **Kernel Mode:**
  - In contrast to user mode, kernel mode allows code to run with unrestricted access to hardware and system resources. This mode is reserved for the most trusted and essential parts of the operating system, such as device drivers, system services, and core functions.

# System Programs vs. Application Programs:

- **System Programs:**
  - System programs are integral to the OS, providing essential utilities and services that maintain system operations. Examples include file managers, system monitors, and network utilities.

- **Application Programs:**
  - Application programs are designed to perform specific tasks for users, such as browsing the internet, word processing, or gaming. They rely on the OS for system resources and services but are not part of the OS itself.

# Kernel Space:

- Kernel space is a protected memory area dedicated to the kernel. This isolation safeguards the kernel from disruptions caused by user applications, ensuring system stability and security.

## Core Responsibilities of the OS:

- **Memory Management:**
  - The OS manages system memory, allocating and deallocating memory as programs require it. This includes managing virtual memory and paging to ensure efficient use of RAM.

- **Storage Management:**
  - OS handles the storage of data on hard drives and other media, including file systems management, data organization, and access control.

- **Process Management:**
  - The OS is responsible for creating, scheduling, and terminating processes. It ensures that CPU time is efficiently distributed among processes and that system resources are allocated appropriately.

- **I/O Subsystem:**
  - This includes a general device-driver interface that acts as a communication layer between hardware devices and the OS. It ensures that software can interact with hardware through a standardized interface.

# System Calls:

- System calls are programming interfaces that allow user applications to request services from the OS. They serve as a controlled gateway between user mode and kernel mode, facilitating secure and efficient operations.

- **Example of System Calls with `strace`:**
  - Tools like `strace` can be used to trace system calls made by programs. For example, running `strace cp a.txt b.txt` reveals the system calls invoked during the file copy operation. This demonstrates how high-level API functions, like `cp`, utilize multiple system calls to perform their tasks.