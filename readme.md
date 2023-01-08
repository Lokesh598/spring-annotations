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

#### Stereotype annotation
  1. @Component
  2. @Service
  3. @RestController/ @Controller
  4. @Repository
  
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
  - @Lazy
  - @Value
  - @PropertySource
  - @ConfigurationProperties
  - @Profile
  - @Scope
  
  
  we use @Bean inside a @Configuration class.
 
  @Autowired: Spring Autowire annotation used to automatic injection of beans.
  @Qualifier: Spring @Qualifier annotation is used in conjunction with Autowired to avoid confusion when we have two of more bean configured for same type.
  
  
