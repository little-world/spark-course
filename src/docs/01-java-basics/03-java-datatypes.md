# Data Types

In Java, there are two categories of data types: primitive data types and object/reference data types. Here is a brief overview of each:

## Primitive Data Types

- boolean: represents a true/false value.
- byte: an 8-bit integer.
- short: a 16-bit integer.
- int: a 32-bit integer.
- long: a 64-bit integer.
- float: a single-precision 32-bit floating-point number.
- double: a double-precision 64-bit floating-point number.
- char: a single Unicode character represented by 16 bits.


###  Examples

```java
// Declaring and initializing an int variable
int age = 25;

// Declaring and initializing a long variable
long population = 10000000000L;

// Declaring and initializing a double variable
double price = 19.99;

// Declaring and initializing a boolean variable
boolean isTrue = true;
```
In the above examples, int is used to represent integer values, long is used to represent larger integer values, double is used to represent decimal or floating-point values, and boolean is used to represent a true or false value.

Note that for long values, you need to add the suffix L to the end of the number to indicate that it is a long value. Similarly, for float values, you need to add the suffix f to the end of the number. This is because by default, Java treats any whole number as an int and any decimal number as a double.

Here's an example of how to use these variables in a program:

```java
public class Example {
  public static void main(String[] args) {
    int age = 25;
    long population = 10000000000L;
    double price = 19.99;
    boolean isTrue = true;

    System.out.println("Age: " + age);
    System.out.println("Population: " + population);
    System.out.println("Price: $" + price);
    System.out.println("Is true? " + isTrue);
  }
}
```
When you run this program, it will output:

```java
Age: 25
Population: 10000000000
Price: $19.99
Is true? true
```

## Object/Reference Data Types

- String: a sequence of characters.
- Array: a collection of elements of the same data type.
- Class: represents a class or interface.
- Interface: represents an interface type.
- Enum: represents an enumerated type.
- Object: represents any Java object.

Primitive data types are basic types that are built into the Java language, whereas object/reference data types are more complex types 

### Examples

Here are a few examples of Java object references:

#### String
Strings are reference types, which means that a variable of type String holds a reference to an object of type String. For example, the following code creates a new String object and assigns a reference to it to the variable "myString":
```java
String myString = new String("Hello, World!");
```
#### Array  
Arrays are also reference types. When you declare an array, you are actually creating a reference to an object that holds the array elements. For example, the following code creates an array of integers and assigns a reference to it to the variable "myArray":

```java
int[] myArray = new int[10];
```


#### Object References
You can create your own classes and create objects of those classes. When you create an object of a class, you are actually creating a reference to an object of that class. For example, the following code creates a new object of the class "Person" and assigns a reference to it to the variable "myPerson":

```java
Person myPerson = new Person("John", "Doe");
```
In all of these examples, the variables are references to objects in memory, rather than the objects themselves. This means that you can manipulate the objects by using their references, such as calling methods on them or passing them as parameters to other methods.
