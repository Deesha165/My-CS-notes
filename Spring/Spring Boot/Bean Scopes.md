- what are bean scopes?
   1- singleton
   2- prototype
   3- request
   4- session
- singleton:
   - default scope
   - only one instance per IOC
   - Eagerly initialized by IOC (means at the time of application start up object is created)
-  Application:
   - similar to singleton but it is only one instance per multiple running IOCs (one instance shared among them)
   - Application scope is specifically tied to the **ServletContext** in web applications.
- Prototype:
   - Each time new object is created 
   - It is lazily initialized meaning that object is created only when it is required
- request:
   - new object is created for each HTTP request
   - lazily initialized
- session
   - New object is created for each HTTP session
   - Lazily initialized
   - when user accesses any endpoint, session is created
   - remains active till it doesn't expire
