```
Parent theParent = new Child();  
theParent.sayHello();
```

the **access** of methods and attributes depends on left  side
whereas the **version** of those methods depends on the right Side

```
Parent theParent = new  Child();  //Upcasting
theParent.sayHello();  
  
Child theChild = (Child)(theParent);  //Downcasting
theChild.toy();
```

Child getting converted to parent is = Upcasting
Parent getting converted to child is = Downcasting