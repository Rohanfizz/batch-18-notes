## 4 Pillars of OOPs
1. Inheritence
2. Polymorphism
3. Abstraction
4. Encapsulation
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
- A nested static member (manufacturer) will be independent of the initialization of all the nester classes.
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
### Code till static

```java
//Main.java
import pkg2.Human;  
import java.util.*;  
  
public class Main {  
  
    public static class Car{  
        String color;  
        int mileage;  
        String manufacturer;  
  
        public Car(String color, int mileage,String manufacturer){  
            this.color = color;  
            this.mileage = mileage;  
            this.manufacturer = manufacturer;  
        }  
        public void printColor(){  
            String color = "blue";  
            System.out.println(this.color);  
        }  
        public void compareMilage(Car otherCar){  
            if(otherCar.mileage > this.mileage){  
                System.out.println("Other Car is better");  
            }else{  
                System.out.print("My car is better");  
            }  
        }  
    }  
  
    public static class Animal{  
        static int population;  
        String name;    // non static  
        public static void whatIsYourMood(){  
//            System.out.println(this.name); // this keyword is not allowed in static context  
            System.out.println("Happy");  
            Animal dog = new Animal();  
            dog.name = "tommy";  
  
  
        }  
    }  
  
    public static void main(String[] args) {  
        Car myFirstCar = new Car("Red",17,"Suzuki");  
        Car vinodsCar = new Car("Black",25,"Toyota");  
        myFirstCar.compareMilage(vinodsCar);  
        System.out.println(Human.population);  
        Human h1 = new Human("Jasprit","Female",24);  
        Human h2 = new Human("Ajit","Male",25);  
        Human h3 = new Human("Vinod","Male",25);  
        System.out.println(Human.population);  
  
        Animal.whatIsYourMood();  
    }  
}
```

Human.java inside pkg2
```java
package pkg2;  
  
public class Human {  
    // static member/methods are not dependent on the initialization of the object of the class.  
    public static int population = 0;  
    public String name;  
    public String gender;  
    public int age;  
  
    public static void printPopulation(){  
        // I will only be able to use static member  
        System.out.println(population);  
    }  
    public Human(String name,String gender,int age){  
        this.name = name;  
        this.gender = gender;  
        this.age = age;  
    }  
  
}
```

___
#### **1. Inheritance**  
-- A child can extend a parent
`public class Vehicle {..}` - parent
`public class Car extends Vehicle{..}` - child

- The car class **extends** vehicle class. this means car class adds to whatever vehicle class is already having.
- Child class acquire properties and methods of parent class.
- Super keyword is used to access the parent class's members/methods from the child class.
- Every class implicitly extends Object class which provides it with some essential functionalities such as `toString(), hashCode()`
- Here's a detailed explanation of different types of inheritance in Java:
# Types of inheritence
### 1. **Single Level Inheritance**

- **Definition**: A single class inherits from one parent class.
- **Example**:
    
    ```java
    class Parent {
        void display() {
            System.out.println("This is the Parent class.");
        }
    }
    
    class Child extends Parent {
        void show() {
            System.out.println("This is the Child class.");
        }
    }
    
    public class Main {
        public static void main(String[] args) {
            Child child = new Child();
            child.display();
            child.show();
        }
    }
    ```
    
- **Output**:
    
    ```
    This is the Parent class.
    This is the Child class.
    ```
    

---

### 2. **Multiple Inheritance** (Not supported in Java with classes)

- **Definition**: A child class inherits from **two or more parent classes**. This is **not directly supported** in Java to avoid the "diamond problem."
- **Workaround**: Java allows multiple inheritance through **interfaces**.
- Example we will see in the interfaces class

---

### 3. **Multi-Level Inheritance**

- **Definition**: A class inherits from another class, which itself is inherited from another class (a chain of inheritance).
- **Example**:
    
    ```java
    class Grandparent {
        void methodGP() {
            System.out.println("This is the Grandparent class.");
        }
    }
    
    class Parent extends Grandparent {
        void methodP() {
            System.out.println("This is the Parent class.");
        }
    }
    
    class Child extends Parent {
        void methodC() {
            System.out.println("This is the Child class.");
        }
    }
    
    public class Main {
        public static void main(String[] args) {
            Child child = new Child();
            child.methodGP();
            child.methodP();
            child.methodC();
        }
    }
    ```
    
- **Output**:
    
    ```
    This is the Grandparent class.
    This is the Parent class.
    This is the Child class.
    ```
    

---

### 4. **Hierarchical Inheritance**

