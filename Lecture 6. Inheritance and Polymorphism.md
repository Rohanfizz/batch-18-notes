## "this" Keyword
- "this" is a **reference variable** that refers to the current object.
- Can only be used in non-static context.
## "static" keyword
- **non-static members/methods  cannot be accessed in the static context**
	- because static methods do not need any instance of an object, whereas non-static member/methods, need  instance  of an object
- static member/methods can be accessed in an non static context.
- Static members are called by Class name itself
	- `Human.population` where `Human` is tha className not the instance variable name.
- [[this keyword]] keyword doesn't work
- Initialization?  Static block
	- Inner static class?
- #### Why is `public static void main` static?
	- Main method has to be declared static because keyword static allows main to be called without creating an object of the class in which the main method is defined.
- How to access non static methods inside static methods
```java
public static void printSubjects(){  
    Student rohan = new Student("Rohan",20,30);  
    rohan.setName("Vikas");  //setName -> non static
    for(String s: subjects){  
        System.out.print(s+", ");  
    }  
}
```
- [[Inner classes]]- Static depends on the Scope of where its  written.
- A nested static member will be static/independent of the initialization of all the nester classes.
```java
public class Main {  
    public class Car{  
        static String manufacturer="ABC";  
        int price;  
  
        public Car(String manufacturer, int price) {  
            this.manufacturer = manufacturer;  
            this.price = price;  
        }  
    }  
  
    public static void main(String[] args) {  
        System.out.println(Main.Car.manufacturer);  
    }  
}
```
`manufacturer` is static, not only for Car but also for main.
#### **1. Inheritance**  
-- A child can extend a parent
`public class Vehicle {..}` - parent
`public class Car extends Vehicle{..}` - child

- The car class **extends** vehicle class. this means car class adds to whatever vehicle class is already having.
- Child class acquire properties of parent class.
- Super keyword is used to access the parent class's members/methods from the child class.
- Every class implicitly extends Object class which provides it with some essential functionalities such as `toString(), hashCode()`
- Types Of Inheritance
	1. Singe Level Inheritance
	2.  Multiple Inheritance - One class extending 2 class ⚠ Not supported in java. We use interfaces instead
	3. Multi Level Inheritance: Object <- Vehicle <- Car <- SUV
	4. Hierarchical Inheritance
	6. Hybrid Inheritance - Mix of multiple and hierarchical.
	7. ![[Pasted image 20241121195530.png]]
## The "super" keyword
Super is used to access parent class methods and attributes from the child class's scope.

⚠ Note the super constructor should be called before any initialization of the child class members.
```java
public Car(int price,int milage,String fuelType,String manufacturer,int tax){  
    super(4,5,price,milage);  
    this.fuelType = fuelType;  
    this.manufacturer = manufacturer;  
    this.tax = tax;  
}
```
## The "final" keyword
- If you make any variable as final, you cannot change the value of final variable(It will be constant). 
- The final keyword can be applied with the variables, a final variable that have no value it is called **blank final variable** or uninitialized final variable. It can be initialized in the constructor only. 
- **If its primitive, you cannot change the value**
- **If its non primitive, you can change the value of any of its members.**
```java
final Student vrinda = new Student("Vrinda",1,2);  
Student rohan = new Student("Rohan",10,30);  
vrinda = rohan; //this is not allowed
```
- Non final objects can point to final objects
#### **2. Polymorphism**  
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

#### **3. Method Overloading**  
- Compile Time/ Static poly.
- Same method name with different parameters in the same class.  
- 2 methods act differently, when the data types of parameters are different
- Operator overloading - **Java Doesn't support**
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


#### **4. Method Overriding**  
- Runtime Poly/Dynamic poly
- Subclass provides a specific implementation of a method already defined in its superclass.  
- [[@Override Annotation]]
- The child class during runtime decides to ignore the implementation of same method from the parent class, giving priority of its own method
- [[Upcasting or Dynamic method dispatch and Downcasting]]
- You cannot override **final** methods
	- I don't want any tampering
	- Enhance compiler performance  for early binding, compiler during the compile time will decide that a final method will look same for every child.
```
public final void sayHello(){  
    System.out.println("Hello from the parent class");  
}
```
- Static methods can be inherited but cannot be overridden 
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

#### **5. Other OOP Concepts**  
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
