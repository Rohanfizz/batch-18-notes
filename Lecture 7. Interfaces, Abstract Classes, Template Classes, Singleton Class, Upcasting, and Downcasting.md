
#### **1. Interfaces**

- **Definition**:  
    An interface defines a contract with a set of methods that must be implemented by a class. It is typically used to achieve abstraction and multiple inheritance.
    
- **Key Points**:
    - It Doesn't have any body for methods
	- It is used to implement multiple inheritance 
	- Java add `public static final` keywords automatically in front of data members
	- `List<T>` is interface
    - Methods in an interface are abstract by default.
    - Can have static and default methods (Java 8+).
    - A class can implement multiple interfaces.
    - Also see [[Java Collections Framework]]
- **Syntax (Java)**:
    
    ```java
    interface PaymentGateway {
        void processPayment(double amount);
    }
    
    class PayPal implements PaymentGateway {
        public void processPayment(double amount) {
            System.out.println("Processing payment through PayPal: $" + amount);
        }
    }
    ```
    
- **Software Development Example**:  
    In an **e-commerce application**, you might define an interface `PaymentGateway` for integrating with multiple payment providers. Each provider (PayPal, Stripe, Razorpay) implements the interface with its specific logic.
    
- **Real-Life Example**:
	
	- **Interface**: A plug (interface) in your home defines a standard set of pins for all appliances.
	- **Implementation**: Devices like TVs and refrigerators provide their own logic for how electricity is used.
PaymentGateway.java
```java
public interface PaymentGateway {  
    // This function processes payment.  
    public void processPayment(int amount);  
  
    // This function prints the platform fees of the paymentGateway.  
    public void platformFees();  
}
```
Paytm.java
```java
public class Paytm implements PaymentGateway {  
    private final int platformFees = 10;  
  
    @Override  
    public void processPayment(int amount) {  
        int finalAmount = (amount + this.platformFees);  
        System.out.println("Total Amount to be payed is " + finalAmount);  
    }  
  
    @Override  
    public void platformFees() {  
        System.out.println("Platform fees for Paytm is: " + this.platformFees);  
    }  
  
}
```
Upi.java
```java
public interface Upi {  
    public void payViaUpi(int amount);  
}
```
Phonepe.java
```java
public class PhonePe implements PaymentGateway,Upi {  
    private final int platformFees = 20;  
  
    @Override  
    public void processPayment(int amount) {  
        int finalAmount = (amount + this.platformFees);  
        System.out.println("Total Amount to be payed is " + finalAmount);  
    }  
  
    @Override  
    public void platformFees() {  
        System.out.println("Platform fees for PhonePe is: " + this.platformFees);  
    }  
  
    @Override  
    public void payViaUpi(int amount){  
        int finalAmount = (amount);  
        System.out.println("Total Amount to be payed is " + finalAmount);  
    }  
}
```
Main.java
```java
public class Main {  
    public static void main(String[] args) {  
        Paytm paytm = new Paytm();  
        PhonePe phonePe = new PhonePe();  
  
        paytm.processPayment(5); // 15  
        phonePe.processPayment(5); // 25  
        phonePe.payViaUpi(5);  
    }  
}
```
---

#### **2. Abstract Classes**

- **Definition**:  
    Abstract classes provide a base structure for other classes, allowing both concrete methods (with implementation) and abstract methods (without implementation).
    
- **Key Points**:
    
    - Cannot be instantiated.
    - Subclasses must implement abstract methods.
    - Used when multiple related classes share some common functionality.
- **Syntax (Java)**:
    
    ```java
    abstract class Database {
        abstract void connect();
        void disconnect() {
            System.out.println("Disconnecting from the database...");
        }
    }
    
    class MySQLDatabase extends Database {
        void connect() {
            System.out.println("Connecting to MySQL Database...");
        }
    }
    ```
    
- **Software Development Example**:  
    In a **data-driven application**, you might create an abstract class `Database` that defines common methods like `connect()` and `disconnect()`. Subclasses like `MySQLDatabase` and `PostgreSQLDatabase` provide specific implementations for connection logic.
