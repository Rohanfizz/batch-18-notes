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