# Java Basics


Here's a quick overview of some basic language elements in Java:

### Variables 
A variable is a name that represents a value. In Java, you must declare a variable with a specific data type, such as int, float, or String. For example:

```java
int age = 25;
float price = 19.99;
String name = "John";
```

- Data Types: Java has primitive data types such as int, double, boolean, and char, and also has object data types such as String, Array, and Class. Each data type has a different range of values and operations that can be performed on it.
- Operators: Java has a range of operators that can be used to perform operations on variables and values, such as arithmetic operators (+, -, *, /), comparison operators (==, !=, <, >), and logical operators (&&, ||).
- Control Structures: Java has control structures that allow you to execute specific blocks of code based on conditions or loops. For example, the if-else statement checks a condition and executes one block of code if the condition is true and another block of code if the condition is false. The for loop executes a block of code a specified number of times.
- Methods: A method is a block of code that performs a specific task. It can be called from other parts of the program and can take parameters as input and return values as output.

Here's an example program that uses some of these elements:

```java
public class HelloWorld {
  public static void main(String[] args) {
    String name = "John";
    int age = 25;
    float price = 19.99f;

    System.out.println("Hello, " + name + "!");
    System.out.println("You are " + age + " years old.");

    if (price > 10) {
      System.out.println("The price is too high!");
    } else {
      System.out.println("The price is affordable.");
    }

    for (int i = 1; i <= 10; i++) {
      System.out.println(i);
    }
  }
}
```
This program declares some variables, uses a conditional statement to check the price, and uses a for loop to print out the numbers 1-10. When you run this program, it will print out the following output:

```java
Hello, John!
You are 25 years old.
The price is too high!
1
2
3
4
5
6
7
8
9
10
```