- **Definition**: Multiple child classes inherit from the same parent class.
- **Example**:
    
    ```java
    class Parent {
        void parentMethod() {
            System.out.println("This is the Parent class.");
        }
    }
    
    class Child1 extends Parent {
        void child1Method() {
            System.out.println("This is Child1 class.");
        }
    }
    
    class Child2 extends Parent {
        void child2Method() {
            System.out.println("This is Child2 class.");
        }
    }
    
    public class Main {
        public static void main(String[] args) {
            Child1 child1 = new Child1();
            Child2 child2 = new Child2();
    
            child1.parentMethod();
            child1.child1Method();
    
            child2.parentMethod();
            child2.child2Method();
        }
    }
    ```
    
- **Output**:
    
    ```
    This is the Parent class.
    This is Child1 class.
    This is the Parent class.
    This is Child2 class.
    ```
    

---

### 5. **Hybrid Inheritance**

- **Definition**: A mix of two or more types of inheritance (e.g., hierarchical + multiple). **Java does not support hybrid inheritance** directly with classes because of the "diamond problem," but it can be implemented using **interfaces**.
- Example we will see in the interfaces class
---

### Key Points:

1. **Single, Multi-Level, and Hierarchical inheritance** are directly supported in Java.
2. **Multiple and Hybrid inheritance** with classes is not supported due to ambiguity issues but can be implemented using **interfaces**.
	7. ![[Pasted image 20241121195530.png]]

Code till inheritance
Vehicle.java
```java
package pkg;  
  
public class Vehicle{  
    public String fuelType;  
    private String manufacturer;  
    private int number;  
    private int model;  
  
    public Vehicle(String fuelType, String manufacturer, int number, int model) {  
        this.fuelType = fuelType;  
        this.manufacturer = manufacturer;  
        this.number = number;  
        this.model = model;  
    }  
  
    public String getFuelType() {  
        return this.fuelType;  
    }  
  
    public void setFuelType(String fuelType) {  
        this.fuelType = fuelType;  
    }  
  
    public String getManufacturer() {  
        return manufacturer;  
    }  
  
    public void setManufacturer(String manufacturer) {  
        this.manufacturer = manufacturer;  
    }  
  
    public int getNumber() {  
        return number;  
    }  
  
    public void setNumber(int number) {  
        this.number = number;  
    }  
  
    public int getModel() {  
        return model;  
    }  
  
    public void setModel(int model) {  
        this.model = model;  
    }  
}
```
Car.java
```java
package pkg;  
  
public class Car extends Vehicle {  
    private int seatCapacity;  
    private int bootCapacity;  
    private int torque;  
    private int hp;  
  
    public Car(String fuelType, String manufacturer, int number, int model, int seatCapacity, int bootCapacity, int torque, int hp){  
        super(fuelType,manufacturer,number,model);  
        this.seatCapacity = seatCapacity;  
        this.bootCapacity = bootCapacity;  
        this.torque = torque;  
        this.hp = hp;  
    }  
  
    public int getSeatCapacity() {  
        return seatCapacity;  
    }  
  
    public void setSeatCapacity(int seatCapacity) {  
        this.seatCapacity = seatCapacity;  
    }  
  
    public int getBootCapacity() {  
        return bootCapacity;  
    }  
  
    public void setBootCapacity(int bootCapacity) {  
        this.bootCapacity = bootCapacity;  
    }  
  
    public int getTorque() {  
        return torque;  
    }  
  
    public void setTorque(int torque) {  
        this.torque = torque;  
    }  
  
    public int getHp() {  
        return hp;  
    }  
  
    public void setHp(int hp) {  
        this.hp = hp;  
    }  
}
```

Bike.java
```java
package pkg;  
  
public class Bike extends Vehicle{  
    private int cc;  
    private boolean areDiskBrakesPresent;  
  
    public Bike(String fuelType,String manufacturer,int number,int model, int cc, boolean areDiskBrakesPresent){  
        super(fuelType,manufacturer,number,model);  
        this.cc = cc;  
        this.areDiskBrakesPresent = areDiskBrakesPresent;  
    }  
  
    public int getCc() {  
        return cc;  
    }  
  
    public void setCc(int cc) {  
        this.cc = cc;  
    }  
  
    public boolean isAreDiskBrakesPresent() {  
        return areDiskBrakesPresent;  
    }  
  
    public void setAreDiskBrakesPresent(boolean areDiskBrakesPresent) {  
        this.areDiskBrakesPresent = areDiskBrakesPresent;  
    }  
}
```
Main.java
```java
import pkg.Bike;  
  
public class Main {  
    public static void main(String[] args) {  
        Bike myBike = new Bike("Petrol", "Honda", 1231, 1234, 160, true);  
        System.out.println(myBike.getCc());  
        System.out.println(myBike.getFuelType());  
        System.out.println(myBike.toString());  
    }  
}
```
___
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
- // TODO If a class is final what will happen? `public final class User`

