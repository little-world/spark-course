# Methods

In Java, a method is a set of instructions that performs a specific task. Methods are used to break down large programs into smaller, more manageable pieces. They also make programs more modular and easier to understand. Here is a tutorial on Java methods:

### Defining a Method
To define a method, you must specify its name, return type, and parameter list (if any). Here is the basic syntax for defining a method:

```java
returnType methodName(parameterList) {
  // method body
  return returnValue;
}
```
- The `returnType` specifies the type of value that the method will return. If the method does not return a value, the return type should be void.

- The `methodName` specifies the name of the method.

- The `parameterList` specifies the parameters that the method takes. If the method does not take any parameters, the parameter list should be empty.

- The `method body` contains the code that is executed when the method is called.

- The `returnValue` is the value that the method returns. If the method does not return a value, the return statement should be omitted.

Here is an example of a method that takes two integers as parameters and returns their sum:

```java
public static int sum(int a, int b) {
  int result = a + b;
  return result;
}
```
### Calling a Method
To call a method, you must specify its name and pass in any required parameters. Here is the basic syntax for calling a method:

```java
returnType result = methodName(argumentList);
```
- The `methodName` specifies the name of the method.

- The `argumentList` specifies the arguments that are passed to the method. If the method does not take any arguments, the argument list should be empty.

- The `result` variable stores the value that is returned by the method.

Here is an example of calling the sum method defined earlier:

```java
int a = 5;
int b = 7;
int result = sum(a, b);
System.out.println(result);
```
- `public`: The method is accessible from anywhere in the program.
- `private`: The method is only accessible within the class in which it is defined.
- `protected`: The method is accessible within the class in which it is defined and its subclasses.
- `default`: The method is only accessible within the same package.
Here is an example of a method with the public access modifier:

```java
public static void greet(String name) {
  System.out.println("Hello, " + name + "!");
}
```
This method can be called from anywhere in the program.

### Overloading Methods
In Java, you can define multiple methods with the same name as long as they have different parameter lists. This is called method overloading. Here is an example:

```java
public static int sum(int a, int b) {
return a + b;
}

public static int sum(int a, int b, int c) {
return a + b + c;
}
```
These two methods have the same name, but they take different numbers of parameters. You can call each method with the appropriate number of arguments.

```java
int a = 5;
int b = 7;
int c = 10;

int result1 = sum(a, b);
int result2 = sum(a, b, c);

System.out.println(result1);
System.out.println(result

```
