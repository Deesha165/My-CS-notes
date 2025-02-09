- What are process and thread?
- process is an independent program in execution each process has its memory space , resources and system state
- thread is the smallest unit of execution within a process or smallest sequence of instructions executed independently by the CPU
- 1 process contain multiple threads
- process take care of converting byte code into machine code 
- what are different ways to create thread?
   1- extending thread class
   2- implementing Runnable interface 
- why we have two ways to create threads? because a class can implement more than one interface but can extend only one interface
- Thread life cycle:
- New: thread has been created but it is in memory
- Runnable: thread is ready to run waiting for CPU time
- Running: when thread start executing the method
- Blocked: two different states for runnable thread to go into blocking state:
    1- I/O : like reading from file or database
    2- Lock acquired: if thread want to lock on a resource which is locked by another thread it has to wait
    - Releases all monitor locks
- Waiting: 
   - Thread goes into this state when we call Wait() method making it non runnable
   - it returns back to runnable when we call notify() or notifyAll() by another thread
   - Releases all monitor locks
- Timed Waiting: 
   - Thread waits for specific time and returns back to runnable state after specific conditions met like Sleep()
   - Don't release any monitor locks
- Terminated: life of cycle terminated and can't be returned again
- A **monitor lock** (or **intrinsic lock**) in Java is a mechanism that ensures **mutual exclusion** in multithreading, allowing only one thread to execute a **synchronized block** or **method** at a time for a given object.
- why Stop, Suspended, Resume are deprecated?
   - Stop: Terminates the thread abruptly , No lock release and no clean up resources
   - Suspend: put thread on hold for temporarily and no resources released too
   - Resume: resuming suspended threads 
   - could lead to issues like deadlock
- Join : when invoked on thread object it blocks thread and waits until this specific thread is finished, it is useful when we want to ensure that certain tasks are done before moving ahead 
- Daemon Thread:
    - Background threads that provide services to user threads.
    - is a thread alive whenever user thread is alive 
    - Used for **garbage collection, logging, and monitoring**.
- User Thread: Regular threads that perform application tasks.