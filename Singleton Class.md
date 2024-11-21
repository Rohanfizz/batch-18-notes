- A class for which I want only 1 instance to exist.
- A singleton class has-
	1. Methods, attributes  
	2. [[Access Modifiers|Private]] constructor 
	3. Static Instance - this will be the only instance  
	4. Custom constructor which restricts any object creation if static instance is already initialized 

```java
public class Owner {  
    //Methods, attributes  
    public String name;  
    //Private constructor  
    private Owner(String name){  
        this.name = name;  
    }  
    //Static Instance - this will be the only instance  
    static Owner me;  
    //Custom constructor which restricts any object creation if static instance is already initialized  
    static public Owner setOwner(String name){  
        if(Owner.me == null) {  
            Owner.me = new Owner(name);  
        }  
        return Owner.me;  
    }  
}
```