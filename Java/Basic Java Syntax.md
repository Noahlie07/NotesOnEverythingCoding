# Basic Java Syntax  

## Defining a Class and Creating an Instance of a Class 
Basic syntax of defining a class (remove public if class is not public)
```
public class MainClass {
  # instance/static variables and methods
}
```

Creating an instance of a class called obj   
```
MainClass obj = new MainClass()
```
  


## Instance Vs Static and How to Create a Method  
**Instance variables and methods** are things defined in a class that only exist once an instance of a class is created. They belong to each individual object created from the class.   
We define an instance variable as we would a normal variable. 
```
int Variable = 10;
```
We define an instance method like below
```
public int myMethod(int arg1, int arg2){
  ......
}
```
public is modifier, int is return type of the method  
Due to the nature of instance variable and method, we can't call them within a static function. 

**Static variables and methods** are things defined in a class that belong to the class itself.  It can therefore be called using the class name.  
We define them the same way we would an instance, but we add the static keyword.    
```
static int Variable = 10;
```
```
static int myMethod(int arg1, int arg2){
  ......
}
```

BTW, to access an instance variable using an instance method in a class, we use the `this.` prefix. 
```
private int instanceVariable;

public void assignValue(int instanceVariable){
  this.instanceVariable = instanceVariable;
}

public voide increment(){
  instanceVariable++;
}
```
Actually, it is **not absolutely necessary** to use this. prefix as seen in the second method. It is only necessary if the argument of a method that uses the instance variable has the same as the instance variable, as seen in the first method.
