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

#### **Key Sections of `pom.xml`:**

1. **Project Metadata**
    - Includes the project name, version, description, and packaging type.
2. **Dependencies**
    - Lists libraries and frameworks needed for the project.
3. **Plugins**
    - Defines additional functionalities like code compilation and packaging.

#### **Example `pom.xml` for a Spring Boot Application**

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>spring-boot-example</artifactId>
    <version>1.0.0</version>
    <packaging>jar</packaging>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.1.0</version>
    </parent>

    <dependencies>
        <!-- Spring Boot Starter for Web Applications -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <!-- H2 Database -->
        <dependency>
            <groupId>com.h2database</groupId>
            <artifactId>h2</artifactId>
            <scope>runtime</scope>
        </dependency>

        <!-- Spring Data JPA -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>

        <!-- Testing -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>
</project>
```

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

### **Example of `application.properties`**

```properties
# Server Configuration
server.port=9090
server.servlet.context-path=/myapp

# H2 Database Configuration
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driver-class-name=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=

# Hibernate (JPA) Settings
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

# Custom Application Properties
app.name=Spring Boot Demo
app.environment=development
```

---

### **Tips for Managing `application.properties`**

1. **Use Profiles for Environment-Specific Configurations:**
    
    - Use files like `application-dev.properties` and `application-prod.properties` for different environments.
    - Activate profiles using:
        
        ```properties
        spring.profiles.active=dev
        ```
        
2. **Secure Sensitive Information:**
    
    - Avoid hardcoding sensitive data like passwords; use environment variables instead.
3. **Default Properties:**
    
    - If `application.properties` is not found, Spring Boot uses default settings.

---

This file provides a foundation for flexible and efficient application configuration, allowing developers to focus on coding without worrying about hardcoded settings.
```


### **3. Dependency Injection in Spring**

#### **What is Dependency Injection?**

- A **design pattern** where a class's dependencies are provided (injected) by an external system, rather than being created within the class.
- Promotes loose coupling and easier testing.

#### **Example of Dependency Injection**

1. **Payment DAO Layer**
    - **Interface:** `PaymentDao`
    - **Implementation:** `PaymentDaoImpl`
    - Annotated with `@Repository` to indicate it's a Spring-managed bean.
2. **Service Layer**
    
    - **Interface:** `PaymentService`
    - **Implementation:** `PaymentServiceImpl`
    - Injects `PaymentDao` using `@Autowired`.
    - Annotated with `@Service`.
3. **Unit Test for Dependency Injection**
    
    ```java
    @SpringBootTest
    public class PaymentServiceTest {
    
        @Autowired
        private PaymentService paymentService;
    
        @Test
        public void testPaymentProcessing() {
            String result = paymentService.processPayment(100.0);
            assertEquals("Payment of 100.0 processed", result);
        }
    }
    ```
    

#### **Code Structure**

**`PaymentDao`**

```java
public interface PaymentDao {
    void savePayment(double amount);
}
```

**`PaymentDaoImpl`**

```java
@Repository
public class PaymentDaoImpl implements PaymentDao {
    @Override
    public void savePayment(double amount) {
        System.out.println("Payment of " + amount + " saved to the database.");
    }
}
```

**`PaymentService`**

```java
public interface PaymentService {
    String processPayment(double amount);
}
```

**`PaymentServiceImpl`**

```java
@Service
public class PaymentServiceImpl implements PaymentService {

    @Autowired
    private PaymentDao paymentDao;

    @Override
    public String processPayment(double amount) {
        paymentDao.savePayment(amount);
        return "Payment of " + amount + " processed";
    }
}
```

---

### **4. Using Spring Boot with H2 Database**

#### **What is H2 Database?**

- H2 is an in-memory database often used for development and testing.
- Fast, lightweight, and doesn't require installation.

#### **Steps to Integrate H2 in Spring Boot:**

1. **Add H2 Dependency in `pom.xml`:**
    
    ```xml
    <dependency>
        <groupId>com.h2database</groupId>
        <artifactId>h2</artifactId>
        <scope>runtime</scope>
    </dependency>
    ```
    
2. **Configure `application.properties`:**
    
```properties
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=password
spring.h2.console.enabled=true
```
1. **Entity Class Example:**
    
    ```java
    @Entity
    public class Payment {
        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        private Long id;
    
        private double amount;
    
        // Getters and Setters
    }
    ```
    
4. **Repository Example:**
    
    ```java
    @Repository
    public interface PaymentRepository extends JpaRepository<Payment, Long> {
    }
    ```
    
5. **Testing the Integration:**
    
    ```java
    @SpringBootTest
    public class PaymentRepositoryTest {
    
        @Autowired
        private PaymentRepository paymentRepository;
    
        @Test
        public void testSavePayment() {
            Payment payment = new Payment();
            payment.setAmount(200.0);
            paymentRepository.save(payment);
    
            assertNotNull(payment.getId());
        }
    }
    ```
    

---

### **Homework

1. Set up a basic Spring Boot project with `pom.xml`.
2. Create the `PaymentDao`, `PaymentService`, and integrate them into a Spring Boot application.
3. Configure H2 and create a sample table for payments. Implement a CRUD operation.