- metadata that provide information about the code but do not affect its execution directly. They are used to give instructions to the compiler, frameworks, or runtime environments. Annotations help in tasks such as code analysis, configuration, and reducing boilerplate code.
- we can use this meta data at runtime and read by reflection
- pre defined ones and custom ones 
- Meta annotations: @Target restricts where to use the annotation
- @Retention tells how annotation will be stored in java
  1- RetentionPolicy.Source: annotations will be discarded by compiler and won't recorded in .class file
   2- RetentionPolicy.Class: annotations will be recorded in .class but will be ignored by JVM at runtime
    3- RetentionPolicy.Runtime: annotations would be recorded in .class and available during runtime and suitable for logic and usage of reflection can be done
-  