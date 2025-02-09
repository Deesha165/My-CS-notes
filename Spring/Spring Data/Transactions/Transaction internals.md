- Transaction management in spring uses AOP 
  1- use point cut expression to search for the method which has @Transactional
  @within("org.springframework.transaction.annotation.tranasactional")
  2- when matching occur run around type advice and advice is invokeWithinTransaction that exist in TransactionalInterceptor class
- @Transactional can be applied on class level or method level
- activating transaction management by annotation @EnableTransactionManagement but it is configured by spring boot directly using @SpringBootApplication
- Transaction achieve ACID properties:
  1- Atomicity: Ensure all operations inside transaction are completed successfully or not
  2-  Consistency: Ensure Db state before and after transaction are consistent
  3- Isolation: Ensure that running transactions in parallel doesn't interfere with each other
  4- Durability: Ensure commited transaction not lost despite system failure or crash
- transaction can be:
    - declarative using annotation @Transactional 
    - programmatic through code and it is more flexible but difficult to maintain
- Propagation: when we try to create new transaction it first checks propagation value set and this tell whether we have to create new transaction or not
- default propagation is required
- propagation types:
   1- required(default): if(parent trans exist ) use it else create new one
   2- required_new :
      if(parent trans exist)
      {
         suspend the parent transaction
         create new transaction and execute second method and once it is finished 
         resume the parent transaction
      }
      else  create new transaction
    3- supports:
    if(parent trans exist)
    {
     use it
    }
    else execute the method without transaction
    4- not support:
      if(parent trans exist)
      {
         suspend the parent transaction
        execute method without transaction
         resume the parent transaction
      }
      else  execute methode without transaction
  5- mandatory: parent transaction should be present
     if(parent trans exist)
     {
     use it
     }
     else throw exception
  6- Never: is inverse of mandatory if parent transaction exist throw exception
     if(parent trans exist)
     { 
     throw exception
     }
     else execute the method without any transaction
 
 
  