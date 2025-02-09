### **Why It Persists Without @Transactional**

1. **Auto-Commit**:
    
    - The underlying JDBC connection automatically commits each SQL operation if no explicit transaction is defined.
    - This is why changes can persist even when you don’t annotate the method with `@Transactional`.
2. **Framework Defaults**:
    
    - Many frameworks (like Spring) configure Hibernate to work seamlessly with default transaction settings.
    - In the absence of an explicit transaction, operations are executed with short-lived transactions, each committing immediately after execution.
- Why it is not a good practice 
   1- lack of atomicity
   2- **Performance Overhead**:
    
    - Each operation requires starting and committing a new transaction.
    - For many operations, this adds significant overhead compared to using a single transaction for all operations.
    
    **Example**:
    
    - 100 updates executed without a transaction = 100 individual transactions.
    - 100 updates executed within a transaction = 1 transaction.

---

3. **Potential Deadlocks**:
    - When multiple independent operations interact with the same resources, they can create deadlock scenarios more easily without a single transactional boundary. 