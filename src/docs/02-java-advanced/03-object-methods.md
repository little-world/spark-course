# Object Methods

In Java, every class is a descendant of the Object class, either directly or indirectly. The Object class resides in the java.lang package. This class provides several important methods that are available to all Java objects. These methods are useful for basic operations like comparison, representation, and object manipulation.

Let's go over some of these essential Object class methods:

### toString
> `public String toString()`
   This method returns a string representation of the object. The default implementation returns a string in the format ClassName@HashCode. Most classes override this method to provide a more meaningful representation.

```java
@Override
public String toString() {
  return "This is a custom string representation of this object.";
}
```
### equals
> `public boolean equals(Object obj)`

This method checks if the current object is equal to the specified object obj. The default implementation checks for reference equality, but it's common to override this method in custom classes to provide a meaningful equality check.

When overriding the equals() method, it's also recommended to override the hashCode() method to maintain the contract that equal objects must have equal hashcodes.

```java
@Override
public boolean equals(Object obj) {
    if (this == obj) return true;
    if (obj == null || getClass() != obj.getClass()) return false;
    MyClass myObj = (MyClass) obj;
    return attribute1.equals(myObj.attribute1) && attribute2.equals(myObj.attribute2);
}
```
### hashCode
> `public int hashCode()`
  
This method returns the hashcode value of the object. If two objects are equal, their hashcodes must be the same. However, the reverse isn't necessarily true; two objects with the same hashcode aren't guaranteed to be equal.

When the equals() method is overridden in a class, the hashCode() method should also be overridden.

```java
@Override
public int hashCode() {
  return Objects.hash(attribute1, attribute2);
}
```
### clone

> `protected Object clone() throws CloneNotSupportedException`

This method creates and returns a copy of the object. The default implementation performs a shallow copy using object's fields. To use this method, the class must implement the Cloneable interface, or else a CloneNotSupportedException will be thrown.

```java
@Override
protected Object clone() throws CloneNotSupportedException {
   return super.clone();
}
```
### getClass
> `public final Class<?> getClass()`

This method returns the runtime class of the object. It's useful when you need meta-information about the object.

```java
Class<?> clazz = obj.getClass();
```

### wait, notify
These methods are related to synchronization. They are essential for inter-thread communication.

`wait()`: Causes the current thread to wait until it's notified.
`notify()`: Wakes up a single waiting thread.
`notifyAll()`: Wakes up all waiting threads.
Note: These methods should be called from a synchronized context (block or method).

### finalize
> `public final void finalize()`

This method gets called by the garbage collector on an object when it determines that there are no more references to the object. It's used for cleanup actions before the object is removed from memory. However, relying on finalize() is not recommended, and it has been deprecated since Java 9.

## Exercises

### a Book class
> `toString(), equals(), and hashCode()`

Problem Statement:
Create a Book class that has three attributes: title, author, and isbn. Override the toString(), equals(), and hashCode() methods.

The toString() method should return a string in the format: "Book: `[Title] by [Author]` (ISBN:` [isbn]`)".
Two books are considered equal if their ISBN numbers are the same.
Ensure the hashCode() method is consistent with your equals() method.

## Solution 
You can do this in IntelliJ with `generate...`