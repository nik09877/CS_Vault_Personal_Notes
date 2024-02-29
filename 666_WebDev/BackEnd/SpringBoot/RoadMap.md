# Introduction to Spring Boot
- **Problem it Solved:**
  Spring Boot addresses the complexity of setting up and developing Spring applications by providing a convention-over-configuration approach. It aims to simplify the process of building production-ready applications with minimal effort.

- **Features and Advantages:**
  - Simplified configuration
  - Embedded server support (Tomcat, Jetty, Undertow)
  - Opinionated defaults to get started quickly
  - Microservices architecture support
  - Production-ready features (metrics, health checks, etc.)
  - Extensive set of annotations and pre-built templates

# Setting up Initial Spring Boot Project
- **Understand Layered Architecture**

# Understand Maven pom.xml a bit
(As Maven and Java are prerequisites for learning Spring Boot)

# Spring Boot Basic Topics
- **Annotations:**
  - `@SpringBootApplication`
  - `@Controller`
  - `@RestController`
  - `@RequestMapping`
  - `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`
  - `@Autowired`
  - `@Component`
  - `@Service`
  - `@Repository`
  - `@ComponentScan`
  - `@Configuration`
  - `@Value`
  - `@Qualifier`
  - `@Profile`
  - `@EnableAutoConfiguration`
  - `@Entity`
  - `@Transactional`
  - `@EnableCaching`
  - `@Async`
  - `@EnableScheduling` etc…

- **Dependency Injection and Beans**

# Spring Boot Data Access
- Spring JPA
- Spring JDBC
- QueryMethod

# RESTful APIs with Spring Boot

# Spring Boot Security
- **Securing our REST APIs**

# Spring Boot Logging
# Spring Boot Exception Handling
# Spring Boot Caching

# Spring Boot Interceptor

# Spring Boot Scheduling

# Spring Boot Testing
- **Mockito**

# Microservices topics in Spring Boot
- **Introduction to Microservices**

- **Service Discovery using Eureka:**
  - Microservice Registering

- **Tracing the Request in Multiple Microservices:**
  - Sleuth and Zipkin
  - Sleuth links the trace id with your request
  - Zipkin helps to visualize using the trace id

- **Spring Boot Profiles:**
  - Different properties based on profiles (like QA, Production)

- **Spring Cloud Config Servers:**
  - Its Configuration Management

- **Communication between Different Microservices:**
  - SYNC
  - ASYNC (messaging queue)

- **API Gateway**

- **Circuit Breaker**

- **CQRS (Command Query Responsibility Segregation)**

# Deployment and Containerization
- Creating executable JARs and WARs
