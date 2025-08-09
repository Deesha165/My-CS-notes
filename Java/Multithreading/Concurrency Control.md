- Dirty Read: if transaction A read data written by transaction B and transaction B rolls back then whatever data read by A it is dirty now.
- Non repeatable read: if transaction A reads the same row several time and there is a chance to read different value.
- Phantom read: if transaction A, executes same query several times and there is a chance that is rows returned are different.
- 
![[isolation levels.png]]   - Optimistic concurrency control: uses Read Committed isolation level and version, no possibility of deadlock
- Optimistic locking assumes **conflicts are rare**, so it **doesn’t lock** the data when it is read. Instead, it uses a mechanism (like a **version number** or **timestamp**) to detect if the data has changed before writing.
- Pessimistic concurrency control: uses Repeatable Read or Serializable and there is possibility of deadlock
- Pessimistic locking assumes **conflicts are likely**, so it **locks the data immediately** when someone accesses it, preventing others from reading or writing until the lock is released.