#### **1. Inheritance**  
- Allows a class to inherit properties and methods of another class using the `extends` keyword.  
  ```java
  class Animal {
      void eat() {
          System.out.println("This animal eats food.");
      }
  }

  class Dog extends Animal {
      void bark() {
          System.out.println("Dog barks.");
      }
  }

  public class Main {
      public static void main(String[] args) {
          Dog dog = new Dog();
          dog.eat(); // Inherited method
          dog.bark(); // Own method
      }
  }
  ```

#### **2. Method Overriding**  
- Subclass provides a specific implementation of a method already defined in its superclass.  
  ```java
  class Animal {
      void sound() {
          System.out.println("Animal makes a sound");
      }
  }

  class Dog extends Animal {
      @Override
      void sound() {
          System.out.println("Dog barks");
      }
  }
  ```

#### **3. Method Overloading**  
- Same method name with different parameters in the same class.  
  ```java
  class Calculator {
      int add(int a, int b) {
          return a + b;
      }

      double add(double a, double b) {
          return a + b;
      }
  }
  ```

#### **4. Polymorphism**  
- **Compile-time Polymorphism**: Achieved via method overloading.  
- **Run-time Polymorphism**: Achieved via method overriding (dynamic method dispatch).  
  ```java
  class Animal {
      void sound() {
          System.out.println("Animal makes a sound");
      }
  }

  class Dog extends Animal {
      void sound() {
          System.out.println("Dog barks");
      }
  }

  public class Main {
      public static void main(String[] args) {
          Animal a = new Dog(); // Upcasting
          a.sound(); // Calls Dog's sound() method
      }
  }
  ```

#### **5. Other OOP Concepts**  
- **Encapsulation**: Binding data (variables) and methods into a single unit (class).  
- **Abstraction**: Hiding implementation details and showing only functionality.  
  ```java
  abstract class Shape {
      abstract void draw();
  }

  class Circle extends Shape {
      void draw() {
          System.out.println("Drawing Circle");
      }
  }
  ``` 

By covering these topics in two sessions, students will have a strong foundation in object-oriented programming in Java.