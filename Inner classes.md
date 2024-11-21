```java
public class Main {  
    public static class Car{  
        String manufacturer;  
        int price;  
  
        public Car(String manufacturer, int price) {  
            this.manufacturer = manufacturer;  
            this.price = price;  
        }  
    }  
  
    public static void main(String[] args) {  
        Car rohansCar = new Car("Alfa Romero",1000000);  
        Car mrBeansCar = new Car("Mini Cooper",10000);  
        System.out.println(rohansCar.manufacturer);  
        System.out.println(mrBeansCar.manufacturer);  
    }  
}
```
