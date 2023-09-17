# Object Oriented


Object-oriented programming is a programming paradigm that is based on the concept of objects. In Java, everything is an object, which means that programs are built around the interactions between objects. Here is a tutorial on object-oriented programming in Java:

### Classes and Objects
A class is a blueprint for creating objects. It defines the properties and methods that the objects will have. Here is the basic syntax for defining a class:

```java
public class ClassName {
// class variables and methods
}
```
The `public` keyword specifies the visibility of the class. 
The class name should start with a capital letter.

To create an object of a class, you use the new keyword:

```java
ClassName objectName = new ClassName();
```
Here is an example of a class that represents a car:

```java
public class Car {
  String make;
  String model;
  int year;

    public void start() {
      System.out.println("The car is starting.");
    }
    
    public void stop() {
      System.out.println("The car is stopping.");
    }
}
```
This class has three properties (make, model, and year) and two methods (start and stop).

To create an object of this class, you would use the following code:


```java
Car myCar = new Car();
myCar.make = "Honda";
myCar.model = "Civic";
myCar.year = 2022;

myCar.start();
```
This code creates a new Car object and sets its properties. It then calls the start method of the object.

###  Inheritance
Inheritance is a mechanism that allows you to create a new class based on an existing class. The new class, called the subclass, inherits the properties and methods of the existing class, called the superclass. Here is the basic syntax for defining a subclass:

```java
public class SubclassName extends SuperclassName {
// subclass variables and methods
}
```
The `subclass` can override the methods of the `superclass` and add new methods and properties. Here is an example of a subclass of the Car class:

```java
public class SportsCar extends Car {
  public void accelerate() {
    System.out.println("The sports car is accelerating.");
  }
}
```
This class inherits the properties and methods of the Car class and adds a new method (accelerate).

To create an object of this class, you would use the following code:


```java
SportsCar mySportsCar = new SportsCar();
mySportsCar.make = "Ferrari";
mySportsCar.model = "458";
mySportsCar.year = 2023;

mySportsCar.accelerate();
```
This code creates a new SportsCar object and sets its properties. It then calls the accelerate method of the object.

### Polymorphism
Polymorphism is the ability of an object to take on many forms. In Java, this is achieved through method overriding and method overloading. Method overriding allows a subclass to provide a specific implementation of a method that is already provided by its superclass. Method overloading allows a class to have two or more methods with the same name but different parameter lists.

Here is an example of method overriding:


```java
public class Vehicle {
  public void start() {
    System.out.println("The vehicle is starting.");
  }
}

public class Car extends Vehicle {
  @Override
  public void start() {
    System.out.println("The car is starting.");
  }
}
```
The Car class overrides the start method of the Vehicle class to provide a specific implementation for cars.

### Abstract Class
An abstract class in Java is a class that cannot be instantiated on its own. It serves as a blueprint for other classes to inherit from, and it can contain both concrete and abstract methods. An abstract method is a method that does not have a body and must be implemented by any concrete subclasses that inherit from the abstract class.

```java

public abstract class Animal {
  public void eat() {
    System.out.println("Animal is eating.");
  }

  public abstract void makeSound();
}
```
In this example, Animal is an abstract class that has a concrete method eat() and an abstract method makeSound(). Any class that inherits from Animal must implement the makeSound() method.

### Interface
An interface in Java is a collection of abstract methods that can be implemented by any class that implements the interface. An interface can also include constant variables, default methods, and static methods. A class can implement multiple interfaces, but it cannot extend multiple classes.

```java
public interface Drawable {
  void draw();
}
```
In this example, Drawable is an interface with a single abstract method draw(). Any class that implements Drawable must provide an implementation for the draw() method.

```java
public class Circle implements Drawable {
  public void draw() {
    System.out.println("Drawing a circle.");
  }
}
```
In this example, Circle is a class that implements Drawable and provides an implementation for the draw() method
