
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
- Special method used to initialize objects. Always Same name as the class.  
- Why do we not write return type in constructors? Constructors by default return the "Class" type.
- What is the use of `new` keyword? It tells java that a constructor is getting called, and a new object of the class should be returned.
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
- Public
	- Data members are accessible from anywhere
		- Any package
		- Any class
		- Universal
- Private
	- Data members are only accessible inside the class
- Default
	- Data members are accessible only in the same package
- Protected
	- They work just fine in the same package
	- But when the package is different the data member is accessible INSIDE the child class which is present in a different package.
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

## Excercise
Create a class named `Book` with the following attributes:
- A **title** to store the name of the book.
- An **author** to store the author's name.
- A boolean to track whether the book is **borrowed** or not.
all properties should be private.
you should implement all getter and setter methods.
Try defining the class in a different package.

### Class Codes
```java
Main.java
import pkg2.Dog;  
  
public class Main {  
    public static class Human { // set of rules  
        // Properties/ Member of human class        String gender;  
        int weight;  
        int height;  
        String name;  
        int age;  
  
        // No need to provide return types in constructors  
        public Human(String g, int w, int h, String n, int a) { // constructor  
            gender = g;  
            weight = w;  
            height = h;  
            name = n;  
            age = a;  
        }  
  
        public void sayHi(){                // Method / functions  
            System.out.println("Hello, my name is "+name+", my age is "+age+" years!");  
        }  
    }  
  
    public static void main(String[] args) {  
//        Human rohan = new Human("Male", 70, 175, "Rohan", 23);  
//        Human riya = new Human("Female", 60, 160, "Riya", 22);  
//  
//        rohan.sayHi();  
//        riya.sayHi();  
  
        Car brezza = new Car( 20);  
        brezza.mileage = 25;  
        brezza.addFuel(10);  
        brezza.checkRange();  
        brezza.setFuel(-5);  
  
        Dog rocky = new Dog("Rocky",5);  
  
        rocky.whatIsYourAge();  
  
    }  
}  
  
// private, public, protected, default = Access Modifiers
```

Car.java
```java 
public class Car {  
    // car class is inside the same package from where we are running the code.  
    // hence we will be able to access all the public and protected properties of this class.    // Private properties are only limited to inner class usage    private int mileage;  
    private int fuel;  
  
    public int getFuel(){  
        return this.fuel;  
    }  
    public void setFuel(int newValue){  
        if(newValue < 0) return;  
        this.fuel = newValue;  
    }  
  
    public Car(int m) {  
        this.mileage = m;  
    }  
  
    public void addFuel(int fuel) {  // This function will add fuel to the car  
        this.fuel += fuel;  
    }  
  
    public void checkRange() {  // This function checks how much KMs are remaining  
        System.out.println(this.mileage * this.fuel + " kms left");  
    }  
}
```

Dog.java (it is in pkg2 package)

```java
package pkg2;  
  
public class Dog{  
    String name;  
    int age;  
    public Dog(String n,int a){  
        this.name = n;  
        this.age = a;  
    }  
  
    public void sayHi(){  
        System.out.println("Woof Woof!");  
    }  
    protected void whatIsYourAge(){  
        System.out.println("Its age is "+age);  
    }  
    private void whatIsYourName(){  
        System.out.println("Its name is "+name);  
    }  
  
}
```