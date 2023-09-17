# Static

The static keyword in Java has a few distinct and important uses. This tutorial will provide a comprehensive overview of the static keyword, its use cases, and its importance in Java development.

### static Variables (Static Fields):
   A static variable belongs to the class rather than any specific instance. This means that only one copy of a static variable exists, regardless of the number of instances of the class.
   It can be accessed directly with the class name, without needing to create an instance of the class.
```java
class MyClass {
    static int staticVariable = 10;
}
// Accessing the static variable
int value = MyClass.staticVariable;
```
Characteristics:

- They get memory only once, at the time of class loading.
- They are initialized before instance variables, so you can refer to a static variable in the initializer of an instance variable.

### static Methods (Static Functions):
Just like static variables, static methods belong to the class and not to any specific instance. 

- They can only directly call other static methods and access static data.
- They cannot refer to this or super keywords in any way.

```java
class MyClass {
    static void staticMethod() {
        System.out.println("This is a static method.");
    }
}

// Calling the static method
MyClass.staticMethod();
```
### static Block:
Used to initialize static variables.
- Gets executed once when the class is loaded into memory.
  
```java
class MyClass {
    static int staticVariable;

    static {
        staticVariable = 10;
        System.out.println("Static block executed!");
    }
}
```

### static Nested Classes:
   A nested class that's declared static is called a static nested class.
   
They can be accessed without instantiating the outer class.
```java
class OuterClass {
    static class StaticNestedClass {
// ... body of static nested class ...
    }
}
   ```
You can create an instance of the static nested class using the outer class name:

```java
OuterClass.StaticNestedClass obj = new OuterClass.StaticNestedClass();
```

### When to use static:\

- `Utility or Helper Methods`: Functions that don't rely on instance variables. For example, methods in the Math class (Math.sqrt(), Math.min()).
- `Constants`: Variables expected to remain unchanged and have only one copy like Math.PI.
- `Counter Variables`: To count the number of instances of a class.
= `Static Initializers`: When some static fields require complex initialization.

### Important Points

- Overloading is possible, but overriding is not possible for static methods.
- static methods can't be abstract.
- Local inner classes cannot be marked static.
- Instance methods can access static variables/methods, 
- The reverse is not true. Static methods can't directly access non-static members of the class.

## Exercises
### Counter
Problem Statement:
Create a class named Student. Every time an instance of Student is created, increment a static variable named studentCount. Implement a static method named getStudentCount that returns the number of instances of the Student class that have been created.

Tasks:

- Create the Student class.
- Create and initialize the studentCount variable.
- Update the constructor to increment the count.
- Implement the getStudentCount method.


### MathUtils
Problem Statement:
Create a class named MathUtil that provides utility methods:

- A static final double variable PI with the value 3.14159.
- A static method square that accepts an integer and returns its square.
- A static method circleArea that accepts a double representing a circle's radius and returns its area.
Tasks:

Create the MathUtil class with the mentioned variable and methods.
In a main method, use the circleArea method to compute the area of a circle with a radius of 5 using the provided PI value.


### Database Initialization
Problem Statement:
Create a class named DatabaseConfig. The class should have:

- A private static String variable databaseURL.
- A static block that initializes databaseURL based on some logic (e.g., based on system properties or some condition).
- A static method getDatabaseURL that returns the databaseURL.

- Tasks:

Create the DatabaseConfig class with the static variable and block.
In the static block, set the databaseURL to "jdbc:mysql://localhost:3306/mydb" or any mock URL of your choice.
Implement the getDatabaseURL method.

## Solutions

### Counter
```java
class Student {
// Static variable to count students
private static int studentCount = 0;

    // Constructor
    public Student() {
        studentCount++;  // Increment count every time a new instance is created
    }

    // Static method to get student count
    public static int getStudentCount() {
        return studentCount;
    }

    public static void main(String[] args) {
        new Student();
        new Student();
        System.out.println("Number of students: " + Student.getStudentCount()); // Outputs: 2
    }
}
```
### MathUtils

```java
class MathUtil {
// Static constant for the value of PI
public static final double PI = 3.14159;

    // Static method to return the square of a number
    public static int square(int number) {
        return number * number;
    }

    // Static method to calculate the area of a circle
    public static double circleArea(double radius) {
        return PI * radius * radius;
    }

    public static void main(String[] args) {
        System.out.println("Area of circle with radius 5: " + MathUtil.circleArea(5));  // Using the PI value
    }
}
```
### Database Initialization
```java
class DatabaseConfig {
// Static variable for database URL
    private static String databaseURL;

    // Static block to initialize the database URL
    static {
        // Logic or conditions to set databaseURL can be added here
        // For the purpose of this solution, we'll simply assign a mock URL
        databaseURL = "jdbc:mysql://localhost:3306/mydb";
    }

    // Static method to get the database URL
    public static String getDatabaseURL() {
        return databaseURL;
    }

    public static void main(String[] args) {
        System.out.println("Database URL: " + DatabaseConfig.getDatabaseURL()); // Outputs the mock URL
    }
}
```