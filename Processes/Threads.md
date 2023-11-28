#Operating-Systems 
# Threads in Computing

- **Shared Sections**: Threads share the code and data segments of their process.
	- All threads in a process will share the heap.
- **Unique Resources**: Each thread possesses its own registers and stack.

## Practical Example

- A web server actively listens for client requests.
- When a request is received, it is handled by a newly created thread, specifically dedicated to that client.
- Simultaneously, the server resumes listening for more requests, managing each with separate threads.

## Advantages of Using Threads

- **Responsiveness**: Threads can keep an application active even when parts of it are blocked or performing lengthy operations.
  
- **Resource Sharing**: Threads can access the same memory and resources of their parent process more efficiently than inter-process communication methods.
  
- **Lower Overhead**: Switching between threads is typically faster than switching between processes due to less overhead.
  
- **Improved Utilization on Multi-Core Systems**: Threads can be spread across multiple cores, allowing a single process to perform multiple tasks simultaneously.

# Harnessing Multi-Core Architectures

- **Independent Cores**: Each core is treated as an independent processing unit.

## Multi-Threaded Programming

- Improves application concurrency and takes full advantage of multi-core system efficiency by parallelizing thread execution.

### Understanding Concurrency and Parallelism

#### Concurrency

- The ability of an application to manage multiple tasks by allowing them to progress in overlapping time periods, optimizing the use of CPU time.

#### Parallelism

- The simultaneous execution of different tasks on multiple processor cores.

#### Delineation of Parallelism

##### Data Parallelism

- Involves processing different pieces of data across multiple cores simultaneously, performing the same operation on each piece of data.

##### Task Parallelism

- Refers to distributing different threads or tasks across multiple cores, with each thread performing a distinct operation.

##### Application in Web Servers

- Web servers employ both data and task parallelism by using a listening thread for accepting connections and multiple handler threads for processing individual client requests concurrently, although all handler threads perform similar tasks on different data (i.e., requests).

# Understanding User Threads and Kernel Threads

## User-Level Threads

- **Management**: User threads are managed by user-level thread libraries, not directly by the operating system kernel.
- **Common Libraries**:
  - `POSIX Pthreads`: A standard for thread creation and synchronization in UNIX-like systems.
  - `Windows Threads`: Native threading library for Windows.
  - `Java Threads`: Managed by the Java Virtual Machine, allowing thread management within Java applications.

## Kernel-Level Threads

- **Support**: Directly supported and managed by the operating system's kernel.

### Relationship Between User and Kernel Threads

#### Many-to-One Model
- **Usage**: Seldom used due to its limitations.
- **Parallelism**: Not achievable as all user threads map to a single kernel thread.
- **Example**: GNU Portable Threads.

#### One-to-One Model
- **Mapping**: Each user-level thread corresponds to a single kernel thread.
- **Overhead**: Higher due to the creation of kernel threads.
- **Efficiency**: Provides the most efficient system utilization.
- **Concurrency**: Maximizes concurrency, albeit with maximum overhead.
- **Examples**: Linux, Windows OS.

#### Many-to-Many Model
- **Prevalence**: Relatively rare due to its complexity.
- **Implementation**: Seen in systems like Windows with the ThreadFiber package where it allows flexibility in management.

## Libraries for Thread Management

- **[[Pthreads]]**: Stands for POSIX threads, a widely used C/C++ library for multi-threading.
- **Windows Thread Library**: Provides APIs for creating and managing threads in Windows applications.
- **Java Thread Library**: Offers a high-level threading model within the Java language for concurrent programming.

