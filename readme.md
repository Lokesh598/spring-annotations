## Annotations: 
  Java 1.5 introduced annotations and now it’s heavily used in Java EE frameworks like Hibernate, Jersey, and Spring. 
  Java Annotation is metadata about the program embedded in the program itself.

### Spring Annotation

### Spring MVC Annotation
  - @Controller
  - @RequestMapping
  - @PathVariable
  - @RequestParam
  - @ModelAttribute 
  - @RequestBody and @ResponseBody
  - @RequestHeader and @ResponseHeader
    
### Spring Boot Annotation
  - @SpringBootApplication
  - @EnableAutoConfiguration
  - @Configuration
  - @ComponentScan
  
  Spring boot introduced @SpringBootApplication annotation. This single annotation is equivalent to using @Configuration, @EnableAutoConfiguration, and @ComponentScan.
  
  As a result, when we run this Spring Boot application, it will automatically scan the components in the current package and its sub-packages. 
  Thus it will register them in Spring's Application Context, and allow us to inject beans using @Autowired.

### Stereotype annotation
  1. @Component
  2. @Service
  3. @RestController/ @Controller
  4. @Repository

### REST API related Annotations:
  - @RestController
  - @RequestMapping
  - @GetMapping
  - @PostMapping
  - @PutMapping
  - @DeleteMapping
  - @RequestMapping
  - @RequestBody
  - @PathVariable
  - @RequestParam
  - @ControllerAdvice
  - @ExceptionHandler
  
### Spring Data JPA related annotations:
  - @Entity
  - @Table
  - @Column
  - @Transactional
  #### Entity class relationships
    - @OnetoOne
    - @OnetoMany
    - @ManytoOne
    - @ManytoMany
    
### Security related annotations:
  - @CrossOrigin
  - @Secured
  - @PreAuthorize
  - @PermitAll

### Caching related annotations:
 - @EnableCaching
 - @Cacheable
 - @CachePut
 - @CacheEvict

### Aspect Oriented annotations:
 - @Aspect
 - @Pointcut
 - @AfterRunning
 - @AfterThrowing
 - @Around
 - @Before

####
  @Component: this is the root annotation. Remaining three annotaions derived from @Component annotation.
  
  Now question is why we need Remaining three annotations if we can use @Component every where?
  Yes We can use @Component everywhere where we need these but they denote that which class have what purpose. 
  for example we have @RestController, So its tell us what is this class use for. like we rest method in this class. So annotaion makes easy to identify the class.
  
  Same we have @Service annotation tells us that it is my service class and I have to write my business logic here.
  
  @Repository annotaion where we write database logic. 
  So three different annotation to define the role of classes.
  
#### Spring core related Annotations:
  - @Configuration
  - @Bean
  - @Autowired
  - @Qualifier
  - [@Primary](https://www.baeldung.com/spring-qualifier-annotation#:~:text=%40Qualifier%20vs%20%40Primary,the%20same%20type%20are%20present.)
  - @Lazy
  - @Value
  - @PropertySource
  - @ConfigurationProperties
  - @Profile
  - @Scope
  
  
  we use @Bean inside a @Configuration class.
 
  @Autowired: Spring Autowire annotation used to automatic injection of beans.
  if remove the @autowired annotation spring not able to create object of it and it will create NullPointerException. example in spring boot application we use it generally in controller class.
  
  @Qualifier: Spring @Qualifier annotation is used in conjunction with Autowired to avoid confusion when we have two of more bean configured for same type.
  
  We use @Qualifier in Spring to autowire a specific bean among same type of beans, where as @Primary is used to give high preference to the specific bean among       multiple beans of same type to inject to a bean.
  
  There's another annotation called @Primary that we can use to decide which bean to inject when ambiguity is present regarding dependency injection.

  This annotation defines a preference when multiple beans of the same type are present. The bean associated with the @Primary annotation will be used unless       otherwise indicated.
  
##### @Autowiring by @Qualifier
 Let's see how we can use @Qualifier annotation to indicate the required bean.
 First we difine two beans of type of formatter 
      
```java
      @Component("fooFormatter")
      public class FooFormatter implements Formatter {
        public String format() {
          return "foo";
        }
      }
```

```java
@Component("barFormatter")
public class BarFormatter implements Formatter {
    public String format() {
        return "bar";
    }
}
```

here we have two different classes which implemetning same interface. lets inject formatter in Forservice class.
```java
public class FooService {
    @Autowired
    private Formatter formatter;
}
```
In our example, there are two concrete implementations of Formatter available for the Spring container. As a result, Spring will throw a NoUniqueBeanDefinitionException exception when constructing the FooService:
...........
We can avoid this by narrowing the implementation using a @Qualifier annotation:
```java
public class FooService {
    @Autowired
    @Qualifier("fooFormatter")
    private Formatter formatter;
}
```

When there are multiple beans of the same type, it's a good idea to use @Qualifier to avoid ambiguity.

Please note that the value of the @Qualifier annotation matches with the name declared in the @Component annotation of our FooFormatter implementation.
  
##### @Primary
we use @Primary to give higher preference to a bean when there are multiple beans of the same type.
we need @Primary to register multiple beans with same name.

