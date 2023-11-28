
### 1. Peterson's Solution

Peterson's Solution is a classical software-based technique used for mutual exclusion in concurrent programming. It allows two processes to share a single-use resource without conflict, using two shared variables: a flag array and a turn variable.

Here is a simple example in C:

```c
#define N 2 // Number of processes

int flag[N]; // Flag array used for signaling the intention to enter the critical section
int turn;    // A shared variable indicating whose turn it is

void enter_region(int process) {
    int other = 1 - process;  // The opposite process number
    flag[process] = 1;        // Show that you are interested
    turn = process;           // Set flag
    while (flag[other] == 1 && turn == process) ;  // Wait
}

void leave_region(int process) {
    flag[process] = 0;  // Indicate exit from critical section
}

void process(int process) {
    while (1) {
        enter_region(process);
        // Critical section
        leave_region(process);
        // Remainder section
    }
}
```

In this code, `enter_region` and `leave_region` functions are used to manage access to the critical section. The `flag` array signals a process's intent to enter the critical section, and `turn` decides whose turn it is to enter.

### 2. Mutex Lock

A mutex lock is a synchronization primitive that can be used to protect shared data from being simultaneously accessed by multiple threads. Here is an example using pthreads in C:

```c
#include <pthread.h>

pthread_mutex_t mutex;  // Mutex lock

void* function(void* arg) {
    pthread_mutex_lock(&mutex);  // Acquire the mutex lock
    // Critical section starts
    // ...
    // Critical section ends
    pthread_mutex_unlock(&mutex);  // Release the mutex lock
    return NULL;
}

int main() {
    pthread_mutex_init(&mutex, NULL);  // Initialize the mutex

    pthread_t thread1, thread2;
    pthread_create(&thread1, NULL, &function, NULL);
    pthread_create(&thread2, NULL, &function, NULL);

    pthread_join(thread1, NULL);
    pthread_join(thread2, NULL);

    pthread_mutex_destroy(&mutex);  // Destroy the mutex
    return 0;
}
```

In this example, the `pthread_mutex_lock` function locks the mutex, and `pthread_mutex_unlock` unlocks it. If a thread tries to lock a mutex that is already locked, it will block until the mutex becomes available.

### 3. Semaphore

Semaphores are more general than mutexes and can be used for a wider range of synchronization problems. A binary semaphore can be used similarly to a mutex. Here is an example in C using POSIX semaphores:

```c
#include <semaphore.h>

sem_t sem;  // Semaphore

void* function(void* arg) {
    sem_wait(&sem);  // Decrement the semaphore and wait if it's zero
    // Critical section starts
    // ...
    // Critical section ends
    sem_post(&sem);  // Increment the semaphore, signaling other threads
    return NULL;
}

int main() {
    sem_init(&sem, 0, 1);  // Initialize the semaphore with value 1

    pthread_t thread1, thread2;
    pthread_create(&thread1, NULL, &function, NULL);
    pthread_create(&thread2, NULL, &function, NULL);

    pthread_join(thread1, NULL);
    pthread_join(thread2, NULL);

    sem_destroy(&sem);  // Destroy the semaphore
    return 0;
}
```

In this example, `sem_wait` decrements the semaphore. If the semaphore's value is zero, the calling thread blocks until it becomes available. `sem_post` increments the semaphore and wakes up a blocked thread if any.