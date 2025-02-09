- Why core thread size is 2 not 10 , 15 or more (important question)?
   - max and min size of threads in thread pool depend on many factors:
     1- CPU Cores: if you have more threads than CPU cores it makes OS schedule more tasks so more threads must take turn on CPU cores meaning more **context switching** which make performance overhead due to saving state of running thread and loading state of the newly switched one
       2- JVM memory : every thread initiated allocate size in memory for(registers, stack and so on) and all inside JVM and JVM memory space is limited so more threads can't be aford by JVM
       3- Task Nature: it depends if it is CPU intensive or I/O intensive as if it is CPU intensive we need less threads to deal with but if it is I/O intensive the thread become idle as it is waiting and in that case we need more threads in thread pool
       4- Concurrency requirments
       5- memory requirments
        6- throughput 
- what is thread pool? 
    - it is a collection of threads used to perform submitted tasks
    - creating new thread takes some time so thread pool has already created threads and they are reused
- what is importance of thread pool? 
   1- Thread creation time can be saved: as creation of thread takes time
    2- overhead of managing life cycle of thread is removed: thread pool abstracts management of life cycle of thread
    3-  increased performance: control of number of threads so context switching time is less
### **What is Context Switching for Threads?**

**Context switching** refers to the process where the **CPU switches from executing one thread to another**. This involves saving the state of the currently running thread (so it can resume later) and loading the state of the next thread to be executed.

Each thread has its own **context**, which includes:

1. **Registers** – the values of the CPU registers for that thread.
2. **Program Counter** – the address of the next instruction to be executed.
3. **Stack** – the call stack, including function parameters, local variables, etc.
4. **Other CPU states** – like flags or status registers.

### **Steps in a Context Switch:**

1. **Save the state** of the currently running thread (its context).
2. **Load the state** of the next thread to run (its context).
3. The **CPU begins executing** the new thread from where it last left off.
### **How Increasing Number of Threads Affects Context Switching**

As you **increase the number of threads**, **context switching** becomes more frequent, and the associated **performance overhead** increases. Here’s why:

1. **More Threads, More Context Switches**
    
    - **More threads** mean that the OS has to **schedule** more tasks, which means it will have to **switch between threads** more frequently.
    - When there are **more threads than available CPU cores**, the OS must **context switch** more often to allow each thread to run on the CPU.
2. **CPU Time Split Between Threads**
    
    - Each thread gets a **smaller slice of CPU time**, especially if the number of threads exceeds the number of CPU cores.
    - The **frequent switching** between threads leads to **increased context switch overhead**, as each thread needs its state saved and loaded during every switch.
3. **Diminishing Returns**
    
    - Initially, adding more threads can increase concurrency and performance. However, when the number of threads exceeds the number of available CPU cores, you get **diminishing returns**.
    - The overhead of switching between threads can exceed the **work done** by the threads, leading to **performance degradation**.
    - For example, if your machine has **4 cores** and you create **100 threads**, the threads will constantly be switched, but only 4 can run at once, increasing the **time spent in context switching**.
4. **Thread Contention**
    
    - When many threads try to access the same resource (e.g., memory, I/O), **contention** occurs. If the threads are frequently blocked, more context switches happen as threads are paused and resumed, adding overhead.
5. **Cache Misses**
    
    - **More threads** mean that the CPU cache can be less effective because threads may be working on different memory locations. As a result, **cache misses** increase, leading to slower execution and more context switching between cached data and slower memory.

---

### **Thread Pool and Performance: Why It Helps**

A **thread pool** is a collection of pre-created worker threads that can be reused to handle multiple tasks. By **using a thread pool**, you can **manage threads more efficiently** and reduce the performance issues caused by context switching. Here's how:

---

### **1️⃣ Reduces the Overhead of Creating and Destroying Threads**

