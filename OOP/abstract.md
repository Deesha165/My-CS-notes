- An **abstract method** is a method declared without an implementation (no method body). It is declared using the `abstract` keyword. Subclasses are required to provide an implementation for abstract methods.
- An **abstract class** in Java is a class that is declared with the `abstract` keyword. It serves as a blueprint for other classes and cannot be instantiated directly. Abstract classes are designed to be extended by subclasses, which provide concrete implementations for its abstract methods.
- #### Key Characteristics of an Abstract Class:

1. **Can Have Abstract Methods**: Methods without a body (just a declaration).
2. **Can Have Concrete Methods**: Fully implemented methods with a body.
3. **Cannot Be Instantiated**: You cannot create an object of an abstract class directly.
4. **Supports All Class Features**:
    - Fields (variables).
    - Constructors.
    - Methods (both abstract and concrete).
5. **Inheritance Requirement**: A subclass must implement all the abstract methods of an abstract class unless it is also declared abstract.
- A **default method** is a feature introduced in **Java 8** that allows you to provide a method implementation in an **interface**. Unlike abstract methods in interfaces, which must be implemented by a class, default methods come with a **default implementation**.
- 