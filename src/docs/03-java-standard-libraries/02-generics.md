# Generics

Generics are a way to define classes, interfaces, and methods that can work with different types of data, without specifying the actual types until runtime. This allows for more flexible and reusable code, and helps to prevent errors caused by type mismatches.

### Generic Class
Here is a simple example of a generic class in Java:

```java
public class MyGenericClass<T> {
  private T data;

  public MyGenericClass(T data) {
    this.data = data;
  }

  public T getData() {
    return data;
  }
}
```
In this example, we define a generic class MyGenericClass with a type parameter T. The class has a constructor that takes a parameter of type T, and a method getData() that returns a value of type T.


To use this class with a specific type, we specify the type parameter in angle brackets when creating an instance of the class:


```java
MyGenericClass<String> stringObj = new MyGenericClass<>("Hello, world!");
String data = stringObj.getData();
```
In this example, we create an instance of MyGenericClass with a type parameter of String, and pass the string "Hello, world!" to the constructor. We then call the getData() method to retrieve the value of the data field, which is a string.

### Generic Method
Here's another example, this time with a generic method:

```java
public class MyUtils {
  public static <T> void printArray(T[] array) {
    for (T item : array) {
      System.out.println(item);
    }
  }
}
```
In this example, we define a generic method printArray that takes an array of type T and prints each element to the console. The <T> before the return type specifies the type parameter.

To use this method with a specific type, we pass an array of that type to the method:

```java
String[] stringArray = {"foo", "bar", "baz"};
MyUtils.printArray(stringArray);
```
In this example, we call the printArray method with an array of strings. The method uses the type parameter T to determine the type of the array elements, and prints each string to the console.

Generics in Java can be used with classes, interfaces, methods, and even with wildcards to allow for even more flexibility in type definitions. They are an important part of modern Java programming and are used extensively in many libraries and frameworks


### Standard Libraries

#### List<E>
Using the List interface with a generic type parameter:
```java
List<String> myList = new ArrayList<>();
myList.add("apple");
myList.add("banana");
myList.add("cherry");
String first = myList.get(0); // returns "apple"
```

In this example, we create a new ArrayList instance that can hold elements of type String. We add some strings to the list and then retrieve the first element using the get method. Since we specified the generic type parameter as String, the get method returns a String object.

#### Map<K, V>
Using the Map interface with generic type parameters:


```java
Map<String, Integer> myMap = new HashMap<>();
myMap.put("apple", 1);
myMap.put("banana", 2);
myMap.put("cherry", 3);
int value = myMap.get("banana"); // returns 2
```
In this example, we create a new HashMap instance that maps strings to integers. We add some key-value pairs to the map and then retrieve the value associated with the "banana" key using the get method. Since we specified the generic type parameters as String and Integer, the get method returns an Integer object.

#### Comparable<T>
Using the Comparable interface to compare objects:
```scala
public class Person implements Comparable<Person> {
  private String name;
  private int age;

  public Person (String name, int age) {
    this.name = name;
    this.age = age;
  }

  public int compareTo(Person other) {
    return Integer.compare(this.age, other.age);
  }
}

Person p1 = new Person("Alice", 30);
Person p2 = new Person("Bob", 25);
int result = p1.compareTo(p2); // returns 1
```
In this example, we define a Person class that implements the Comparable interface with a generic type parameter of Person. We define a compareTo method that compares two Person objects based on their ages. We create two Person objects and compare them using the compareTo method. Since p1 is older than p2, the compareTo method returns a positive value.
