# Exceptions

In Java, an exception is an event that occurs during the execution of a program that disrupts the normal flow of instructions. Exceptions are used to handle errors and other exceptional events that may occur during the execution of a program.

Java has two types of exceptions:

- `Checked exceptions` must be handled by the programmer, either by using a try-catch block or by declaring the exception to be thrown by the method.
- `Unchecked exceptions`, on the other hand, do not need to be handled explicitly by the programmer.

### Checked Exception
Here's an example of a try-catch block that handles a checked exception:

```java
public void readFile() {
  try {
    BufferedReader reader = new BufferedReader(new FileReader("file.txt"));
    String line = reader.readLine();
    while (line != null) {
      System.out.println(line);
      line = reader.readLine();
    }
    reader.close();
  } catch (IOException e) {
    System.out.println("An error occurred while reading the file: " + e.getMessage());
  }
}
```
In this example, the readFile() method attempts to read from a file using a BufferedReader. If an IOException occurs (which is a checked exception), the catch block is executed and the error message is printed to the console.

Here are some examples of checked exceptions:

- `IOException`: This exception is thrown when an input/output operation fails, such as when a file cannot be opened or read.
- `ClassNotFoundException`: This exception is thrown when a class cannot be found by the class loader.
- `InterruptedException`: This exception is thrown when a thread is interrupted while it is sleeping or waiting.
- `SQLException`: This exception is thrown when an error occurs while working with a database.
- `FileNotFoundException`: This exception is thrown when a file cannot be found at the specified path.
- `ParseException`: This exception is thrown when a date or time cannot be parsed from a string.
- `NoSuchMethodException`: This exception is thrown when a method is not found in a class.



### Unchecked Exception
Here's an example of a method that throws an unchecked exception:

```java
public int divide(int a, int b) {
  if (b == 0) {
    throw new ArithmeticException("Cannot divide by zero");
  }
  return a / b;
}
```
In this example, the divide() method checks if the b parameter is zero, and if it is, it throws an ArithmeticException (which is an unchecked exception). If the b parameter is not zero, the method performs the division and returns the result.


Here are some examples of unchecked exceptions:

- `NullPointerException`: This exception is thrown when a program attempts to access a null object or reference.
- `ArrayIndexOutOfBoundsException`: This exception is thrown when a program attempts to access an array element with an index that is out of range.
- `ClassCastException`: This exception is thrown when a program attempts to cast an object to a class of which it is not an instance.
- `ArithmeticException`: This exception is thrown when a program attempts to divide by zero.
- `IllegalArgumentException`: This exception is thrown when a method is called with an illegal or inappropriate argument.
- `IllegalStateException`: This exception is thrown when a program is in an inappropriate state or has violated an invariant.
- `UnsupportedOperationException`: This exception is thrown when an unsupported operation is attempted on a collection or other data structure.
- `NumberFormatException`: This exception is thrown when a program attempts to parse a string that cannot be interpreted as a number.

### try-catch
A try-catch block is used to catch and handle exceptions that occur within a block of code. The try block contains the code that might throw an exception, and the catch block contains the code that handles the exception if it is thrown. If an exception is thrown inside the try block, the control flow jumps to the catch block, which handles the exception and then continues with the rest of the program.

Here's an example of a try-catch block:

```java
public void readFile() {
  try {
    BufferedReader reader = new BufferedReader(new FileReader("file.txt"));
    String line = reader.readLine();
    while (line != null) {
      System.out.println(line);
      line = reader.readLine();
    }
    reader.close();
  } catch (IOException e) {
    System.out.println("An error occurred while reading the file: " + e.getMessage());
  }
}
```
In this example, the try block attempts to read from a file using a BufferedReader. If an IOException occurs (which is a checked exception), the catch block is executed and the error message is printed to the console.

On the other hand, the throws keyword is used to declare that a method might throw a checked exception. When a method is declared to throw an exception, it means that the method is not handling the exception itself and is instead passing the responsibility of handling the exception to the calling method.

### try-catch-finally

The `try-catch-finally` block is used to handle exceptions that might occur within a block of code. The try block contains the code that might throw an exception, the catch block contains the code that handles the exception if it is thrown, and the finally block contains the code that is always executed, regardless of whether an exception is thrown or not.

```java
public void readFile() {
  BufferedReader reader = null;
  try {
    reader = new BufferedReader(new FileReader("file.txt"));
    String line = reader.readLine();
    while (line != null) {
      System.out.println(line);
      line = reader.readLine();
    }
  } catch (IOException e) {
    System.out.println("An error on reading: " + e.getMessage());
  } finally {
    try {
      if (reader != null) {
        reader.close();
      }
    } catch (IOException e) {
      System.out.println("An error on closing: " + e.getMessage());
    }
  }
}
```
In this example, the try block attempts to read from a file using a BufferedReader. If an IOException occurs (which is a checked exception), the catch block is executed and the error message is printed to the console. The finally block contains code that always executes, regardless of whether an exception is thrown or not.

In the finally block, the close() method on the BufferedReader object is called to release any resources that the object may be holding. If an IOException occurs while closing the file, the catch block within the finally block is executed and the error message is printed to the console.

Using a finally block ensures that important cleanup code is always executed, even if an exception occurs. For example, if a file is opened within a try block, it is important to make sure that the file is closed in the finally block, even if an exception is thrown.


### try-with-resources

`AutoCloseable` is an interface that defines a single method called close(), which is used to release any resources that the object may be holding. AutoCloseable is implemented by classes that manage resources that must be explicitly released, such as files, streams, and sockets.

The `java.io.Closeable` interface extends AutoCloseable and defines an additional method called close() that throws an IOException. This method is used to release any resources that the object may be holding, and to handle any exceptions that may occur while doing so.

When you use a class that implements AutoCloseable or Closeable, it is best practice to use a try-with-resources block to ensure that the close() method is called automatically when the block is exited, even if an exception is thrown. The try-with-resources statement automatically calls the close() method on all resources that are declared in the statement's header.

Here's an example of using a try-with-resources block to handle a Closeable resource:

```java
try (BufferedReader reader = new BufferedReader(new FileReader("file.txt"))) {
  String line = reader.readLine();
  while (line != null) {
    System.out.println(line);
    line = reader.readLine();
  }
} catch (IOException e) {
  System.out.println("An error occurred while reading the file: " + e.getMessage());
}
```
In this example, the BufferedReader object is declared in the try-with-resources statement, and the readLine() method is called inside the block. When the block is exited, the close() method on the BufferedReader object is called automatically.

If an IOException occurs while reading the file, the catch block is executed and the error message is printed to the console.

### throws
Here's an example of a method that declares that it throws an exception:

```java
public int divide(int a, int b) throws ArithmeticException {
  if (b == 0) {
    throw new ArithmeticException ("Cannot divide by zero");
  }
  return a / b;
}
```
In this example, the divide() method checks if the b parameter is zero, and if it is, it throws an ArithmeticException (which is a checked exception). The throws keyword in the method signature indicates that the method might throw an exception, and the responsibility of handling the exception is passed to the calling method.

In general, it is best practice to use a try-catch block to handle exceptions whenever possible, as it provides a more robust error handling mechanism. However, there are situations where using throws is more appropriate, such as when you want to force the calling method to handle the exception.

