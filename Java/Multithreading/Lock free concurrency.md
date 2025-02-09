- what are ways to achieve concurrency?
  1- lock based mechanisms: synchronized, reentrant, read write, stamped and semaphore  
  2- lock free mechanisms: CAS operation (compare and swap) (Atomic Integer, Atomic Boolean, Atomic Long)
- To solve the problem of non atomicity due to threads we use two solutions:
   1- using synchronized 
    2- using lock free operation like in Atomic integers 
- lock free mechanism uses CAS : it is low level operation, atomic and supported by all processors
- it involves three parameters : memory location , expected value and new value
- CAS(Memory, Expected value, New value )
- CAS flow:
   1- load variable from main memory
    2- compare value from memory and expected one
     3- if match update new value in memory

- Volatile : ensures that read/write done from memory not cache which ensures consistency when more than one thread read data