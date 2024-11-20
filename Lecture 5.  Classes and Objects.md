
#### **1. Understanding Classes and Objects**  
- **Class**: Blueprint for creating objects. Defines properties (attributes) and behaviors (methods).  
  ```java
  class Car {
      String color;
      int speed;

      void displayDetails() {
          System.out.println("Color: " + color + ", Speed: " + speed);
      }
  }
  ```
- **Object**: Instance of a class.  
  ```java
  public class Main {
      public static void main(String[] args) {
          Car car1 = new Car();
          car1.color = "Red";
          car1.speed = 100;
          car1.displayDetails();
      }
  }
  ```

#### **2. Constructors**  
- Special method used to initialize objects. Same name as the class.  
  ```java
  class Car {
      String color;
      int speed;

      // Constructor
      Car(String color, int speed) {
          this.color = color;
          this.speed = speed;
      }
  }

  public class Main {
      public static void main(String[] args) {
          Car car1 = new Car("Red", 100);
      }
  }
  ```

#### **3. Member Variables and Methods**  
- **Member Variables**: Define the properties of a class.  
- **Methods**: Define the actions/behavior of a class.  
  ```java
  class Calculator {
      int add(int a, int b) {
          return a + b;
      }
  }
  ```

#### **4. Access Modifiers**  
- Control access to classes, variables, methods.  
  | Modifier   | Class | Package | Subclass | World |
  |------------|-------|---------|----------|-------|
  | **public** | ✔️    | ✔️      | ✔️       | ✔️    |
  | **protected** | ✔️    | ✔️      | ✔️       | ❌    |
  | **private** | ✔️    | ❌      | ❌       | ❌    |

  ```java
  class Person {
      private String name;

      public void setName(String name) {
          this.name = name;
      }

      public String getName() {
          return name;
      }
  }
  ```

---
