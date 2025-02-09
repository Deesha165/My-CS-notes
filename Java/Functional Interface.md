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