- **Thread creation** and **destruction** are expensive operations. If you constantly create and destroy threads, the overhead of these operations can severely degrade performance.
- **Thread pools** create a fixed number of threads at the start and reuse them to handle tasks. This reduces the need for frequent thread creation and destruction, leading to **less overhead**.

---

### **2️⃣ Limits the Number of Concurrent Threads**

- **Thread pool** has a **limited number of threads** (often set to the number of available cores or a specific number based on the workload).
- By limiting the number of threads that can execute at once, it prevents the system from being **overwhelmed** by a large number of threads, which can cause **too many context switches**.
- With a **limited number of threads**, only a specific number of threads are actively running, which minimizes the overhead of **context switching** between threads.

---

### **3️⃣ Optimizes Task Scheduling**

- **Thread pools** allow better control over how tasks are executed:
    - Tasks are **queued** and assigned to threads as they become available, allowing for **efficient use of CPU time**.
    - The pool can **prioritize tasks**, handle **shorter tasks** quickly, and avoid running **unnecessary threads**, reducing unnecessary switches.
- **Fairness**: The pool ensures that each task gets its chance to execute without overwhelming the system with too many threads.

---

### **4️⃣ Prevents Thread Starvation**

- Without a thread pool, there may be cases where certain threads are left waiting for a long time while others get executed. This can lead to **thread starvation**.
- A thread pool can help prevent this by ensuring **tasks are evenly distributed** and **fairly allocated** across available threads, improving **overall efficiency**.

---

### **5️⃣ Reduces the Need for Synchronization**

- In many concurrent applications, the threads need to access shared resources, which often involves **locking** (e.g., using mutexes).
- **Locks** can result in **context switches** if threads are blocked waiting for a lock to be released. If too many threads are trying to access a resource, it causes **high contention**, leading to more context switches.
- A **thread pool** can help by controlling the number of threads running concurrently, **reducing contention** and the need for synchronization, which in turn reduces the overhead of context switching.

---

### **6️⃣ Helps with CPU Resource Management**

- The OS is often better at managing the CPU when there is a fixed number of threads (as in a thread pool).
- When there are too many threads, the operating system's scheduler can spend too much time managing them, rather than executing tasks. The **thread pool** reduces this load and keeps the CPU working on actual tasks rather than managing excessive threads.

---

### **How a Thread Pool Improves Performance:**

#### **Without Thread Pool:**

- Create many threads.
- High context switch frequency.
- Overhead due to thread creation and destruction.
- Increased contention for resources (e.g., CPU time, memory).
- Poor CPU utilization if too many threads are created.

#### **With Thread Pool:**

- Use a fixed number of threads.
- Reduced context switching (as there are fewer threads).
- Reuse threads to handle tasks.
- Improved CPU utilization and resource management.
- Better task scheduling and fairness.
---------------------------------------------------
- Core pool size is the number of threads are initially created and left at the pool even if they are idle
- what are types of tasks? 
   1- CPU intensive
1. 
    2- I/O intensive like reading from files and DB in that case thread may be idle 
 - ### **Thread Pool Life Cycle in Java**
A **ThreadPoolExecutor** in Java goes through a **well-defined lifecycle** with the following **states**:
## **1. RUNNING (Active State)**

- The thread pool **accepts new tasks** and **processes queued tasks**.
- Threads are created **up to the core size** (`corePoolSize`).
- If the queue is full, new threads are **spawned up to maxPoolSize**. 
## **2. SHUTDOWN (Graceful Shutdown)**

- The thread pool **stops accepting new tasks** but **continues processing existing tasks**.
- **Threads finish their work and terminate gracefully**.
## **3. STOP (Immediate Shutdown)**

- **All running threads are interrupted** immediately.
- The queue is **cleared** (pending tasks are discarded).
## **4. TERMINATED (Fully Stopped)**

- The thread pool has **fully shut down**.
- No running tasks, no active threads.
- Calling `submit()` now will throw an exception.