- **Real-Life Example**:
	- **Abstract Class**: A _Vehicle_ is an abstract concept—it has wheels, an engine, etc., but can't be directly used.
	- **Subclasses**: Car, Truck, Bike, etc., define specific behavior (e.g., engine starting).

---

#### **3. Template Classes (Generics)**

- **Definition**:  
    Template classes allow the creation of reusable, type-safe classes or methods that can work with different data types.
    
- **Key Points**:
    
    - Common in Java, C++, and other languages.
    - Helps avoid duplication of code for similar logic applied to different data types.
- **Syntax (Java)**:
    
    ```java
    class Response<T> {
        private T data;
        public void setData(T data) {
            this.data = data;
        }
        public T getData() {
            return data;
        }
    }
    
    public class Main {
        public static void main(String[] args) {
            Response<String> successResponse = new Response<>();
            successResponse.setData("Success!");
            System.out.println(successResponse.getData());
        }
    }
    ```
    
- **Software Development Example**:  
    In **REST API development**, you might use a generic `Response<T>` class to return responses with different data types (e.g., `Response<User>`, `Response<Product>`). This avoids writing separate response classes for every endpoint.
- **Real-Life Example**:
	- **Template**: A box that can hold anything (toys, clothes, books).
	- **Usage**: You define what you store in it at runtime.
```java
abstract class DataBase {  
    // Sql, rds, postgresql, mongodb, dynamodb  
    abstract void connectDB();  
  
    public void disconnectDB(){  
        System.out.println("DB Disconnected!");  
    }  
}
```
---

#### **4. Singleton Class**

- **Definition**:  
    A Singleton ensures that only one instance of the class is created throughout the application and provides a global access point to it.
    
- **Key Points**:
    
    - Often used for shared resources like configuration, logging, or database connections.
    - Typically implemented with private constructors and a static instance.
- **Syntax (Java)**:
    
    ```java
    class Logger {
        private static Logger instance;
        private Logger() {}
        public static Logger getInstance() {
            if (instance == null) {
                instance = new Logger();
            }
            return instance;
        }
        public void log(String message) {
            System.out.println("LOG: " + message);
        }
    }
    ```
    
- **Software Development Example**:  
    In a **logging system**, a Singleton `Logger` ensures that all parts of the application write logs to the same destination, avoiding the creation of multiple log writers.
- **Real-Life Example**:
	- **Singleton**: A government in a country (only one exists).
	- **Usage**: You call it to manage centralized tasks.
Singletonclass.java
```java
public class SingletonClass {  
    public static SingletonClass instance;  
    private String data;  
  
    private SingletonClass(String data){  
        this.data = data;  
    };  
    public static void setData(String s){  
        if(instance == null){   // if its not initialized  
            instance = new SingletonClass(s);  
        }else{  // when instance is already initialised  
            instance.data = s;  
        }  
    }  
  
    public static String getData(){  
        if(instance == null) return "";  
        return instance.data;  
    }  
}
```
---

#### **5. Upcasting and Downcasting**

- **Upcasting**:  
    Converting a subclass object to its superclass type.
    - **Why**: To enable polymorphism and generalize objects.
- **Syntax**:
    
    ```java
    Animal animal = new Dog(); // Upcasting
    animal.eat(); // Calls Dog's implementation
    ```
    
- **Software Development Example**:  
    In a **zoo management system**, you might treat all animals as `Animal` for general operations like feeding. Specific behaviors like barking or flying are not accessible during upcasting.
- **Real-Life Example**:
	- **Upcasting**: A _Cat_ or _Dog_ treated as an _Animal_ in a pet shop system.
	- **Downcasting**: When specifics like `Dog.bark()` or `Cat.purr()` are needed.

---

- **Downcasting**:  
    Converting a superclass object back to its subclass type.
    
    - **Why**: To access subclass-specific methods.
- **Syntax**:
    
    ```java
    Dog dog = (Dog) animal; // Downcasting
    dog.bark();
    ```
    
- **Software Development Example**:  
    In a **game development project**, you might have a base class `Character` and subclasses like `Warrior` or `Mage`. During combat, you downcast the `Character` to a specific subclass to use abilities like `warrior.shieldBlock()` or `mage.castSpell()`.
    
