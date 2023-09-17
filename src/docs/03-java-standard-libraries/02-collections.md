# Collections
Java Collections Framework Tutorial
1. What is the Collections Framework?

The Collections Framework provides a unified architecture for representing and manipulating collections. This framework includes:
### Core Collection Interfaces

- `List`: An ordered collection. Allows duplicate elements.
- - `ArrayList`: Resizable array implementation.
- - `LinkedList`: Doubly-linked list implementation.
- - `Vector`: Similar to ArrayList, but thread-safe.
- `Set`: A collection that does not allow duplicate elements.
- - `HashSet`: Uses a hash table for storage. No order.
- - `LinkedHashSet`: Ordered by the insertion order.
- - `TreeSet`: Stored in a sorted order (red-black tree).
- `Queue`: A collection designed for holding elements prior to processing.
- - `PriorityQueue`: Elements ordered by their natural ordering or by a comparator.
- - `ArrayDeque`: Resizable array that can be used as a stack or a queue.
- - `Deque`: Extends Queue to handle elements at both ends.
- - `ArrayDeque`: Can be used as both a queue and a stack.
- `Map`: An object that maps keys to values. No duplicate keys.
- - `HashMap`: Uses a hash table to store key-value pairs.
- - `TreeMap`: Red-black tree-based implementation.
- - `LinkedHashMap`: Hash table and linked list implementation.
- - `Hashtable`: Similar to HashMap, but thread-safe.

### Operations

#### Creation
```java
List<String> list = new ArrayList<>();
Set<Integer> set = new HashSet<>();
Map<String, Integer> map = new HashMap<>();
```
#### Adding Elements
```java
list.add("A");
set.add(1);
map.put("One", 1);
```
#### Removing Elements
```java
list.remove("A");
set.remove(1);
map.remove("One");
```
### Iteration
```java
for(String item : list) 
  System.out.println(item);

```
### Size and Contents:
```java
int size = list.size();
boolean containsA = list.contains("A");
```
### Algorithms:

The Collections class provides static methods that are applicable to various collections. Examples include:

- `Sorting`: Collections.sort(list)
- `Shuffling`: Collections.shuffle(list)
- `Searching`: Collections.binarySearch(list, key)
-  `Max/Min`: Collections.max(list) or Collections.min(list)

### Thread Safety:

Not all collection implementations are thread-safe. If multiple threads access a collection concurrently and at least one thread modifies it, it must be synchronized externally. For thread-safe collection alternatives, you might consider:

- `Vector` (thread-safe alternative to ArrayList)
- `Hashtable` (thread-safe alternative to HashMap)
- `Collections.synchronizedList(), Collections.synchronizedSet(), Collections.synchronizedMap()` for wrapping collections in synchronized versions.

### Collections and Streams

Java 8 introduced the Stream API, allowing for more functional and concise operations on collections. For example:

```java
list.stream().filter(item -> item.startsWith("A")).forEach(System.out::println);
```
