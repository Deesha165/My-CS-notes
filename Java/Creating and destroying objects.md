- Consider static factory methods instead of constructors
- advantages of static factory methods:
    1- unlike constructors, they have names.
    2- unlike constructors, they are not required to create a new object each time they’re invoked.
    3- unlike constructors, they can return an object of any subtype of their return type.
    4- hiding complex creation logic.
    5- dynamic behavior : the class of the returned object can vary from call to call as a function of the input parameters.
- Consider builder when faced with many constructor parameters.
- the Builder pattern is a good choice when designing classes whose constructors or static factories would have more than a handful of parameters, especially if many of the parameters are optional or of identical type. Client code is much easier to read and write with builders than with telescoping constructors, and builders are much safer than JavaBeans.
- ##  The Problem: Telescoping Constructor Anti-pattern

When a class has many optional parameters, using constructors alone leads to either:

###  A telescoping constructor chain:

java

CopyEdit

`public class User {     public User(String name) {}     public User(String name, int age) {}     public User(String name, int age, String address) {}     public User(String name, int age, String address, String phone) {} }`

Using this is awful:

java

CopyEdit

`User user = new User("Alice", 25, null, null);`

- Confusing: Which `null` is for what?
    
- Hard to read and maintain.
    
- Adding a new parameter breaks existing code.
    

---

## ✅ Option 2: JavaBeans (setters)

java

CopyEdit

`User user = new User(); user.setName("Alice"); user.setAge(25);`

But this has **drawbacks**:

- ❌ Object is mutable (bad for thread safety or consistency).
    
- ❌ No guarantee that object is valid before use (you can forget to call a setter).
    
- ❌ Can lead to inconsistent state.
    

---

##  Solution: Builder Pattern

The **Builder Pattern** is designed to:

- Keep object **immutable** (like constructor).
    
- Allow **optional parameters** (like setters).
    
- Provide **readable code** with **method chaining**.
    

---

###  How it works

1. Create a **static nested class `Builder`**.
    
2. Provide setter-like methods on `Builder`, but returning `Builder` (`this`) for chaining.
    
3. `build()` constructs the object with all values set at once.
    

---
- The best approach to apply singleton is using enum due to reasons satisfied in enumsbut even i used rflection to ovveride and create instance it would throw exception:
   1- thread safety
    2- Serialization safe
    3- protection against reflection
    4- concise and clear

- Enforce non instantiability with a private constructor
- An object can always be reused if it is immutable
- Eliminate obsolete object references
- 