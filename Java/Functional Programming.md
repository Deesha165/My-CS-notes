- what is functional interface? it is interface containing only one **abstract method**
- functional interface can has default, static or object class methods
- optional to annotate with @FunctionalInterface but if you done you restrict it for only one method and addition of more methods makes compilation error
- what are different ways to implement interface?
   1- through implements keyword
   2- anonymous class
   3- lambda expression (for functional interface only)
- what are types of functional interfaces?
  1- Consumer: represent Function that accept one input parameter and return nothing
  2- Supplier: Accept no input parameters and return one input
  3- Function: represent Function that accept one parameter and return result
  4- Predicate: 
- Use mapMulti over flatMap due to:
   1- Avoids Intermediate Streams: Unlike `flatMap`, `mapMulti` doesn’t create a stream for each element, which reduces object creation and memory pressure.
    2- Better Performance: It enables faster processing by avoiding unnecessary boxing/unboxing, stream creation, and function chaining.
    3- No Additional Allocations: You don't need to allocate intermediate collections or temporary lists — output elements are directly passed to the downstream consumer.
    4- Dynamic behavior: you can use as one to zero mapping as filter, or one to one mapping as map, or one to many mapping like flatmap.  
- When calling non-static methods, there is one main difference between a method reference and a lambda. A method reference calls the constructor immediately and only once (at method invocation (run()), the constructor is not called). On the other hand, lambdas are lazy. They call the constructor only at method invocation and at each such invocation (run()).
-  We can use lambda laziness and memoization to optimize highly computation operations
- 