1- what are ways of creating beans?
- @Component: "convention over configuration" creating object and adding to context
- @Bean
2- At what time these beans get created?
 - Eager: like singleton
 - Lazy: like prototype
3- What is Bean life cycle?
-> Application start->IOC container started -> Construct Bean -> Inject dependencies into constructed Bean->@PostConstruct -> Bean use-> @PreDestroy->Bean destruction
- When app starts spring boot invokes IOC container 
- IOC container make use of configurations and @ComponentScan to find classes which need beans
- Construct beans for scanned classes at application startup (if it is not lazy otherwise construct the bean when it is first requested only)
- Look for dependencies and inject them into Constructed beans
- now these objects are fully constructed you can perform actions after construction with @PostConstruct
- Use the bean
- then before destroying do actions with @PreDestroy
- destroying bean