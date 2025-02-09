- it is Java API or an interface to
   1- make connection to DB
    2- Query DB 
    3- and process the result

- actual implementation is provided by the database driver
- plain JDBC  result in much boiler code:
    1- driver class loading
    2- db connection making
    3- exception handling
    4- closing of db connection and other like statement 
    5- manual handling of db connection pooling

- that is motivation for spring boot jdbc that uses jdbc Template:
   1- driver class loading at application startup
   2- db connection making and handled by jdbc Template 
   3- Exception handling is more detailed now
   4- closing of db connection using jdbc Template
   5- Manual handling of connection pooling using HikariCP
   