Codes of final keyword
User.java
```java
public final class User {  
    public String name;  
    public int bankAccountNumber;  
    public int balance;  
    public User(String name, int bankAccountNumber, int balance) {  
        this.name = name;  
        this.bankAccountNumber = bankAccountNumber;  
        this.balance = balance;  
    }  
    public String getName(){  
        return this.name;  
    }  
  
    public int getBankAccountNumber(){  
        return this.bankAccountNumber;  
    }  
    public int getBalance(){  
        return this.balance;  
    }  
}
```

Main.java
```java
public class Main{  
    public static void main(String[] args) {  
        final User user1 = new User("Rohan",123123,100000);  
        User user2 = new User("Bhushan",123124,100000);  
        user2 = user1;  
        user2 = new User("Bhushan",123124,100000);  
        user1.balance = 10;  
    }  
}
```
#### **2. Polymorphism**  
=> Poly - many
=> morph - change shape
// TODO Simple definition to be added.
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
	- Enhance compiler performance for early binding, compiler during the compile time will decide that a final method will look same for every child.
```java
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

Polymorph codes
Main.java
```java
import java.util.ArrayList;  
  
public class Main {  
    public static void main(String[] args) {  
//        Car myCar = new Car(100000,20,5,123,"Tata","Petrol"); // No args constructor  
//        myCar.printCarDetails();  
        Lion.whereAreTheAnimals();  
        Lion simba = new Lion("Simba");  
        simba.sayHi();  
  
        Dog tommy = new Dog("Tommy");  
        tommy.sayHi();  
        ArrayList<Integer> arr = new ArrayList<>();  
        arr.add(10);  
        System.out.println(arr);  
    }  
}
```
Animal.java
```java
public class Animal {  
    String name;  
  
    public Animal(String name) {  
        this.name = name;  
    }  
  
    public void sayHi() {  
        System.out.println("Hello! I'm an animal my name is " + this.name + "!");  
    }  
    public static void whereAreTheAnimals(){  
        System.out.println("Zoo!");  
    }  
}
```

Dog.java
```java
public class Dog extends Animal {  
    public Dog(String name){  
        super(name);  
    }  
}
```
Lion.java
```java
public class Lion extends Animal {  
    public Lion(String name){  
        super(name);  
    }  
  
    @Override  
    public void sayHi(){  
        System.out.println("Roaar!!");  
    }  
  
}
```

Car.java
```java
public class Car {  
    int price;  
    int mileage;  
    int seatingCap;  
    int modelNumber;  
    String manufacturer;  
    String fuelType;  
  
    public Car(int price, int mileage, int seatingCap, int modelNumber, String manufacturer, String fuelType) {  
        this.price = price;  
        this.mileage = mileage;  
        this.fuelType = fuelType;  
        this.seatingCap = seatingCap;  
        this.modelNumber = modelNumber;  
        this.manufacturer = manufacturer;  
    }  
    public Car(){  
  
    }  
    public Car(int mileage){  
        this.mileage = mileage;  
    }  
  
    public void printCarDetails(){  
        System.out.println(this.price);  
        System.out.println(this.mileage);  
        System.out.println(this.seatingCap);  
        System.out.println(this.modelNumber);  
        System.out.println(this.manufacturer);  
        System.out.println(this.fuelType);  
    }  
  
    public void printCarDetails(String destination){    // same function name, same return type  
        // But different number of parameters, hence polymorphism  
    }  
  
}
```
#### **5. Other OOP Concepts**  
- **Abstraction**: - Hiding unnecessary details and showing the valuable  information.
- We don't care about HOW, we just care about WHAT

## Class Codes
- Used to explain this keyword
```java
//TIP To <b>Run</b> code, press <shortcut actionId="Run"/> or  
// click the <icon src="AllIcons.Actions.Execute"/> icon in the gutter.  
public class Main {  
    public static class Car{  
        String color;  
        int mileage;  
        String manufacturer;  
  
        public Car(String color, int mileage,String manufacturer){  
            this.color = color;  
            this.mileage = mileage;  
            this.manufacturer = manufacturer;  
        }  
        public void printColor(){  
            String color = "blue";  
            System.out.println(this.color);  
        }  
        public void compareMilage(Car otherCar){  
            if(otherCar.mileage > this.mileage){  
                System.out.println("Other Car is better");  
            }else{  
                System.out.print("My car is better");  
            }  
        }  
    }  
    public static void main(String[] args) {  
        Car myFirstCar = new Car("Red",17,"Suzuki");  
        Car vinodsCar = new Car("Black",25,"Toyota");  
        myFirstCar.compareMilage(vinodsCar);  
    }  
}
```
