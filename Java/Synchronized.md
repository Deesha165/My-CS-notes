**What does the `synchronized` keyword do?** The `synchronized` keyword in Java serves two main purposes:

- **Mutual Exclusion:** It ensures that only one thread can execute a synchronized method (or block) on the same object at a time.
- **Memory Visibility:** It ensures that when a thread exits a synchronized block, all changes made to shared variables inside that block are **visible to other threads** when they acquire the same lock.