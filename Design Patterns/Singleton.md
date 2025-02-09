- it targets creating only one object for the whole life time of the application
- it can be implemented in several ways:
   1- eager initialization: it is problem is allocating memory for static variable even if it is not used
   2- lazy initialization: instance is created once it is requested but it is problem also if two threads tried to create two instances at the same time
    3- synchronized: put lock on the method for one thread to pass and then other one go inside after unlocking , it is thread safe but it is so slow
    4- double check locking: similar to synchronized but putting lock when instance is null only which improves performance
    5- bill pugh  :  it uses static inner class to depending class loader mechanism that classes are loaded when they are accessed so 
       - **Inner static class is NOT loaded when the application starts** because **it is only loaded when first accessed**.
    - This enables **lazy initialization**, ensuring that the singleton instance is created **only when needed**.
    -  In Java, a class is loaded into memory **only when it is first referenced**.
    - Class loading is **synchronized internally by the JVM** to prevent multiple threads from initializing the class multiple times.
    - This guarantees that **a class is loaded only once per ClassLoader**.
     