Main.java
```java
import java.util.ArrayList;  
  
//TIP To <b>Run</b> code, press <shortcut actionId="Run"/> or  
// click the <icon src="AllIcons.Actions.Execute"/> icon in the gutter.  
public class Main {  
    public static void main(String[] args) {  
        // Normal  
        // Left side is equal to right side, Dog = Dog        Dog tommy = new Dog("Tommy","Husky");  
  
        // Upcasting  
        // Parent on left, child on right        // parent will not be able to access child members/methods        // because parent does not know about child        Animal animal = new Dog("Tommy","Husky");  
  
  
        // Downcasting  
//        Animal jacky = new Animal("Jacky");  
//        Dog dog2 = (Dog) jacky;  
//        System.out.println(dog2.breed);  
  
        ArrayList<Object> arr = new ArrayList<>();  
        arr.add(10);  
        arr.add("asd");  
        System.out.println(arr);  
    }  
}
```
Dog.java
```java
public class Dog extends Animal {  
    public String breed;  
  
    public Dog(String name, String breed) {  
        super(name);  
        this.breed = breed;  
    }  
  
    public void bark() {  
        System.out.println("Woof woof!");  
    }  
}
```
Animal.java
```java
public class Animal {  
    public String name;  
  
    public Animal(String name) {  
        this.name = name;  
    }  
  
    public void eat() {  
        System.out.println("Yummy!");  
    }  
}
```
---

#### **Comparison Table**

|**Concept**|**Purpose**|**Software Development Example**|
|---|---|---|
|**Interface**|Define behavior contracts.|Payment gateways for e-commerce integration.|
|**Abstract Class**|Share common behavior partially.|Database base class for connection/disconnection.|
|**Template Class**|Reusability with type safety.|Generic response classes for API responses.|
|**Singleton**|One instance for global use.|Logger for application-wide logging.|
|**Upcasting**|Generalization for polymorphism.|Treating all animals as `Animal` in a zoo app.|
|**Downcasting**|Access specific subclass features.|Using specific abilities in game characters.|
## MyArrayList Activity
```java
//TIP To <b>Run</b> code, press <shortcut actionId="Run"/> or  
// click the <icon src="AllIcons.Actions.Execute"/> icon in the gutter.  
public class Main {  
    public static void main(String[] args) {  
        MyArrayList<Integer> arr = new MyArrayList<>();  
        arr.add(10);  
        arr.add(20);  
        arr.add(30);  
        arr.add(40);  
        arr.add(50);  
        arr.add(60);  
        arr.add(70);  
        arr.add(80);  
        arr.add(90);  
        arr.add(100);  
        arr.add(110);  
        System.out.println(arr.remove());  
        System.out.println(arr.get(9));  
        arr.set(0,2000);  
    }  
}
```
MyArraylist.java
```java
public class MyArrayList<T> {  
    private int size;  
    private int capacity;  
    private T[] arr;  
  
    public MyArrayList(){  
        this.capacity = 10;  
        this.size = 0;  
        this.arr = (T[]) new Object[this.capacity];  
    }  
  
    private void resize() {  
        T[] newArr = (T[]) new Object[this.capacity * 2];  
        for(int i = 0;i<this.arr.length;i++){  
            newArr[i] = this.arr[i];  
        }  
        this.arr = newArr;  
        this.capacity = this.capacity*2;  
    }  
  
    public boolean isEmpty() {  
        return size == 0;  
    }  
  
    public T get(int idx) {  
        if (idx < 0 || idx >= size) {  
            System.out.println("Index out of bounds!");  
            return null;  
        }  
        return this.arr[idx];  
    }  
  
    public void set(int idx, T val) {  
        if (idx < 0 || idx >= size) {  
            System.out.println("Index out of bounds!");  
            return;  
        }  
        this.arr[idx] = val;  
    }  
  
    public void add(T val) {  
        if(this.size == this.capacity){  
            this.resize();  
        }  
        this.arr[this.size] = val;  
        this.size++;  
    }  
  
    public T remove() {  
        if(this.isEmpty()) return null;  
        this.size--;  
        return this.arr[this.size];  
    }  
  
}
```
---
