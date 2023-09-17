# Final
The keyword final in Java has multiple uses and is fundamentally about restricting change or modification. Here's a detailed tutorial on the usage of final in Java:

### final Variables:
   A final variable cannot be reassigned once it has been initialized. This effectively makes it a constant.
   final variables need to be initialized either at the time of declaration or within the constructor (for instance variables).
```java
final int MY_CONSTANT = 10;  // You cannot reassign a new value to MY_CONSTANT
```
### final Methods:
A final method in a class cannot be overridden by subclasses.   
This is useful when you want to ensure that the behavior of a method remains consistent across subclasses.
```java
class Parent {
   final void show() {
      System.out.println("This is a final method.");
   }
}

class Child extends Parent {
// This will throw a compile-time error
// void show() { ... }  // Cannot override the final method from Parent
}
```
### final Classes:
A final class cannot be subclassed (i.e., extended). This can be especially useful for security reasons or to ensure the immutability of the class.
```java
final class MyFinalClass {
   // ... class contents ...
}

// This will throw a compile-time error
class AnotherClass extends MyFinalClass { ... }  // Cannot inherit from final MyFinalClass 
```
### final Parameters:
   Parameters of a method can also be declared final. This means that the value of the parameter cannot be changed within the method.
```java
void myMethod(final int num) {
   // num = 20;  // This would be a compile-time error because num is final
}
```
  
### Benefits of Using final:
- `Immutable Objects:` By combining final with other techniques, you can create immutable objects in Java, which can be beneficial for creating thread-safe applications.
- `Performance`: In some cases, using final can provide minor performance improvements as the JVM can optimize final variables or methods.
- `Intention`: When you use final, it sends a clear signal to other developers that something (a variable, method, or class) is not meant to be changed or extended.
  
### Summary:
The final keyword in Java is all about restriction:

- final variables cannot be reassigned.
- final methods cannot be overridden.
- final classes cannot be subclassed.

Using final can help in creating robust and secure applications, as it restricts unwanted modifications and clarifies your intentions in the code.

## Exercises

### Final Circle
Problem Statement:

Create a class named `Circle` with the following specifications:

It should have a final double variable named PI with a value of 3.14159.
It should have a constructor that accepts a single double parameter representing the radius of the circle. The radius itself should be a final variable.
Implement a method area() that calculates the area of the circle using the formula PI * radius * radius.
Tasks:

Create the `Circle` class as described.
Instantiate a Circle object in a main method and print its area.

### Final Method
Problem Statement:

You have a base class called Vehicle and a derived class called Car.

In the `Vehicle` class, implement a final method named startEngine() that prints "Engine started".
In the `Car` class, try overriding the startEngine() method to print "Car engine started".
Observe the compile-time error and understand the significance of a final method.
Tasks:

Create the `Vehicle` and `Car` classes as described.
Instantiate a Car object in a main method and call the startEngine() method.
Note the error and rectify it by removing the overriding attempt in the Car class.

## Solutions

### Final Circle
```java
public class Circle {
// Final constant for the value of PI
public final double PI = 3.14159;

    // Final variable for the circle's radius
    private final double radius;

    // Constructor
    public Circle(double radius) {
        this.radius = radius;
    }

    // Method to calculate the area of the circle
    public double area() {
        return PI * radius * radius;
    }

    public static void main(String[] args) {
        Circle circle = new Circle(5);  // circle of radius 5 units
        System.out.println("Area of the circle: " + circle.area());
    }
}
```
### final Car
```java
// Base class
class Vehicle {
    // Final method
    final void startEngine() {
        System.out.println("Engine started");
    }
}

// Derived class
class Car extends Vehicle {
// This method will throw a compile-time error since we're trying to override a final method.
// Comment this out to fix the error.
/*
@Override
void startEngine() {
System.out.println("Car engine started");
}
*/

    public static void main(String[] args) {
        Car car = new Car();
        car.startEngine();
    }
}
```
For the Car class in Exercise 2, you'll notice that if you try to override the startEngine() method, a compile-time error will occur. This is due to the final keyword in the Vehicle class's startEngine() method, which prevents it from being overridden in subclasses.

Remember, using the final keyword sends a clear signal to other developers about the intentions of the code, preventing accidental overrides or assignments.