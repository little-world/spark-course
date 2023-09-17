# Streams
The Stream API, introduced in Java 8, represents a new abstraction of data manipulation using a functional approach. Streams allow for complex operations on data sources, such as collections, in a functional style, thereby providing a new and concise way to perform data operations.

### What is a Stream?

A stream is a sequence of elements that can be processed in parallel or sequentially. It's important to note that streams, unlike collections, are not a data structure that stores elements. Instead, they convey elements from a source such as collections, arrays, or I/O resources, through a pipeline of computational operations.

### Creating Streams


```java
List<String> myList = Arrays.asList("a1", "a2", "b1", "c2", "c1");
Stream<String> myStream = myList.stream();
```
```java
int[] myArray = {1, 2, 3, 4, 5};
IntStream streamFromArray = Arrays.stream(myArray);
```

```java
Stream<String> streamFromValues = Stream.of("a1", "a2", "b1");
```
```java
Stream<Integer> sequentialNumbers = Stream.iterate(0, n -> n + 1);
```

### Stream Intermediate Operations

Streams operations are either intermediate (return a stream) or terminal (return a result or produce a side effect).


#### filter:
Takes a predicate and returns a stream including elements that match.
```java
myList.stream()
  .filter(s -> s.startsWith("c"))
  .forEach(System.out::println);  // Outputs: c2, c1
```
#### map
Converts elements in a stream.

```java
myList.stream()
  .map(String::toUpperCase)
  .forEach(System.out::println);  // Outputs: A1, A2, B1, C2, C1
```

#### sorted
Sorts the stream's elements.

```java
myList.stream()
  .sorted()
  .forEach(System.out::println);  // Outputs: a1, a2, b1, c1, c2
```
### Terminal Operations:
#### forEach
Iterates over each element of the stream

#### collect
Accumulates elements of a stream into a collection.
```java
List<String> resultList = myList.stream()
  .map(String::toUpperCase)
  .collect(Collectors.toList());
```
#### match
Various matching operations.
```java
boolean anyStartsWithA = myList.stream()
.anyMatch(s -> s.startsWith("a"));  // true
```
### count
Counts elements in the stream.
```java
long startsWithB = myList.stream()
  .filter(s -> s.startsWith("b"))
  .count();  // Outputs: 1
```
### Parallel Streams

Streams can be processed in parallel to leverage multi-core architectures:

```java
myList.parallelStream()
  .sorted()
  .forEach(System.out::println);
```
### Reducing Streams

reduce is a terminal operation that performs a reduction on the elements of the stream:

```java
OptionalInt reduced = IntStream.range(1, 4)
  .reduce((a, b) -> a + b);
System.out.println(reduced.getAsInt());  // Outputs: 6
```
### Closing Remarks

- Streams are not collections: They don't have storage.
- Streams are lazy: Computations on streams are only performed when necessary.
- Streams are not reusable: Once consumed, a stream cannot be used again.
