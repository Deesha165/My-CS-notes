- @ResponseBody:- to tell spring boot to that method return HTTP response body not HTML view
- @Controller:which is responsible for handling HTTP requests, processing user input, and returning a response.
-  @RestController: @Controller+ @ResponseBody
- @Component: -The `@Component` annotation is used to indicate that a class is a Spring-managed component (or bean). When you annotate a class with `@Component`, it tells Spring to automatically detect and register it as a bean in the Spring **IoC container**.
- @SpringBootApplication: - It is used as replacement for three anotations:
  1- @EnableAutoConfiguration: it enables Spring Boot auto- configuration mechanism.
  2- @ComponentScan: It scans the package where the application is located.
  3- @Configuration: It allows us to register extra beans in the context or import additional configuration classes.
- @Autowired: The `@Autowired` annotation is used to enable **automatic dependency injection**. It tells Spring to resolve and inject the required dependency automatically by type (default behavior).
- @RequestParam : to bind request parameter to controller method parameter.
- @PathVariable: to bind request parameter at path to controller method parameter
- @RequestBody; bind body of HTTP request (json object) to controller method parameter (java object) and this is done using serialization library Jackson or Gson
- @InitBinder: for customizing rules before binding 
- @ConditionalOnProperty: Bean is created conditionally, it consist of prefix, value forming key and having value forming value and look for key value pair in application.properties and if missing we can ignore or construct also.
    - advantages:
       - toggling of features
       - avoid clutering app context with unnecessary bean
       - save memory
       - reduce application startup time
    - disadvantages:
       - misconfiguration can happen
       - complexity when over used
       - complexity in managing
       - multiple bean creation with the same configuration brings confusion
- @Value: binds values from application.properties 