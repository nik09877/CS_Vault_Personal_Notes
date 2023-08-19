# Spring, Spring Boot Annotations Cheat sheet | by Suresh Kumar | Medium
As known there are a number of Annotations provided by Java’s Spring, Spring Boot Framework, and it would be quite difficult to remember all. Hence I had comeup with below Spring, Spring Boot Annotations Cheat Sheet, to help the readers.

[Click here to explore my Spring, Spring Boot course with 12 hours Video, with downloadable source code examples](https://www.udemy.com/course/learn-java-spring-spring-boot-spring-boot-jpa-security/?referralCode=2A01658389D8880E75DE)

**Spring Core related Annotations:**

**@Bean** — method annotated with @Bean creates and returns Bean. Spring Container calls such methods, automatically.

**@PostConstruct** & **@PreDestroy** — indicates Bean life cycle methods

**@Configuration** — Class annotated with @Configuration has methods annotated with @Bean or has data members annotated with @Value

**@**[**Scope**](https://medium.com/u/eb2633533480?source=post_page-----de546e0b03d4--------------------------------) — indicates Scope of a Bean such as Singleton, Prototype, Session, etc…

**@Lazy** — indicates that Bean needs to be created on Demand only, i..e when there is explicit request

**@Autowired** — indicates Bean needs to be automatically created by Spring Container.

```Java
class EmployeeController{
@Autowired
EmployeeService eService;
//Remaining code which directly uses eService, as it's automatically created using Autowired
}
```


**@Qualifier** — used along with @Bean or @Autowired to avoid ambiguity during Bean creation by Spring Container

**@Primary** — When there are multiple qualified Beans, priority is given to the Bean annotated with @Primary

**@Component** — indicates a class as Component, so that it can be recognized by @ComponentScan, automatically. As known, all Component classes are automatically scanned and loaded by Spring Container.

**@ComponentScan** — scans one or more packages/subpackages for Components. This annotation is part of @SpringBootApplication, however it may be used separately as well.

**@Service** — Components in Service Layer need to be annotated with @Service

```Java
@Service
public class EmployeeService{
  //define methods exposed by the Service Layer
}
```


**@Repository** — Components in Repository Layer need to be annotated with @Repository

**@SpringBootApplication** — This annotation is used with main class of Spring Boot Application. @SpringBootApplication is combination of @ComponentScan, @EnableAutoConfiguration and @Configuration

**@Value** — Data members of a Configuration class are automatically loaded from Configuration file(such as application.properties) or initialized to a specific value, as shown below.

```Java
@Service
public class EmployeeService{
//cname property is automatically retrieved from application.properties file
@Value("${cname}")
private String company_name;
//initialize tax_id with ABCDEF123
@Value("ABCDEF123")
private String tax_id;
//methods which uses above fields...
}
```


**@ConfigurationProperties** — Class annotated with @ConfigurationProperties automatically loads bunch of data members(with matching property names)from Configuration file(such as application.properties), as shown below

```Java
@Component
@ConfigurationProperties
public class CompanyDetails{
  private String company_name;
  private String company_ceo;
  private String head_office_city;
    //methods defined by this class...
}
```


```Java
#contents of application.properties file
company_name = WXYZ Company 
company_ceo = Some One
head_office_city = Bangalore
#other configuration properties can be specified here
```


**@PropertySource** — Class Level Annotation, generally along with @Configuration annotation. @PropertySource lets developers to specify custom Property file name(s)(other than application.properties), from which Configuration properties can be loaded, in runtime, as shown below

```Java
@Configuration
@PropertySource("classpath:myfilename.properties")
class SomeConfigurations{
  //Spring Boot automatically looks for myfile.properties file, for required Configuration properties
}
```


**@Profile** — can be used with Configuration or Component classes, to indicate this specific class is available, when application is running in specific profile mode, such as dev, test or production

**REST API related Annotations:**

**@RestController** — Class annotated with @RestController exposes REST End points, as shown below

```Java
@RestController
class EmployeeController{
@GetMapping("/allemployees")
List<Employee> getEmployees(){
//return List of Employees
}
//More REST end points can be exposed
}
```


**@RequestBody** — used with method parameter of REST end point. This annotation automatically deserializes the body(of Http request) into a Model or Entity object.

```Java
@RestController
class EmployeeController{
@PostMapping("/create")
ResponseEntity<Employee> createEmployee(@RequestBody Employee emp){
//code to save emp object in DB
}
//other REST end points
}
```


**@PathVariable** — used with method parameter of REST end point. It automatically retrieves a Path variable into the method parameter of REST end point.

```Java
@RestController
class EmployeeController{
@GetMapping("/employee/{eid}")
Employee getEmployee(@PathVariable("eid") Integer empid){
//code to fetch Employee from DB
}
//other REST end points
}
```


**@RequestParam** — used with method parameter of REST end point. It automatically retrieves a Query parameter into the method parameter of REST end point.

```Java
@RestController
class EmployeeController{
@GetMapping(“/emp”)
Employee getEmployee(@RequestParam Integer empid){
//code to fetch Employee from DB
}
//other REST end points
}
```


**@RequestHeader** — used with method parameter of REST end point. It automatically retrieved value from a specified HTTP header and populates the value into the method parameter.

REST End points are annotated with any of below annotation, to indicate specific HTTP method

1.  @RequestMapping
2.  @GetMapping — to retrieve one or more resource(such as Employee) details
3.  @PostMapping — to create a new resource
4.  @PutMapping — to update an existing resource
5.  @DeleteMapping — to delete an existing resource

```Java
@RestController
class EmployeeController{
@DeleteMapping("/emp")
Employee removeEmployee(@RequestParam Integer empid){
//code to delete Employee from DB
}
//other REST end points
}
```


REST API Exception Handling annotations:

**@ExceptionHandler** —method annotated with this annotation, is automatically called whenever a specific Exception(either inbuilt or custom) occurs. This method returns appropriate Exception details to the Client.

**@ControllerAdvice** — class annotated with this annotation, has methods annotated with @ExceptionHandler

@Valid — used with @RequestBody , to automatically validate the data members during deserialization. This annotation works along with Validation rules such as @NotNull, @Max, etc… used with fields of Entity class

```Java
@RestController
class EmployeeController{
@PostMapping("/emp")
Employee createEmployee(@Valid @RequestParam Employee emp){
//code to create new Employee in DB
}
//other REST end points
}
```


[Click here to explore my Spring, Spring Boot course with 12 hours Video, with downloadable source code examples](https://www.udemy.com/course/learn-java-spring-spring-boot-spring-boot-jpa-security/?referralCode=2A01658389D8880E75DE)

**Spring Boot Data JPA related annotations:**

**@Entity** — class which need to be mapped with underlying DB Table

**@Table** — Used along with @Entity annotated, to specify custom name for DB Table(by default DB Table has same name as Entity Class name)

**@Column** — Used with Data members of Entity class, to indicate a Column of DB Table.

Data field Validation related — @NotNull, @Max, @Min, @Positive, @Negative, etc…

**@Query** — to specify Custom Query String(native or JPQL query), along with method declaration in Repository interface.

Entity class relationships — @OnetoOne, @OnetoMany, @ManytoOne, @ManytoMany

**Security related Annotations:**

**@CrossOrigin** — Can be used with Class or method(s), indicating by which Origins(domain name or domain name patterns) the REST end points can be invoked.

Below annotations used for method level Security

1.  **@Secured**
2.  **@PreAuthorize**
3.  **@PermitAll**

**AOP related Annotations:** Aspect Oriented Programming is used to separate Cross Cutting concerns(such as Logging, Security, etc…), from Business Logic. AOP is used only in selected Spring Boot Projects.

**@Aspect** — to specify that a class is Aspect, which holds Cross cutting concerns

**@Pointcut** — to specify Pointcut expressions

**@Before** — to specify a method is Before Advice

**@After** — to specify a method is After Advice

**@Around** — to specify a method is around Advice

As known, all advice methods are in an Aspect class.

**Caching related Annotations:**

@EnableCaching — Used along with @SpringBootApplication, which enables the application to perform Cache related operations

@Cacheable — Adds an entry to the Cache

@CachePut — Updates an existing entry in the Cache

@CacheEvict — Removes one or more entries from the Cache

**Scheduling related Annotations:** It’s quite common that an Enterprise application may need some functionality to be executed periodically. For such requirements, below Scheduling related Annotations are used

**@EnableScheduling** — Enables the Application to use Scheduler. This annotation is used along with @SpringBootApplication.

**@Scheduled** — This annotation is used with a method, which needs to be automatically executed periodically at specific points of time.

**Transaction related Annotations:**

@Transactional — Used by class/interface or method, indicates the method(s) is executed under a Transaction

[Click here to read my post on, Commonly used Spring Boot Starter dependencies, classes, interfaces](https://medium.com/@sureshkumar_95502/spring-boot-starters-classes-interfaces-part-1-1607a4e65297)

[Click here to explore my Spring, Spring Boot course with 12 hours Video, with downloadable source code examples](https://www.udemy.com/course/learn-java-spring-spring-boot-spring-boot-jpa-security/?referralCode=2A01658389D8880E75DE)

Thanks for reading this Post, and Happy Learning!!!

Read my other post(s):

[Create Custom Collections by extending an existing Collection class](https://medium.com/@sureshkumar_95502/how-to-create-custom-java-collection-by-extending-from-an-existing-collection-class-3682e6d0ad8)

I will be sharing Spring Cloud related Annotations, shortly.