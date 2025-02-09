1- what is dependency injection?
 - design strategy used to make classes independent of its dependencies
 - it helps to git red of concrete implementations and providing dependencies from external resources
 2- what are ways of dependency injection?
  - Constructor injection
  - field injection
  - setter injection
1- field injection: fields are injected directly in class and spring uses reflection to iterate over class fields and resolving dependencies, **so you can initialize the class before resolving its dependencies**
- advantages: very easy and simple 
- disadvantages: 
     - can't be used with immutable fields
     - chances of null pointer exceptions if we some how initialized object which has dependency and accessed it it would be null (very important point)
     - Testability is difficult
2- setter injection: dependency is set into fields using setter method
 - advantages: 
     - dependency can be changed any time after object creation
     - easier testability as we can pass mock object in the dependency easily
- disadvantages:
     -field can't be final (immutable)
     - difficult to read and maintain
3- constructor injection(recommended): dependency get resolved at the time of initialization of the object itself
  - advantages:
    - all mandatory dependencies are created at the time of initialization itself makes 100% sure that object is fully created with its dependencies.
    - we can create immutable objects using constructor injection
    - fail fast : if there is missing dependency it will fail during compilation rather than runtime
    - easier testability as mock can be passed easily in dependency

3- what are common issues in dependency injection?
 - Circular dependency
       solutions:
          - refactoring by taking part of code they depend on each other and put in separate class and make them depend on it
          - Lazy instantiation using @Lazy
          - using @PostConstruct 
 - unsatisfied dependency: meaning many instances of same class and spring doesn't know which one to inject
     solutions:
      - use @Primary annotation
      - use @Qualifier annotation