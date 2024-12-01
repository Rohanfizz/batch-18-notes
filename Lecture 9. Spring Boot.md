### Notes for the First Class on Spring Boot

#### **1. Introduction to Spring Boot**

Spring Boot simplifies the development of Java applications by providing default configurations and eliminating boilerplate code. It is widely used for creating microservices and web applications.

---
#### *Using the Spring Initializr

1. **Open Spring Initializr:**
    - Navigate to [https://start.spring.io/](https://start.spring.io/).
2. **Fill in the Project Details:**
    - **Project:** Maven
    - **Language:** Java
    - **Spring Boot Version:** Choose the latest stable version (e.g., 3.1.0).
    - **Group:** Your organization name or domain (e.g., `com.example`).
    - **Artifact:** Your project name (e.g., `spring-boot-demo`).
    - **Name:** Project display name.
    - **Description:** Brief description (optional).
    - **Package Name:** Automatically derived from Group + Artifact.
    - **Packaging:** Choose `Jar` (default for most applications).
    - **Java Version:** Select the version installed on your system (e.g., 17).
3. **Add Dependencies:**
    - Use the search bar to find and add the required dependencies:
        - **Spring Boot Starter Web** (for web applications)
        - **Spring Boot Starter Data JPA** (for database access)
        - **H2 Database** (for an in-memory database)
        - **Spring Boot Starter Test** (for testing)

### **2. Understanding `pom.xml` in a Spring Boot Project**

#### **What is `pom.xml`?**

- **POM** stands for **Project Object Model**.
- It is an XML file that contains configuration information for Maven projects.
- It manages project dependencies, build configurations, and plugins.
---
## Application properties file

The `application.properties` file in a Spring Boot project is used to configure application-level settings. It is a simple text file where key-value pairs define configuration properties for your application.

---

### **Why Use `application.properties`?**

1. **Centralized Configuration:**
    - All configurable properties for the application are stored in one file.
2. **Ease of Customization:**
    - Properties can be overridden for different environments (e.g., development, staging, production).
3. **Automatic Integration:**
    - Spring Boot automatically reads this file during application startup.

---

### **Common Use Cases for `application.properties`**

1. **Server Configuration:**
    
```properties
server.port=8080
server.servlet.context-path=/api
```

- **`server.port`**: Sets the port for the application.
- **`server.servlet.context-path`**: Sets the base URL path for APIs.
2. **Database Configuration:**

```properties
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.username=sa
spring.datasource.password=
spring.datasource.driver-class-name=org.h2.Driver
```

3. **Logging Configuration:**

```properties
logging.level.org.springframework=DEBUG
logging.file.name=application.log
```
    
1. **Custom Application Properties:**
    
    ```properties
app.name=MySpringApp
app.version=1.0.0
```
    
5. **Enable/Disable Features:**
    
```properties
spring.h2.console.enabled=true
```
    
---
Before we start with activities, make sure your VsCode is ready with nesseary extensions:
1. Java Code Generators
2. Extension Pack For Java
3. Spring Boot Extension Pack
# Activity 1: Spring Data JPA + H2

1. Create a project with following dependencies:
	1. H2
	2. Data JPA
2. Create the Entity Class Student and add getters and setters.
```java
@Entity
public class Student {
 @Id
  private int id;
  private String name;
  private int testScore;
}
```
3. Create Repository Interface.
```java
@Repository
public interface StudentRepository extends JpaRepository<Student, Integer> {}
```
4. Create Unit Test to test the application.
```java
@Autowired
private StudentRepository repo;

@Test
void contextLoads() {
	Student input = new Student();
	input.setName("Rohan");
	input.setTestScore(123);
	input.setId(2);
	
	repo.save(input);
	Student output = repo.findById(2).get();
	assertNotNull(output);
}
```
## Learnings

- #### Annotations
    - **@Entity**: Marks the class as a JPA entity, mapping it to a database table.
    - **@Id**: Declares the primary key of the entity.
    - **@Repository**: Indicates the interface is a Spring Data repository, providing database interaction capabilities.
    - **@Autowired**: Enables dependency injection to inject required beans automatically.
    - **@Test**: Marks a method as a test case in the JUnit framework.
    - **@SpringBootTest**: Loads the full Spring application context for integration testing.
- #### Repository Methods
    - **`save(S entity)`**: Saves the given entity to the database.
    - **`findById(ID id)`**: Retrieves an entity by its primary key (returns an `Optional`).
    - **`findAll()`**: Returns all entities in the database as a list.
    - **`deleteById(ID id)`**: Deletes an entity by its primary key.
    - **`existsById(ID id)`**: Checks whether an entity exists with the given primary key.
    - **`count()`**: Returns the total number of entities in the database.
- #### Other Learnings
    - **Dependency Management**: Using Maven or Gradle to manage Spring Boot dependencies like H2 and Data JPA.
    - **H2 Database**: Hands-on experience with an in-memory database for testing.
    - **JPA Basics**: Understanding how entity classes and repositories simplify database interactions.
    - **CRUD Operations**: Gaining practical knowledge of Create, Read, Update, Delete operations.
    - **Testing with JUnit**: Writing robust tests to validate application functionality.
    - **Assertions**: Using `assertNotNull`, `assertEquals`, and other assertions to verify test results.
    - **Optional Handling**: Understanding how `Optional` can help handle null values safely.
    - **Rapid Prototyping**: Leveraging Spring Boot and H2 to build and test applications quickly.
    - **Spring Boot Layers**: Understanding how entities, repositories, and tests fit into a Spring Boot application's architecture.
___
# Activity 2: CRUD Rest API with MySQL DB
1. Create a connection with sql in mysql workbench.
2. Create DB and table in mysql using workbench
```mysql
create database mydb;
use mydb;

create table product (
id int NOT NULL AUTO_INCREMENT PRIMARY KEY,
name varchar(20),
description varchar(20),
price int
);

select * from product;
```
3. Create project using following dependencies
	1. MySql Driver
	2. JPA
	3. Web 
4. Create product model ( generate getters and setters for the model)
```java
@Entity
public class Product {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private int id;
  private String name;
  private String description;
  private int price;
}
```
5. Create a repository for Product model so that db interactions can be made
```java
@Repository
public interface ProductRepository extends JpaRepository<Product, Integer> {}
```
6. Create the Controller
> A **Controller** in a backend application is like a traffic cop for your app. Its job is to handle the requests that come from users (or their `browsers/apps`) and send back the appropriate responses.
```java
@RestController
public class ProductRestController {
  
  @Autowired
  ProductRepository repo;
  
  @RequestMapping(value = "/products/", method = RequestMethod.GET)
  public List<Product> getProduct() {
    return repo.findAll();
  }
  
  @RequestMapping(value = "/products/{id}", method = RequestMethod.GET)
  public Product getProductById(@PathVariable("id") int id) {
    return repo.findById(id).get();
  }
}
```
7. Configure the Data source. Note, DB username and DB password will be the one you configured while installing mysql.
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
spring.datasource.username=root
spring.datasource.password=rootroot
```
8. Implement other CRUD operations
## Learnings

### CRUD Rest API with MySQL DB
- **Setting Up MySQL**:
    - How to create a database and table in MySQL using MySQL Workbench.
    - Writing basic SQL commands like `CREATE DATABASE`, `CREATE TABLE`, and `SELECT`.
- **Database Integration**:
    - Understanding how to connect a Spring Boot application to MySQL using the `spring.datasource` configuration.
    - Using MySQL Driver dependency to enable communication between the application and the database.
- **JPA Model Features**:
    - **Auto-Generated IDs**: Use of `@GeneratedValue` with `GenerationType.IDENTITY` to let the database handle ID generation for each record.
- **Controller Basics**:
    - Understanding the role of a REST Controller in handling HTTP requests and sending responses.
    - Use of `@RestController` and `@RequestMapping` to map URL paths to Java methods.
    - Returning a list of objects (e.g., products) directly from the database using `findAll()`.
- **Repository Capabilities**:
    - Using JPA repository methods like `findAll()` to fetch all records from a table.
    - Extending the repository to handle CRUD operations (`save`, `findById`, `deleteById`, etc.).
- **Spring Boot Features**:
    - Configuring the application properties file for externalizing database credentials and URLs.
    - Leveraging the **Spring Boot Web** dependency to expose REST APIs.
- **Other Learnings**:
    - **CRUD Operations**: Creating, Reading, Updating, and Deleting records in the database through REST APIs.
    - **JSON Representation**: How Java objects are automatically converted to JSON when returned from a REST controller.
    - **Best Practices**: Keeping the controller focused on handling requests and delegating database interactions to the repository layer.
    - **API Testing**: Testing APIs using tools like Postman or browser extensions to verify endpoint functionality.
