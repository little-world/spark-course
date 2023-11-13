# RDD Usage

### Creating RDDs
There are two main ways to create RDDs in Spark:

#### Parallelizing an existing collection:

This is done by passing an existing collection to SparkContext’s parallelize method.

```python
from pyspark import SparkContext
sc = SparkContext("local", "First Spark App")

# Example data
data = [1, 2, 3, 4, 5]

# Parallelizing data
distributed_data = sc.parallelize(data)
```

#### Referencing an external dataset:
You can create RDDs from external storage like HDFS, HBase, or shared file systems.

```python
# Creating an RDD from a text file
file_rdd = sc.textFile("path/to/file.txt")
```

### Basic Operations
RDDs support two types of operations:

#### Transformations:
These are operations that create a new dataset from an existing one. Examples include map, filter, flatMap, etc.
```python
# Using map to square each element
squared_rdd = distributed_data.map(lambda x: x * x)
```

#### Actions:
These are operations that return a value to the driver program after running a computation on the dataset. Examples include reduce, collect, count, first, etc.

```python
# Collecting data
result = squared_rdd.collect()
print(result) # Output: [1, 4, 9, 16, 25]
```

### Persisting RDDs
Persistence (or caching) is a key property of RDDs, allowing users to keep intermediate results in memory for fast access in subsequent stages.

```python
# Persisting an RDD in memory
squared_rdd.persist()
```

### Example Use Case
Here's a simple example of using RDDs to compute the sum of squares of numbers:

```python
# Parallelize data
data = [1, 2, 3, 4, 5]
rdd = sc.parallelize(data)

# Apply transformation
squared_rdd = rdd.map(lambda x: x * x)

# Apply action
sum_of_squares = squared_rdd.reduce(lambda x, y: x + y)
print(sum_of_squares)  # Output: 55
```

### Closing the SparkContext
Finally, when you're done with your application, you should close the SparkContext to free up resources.

```python
sc.stop()
```

## Exercises

#### Word Count
Count the number of occurrences of each word in a given text file.

Steps:

- Read a text file into an RDD using textFile method.
- Split each line into words using the flatMap transformation.
- Map each word to a tuple containing the word and the number 1.
- Use the reduceByKey transformation to sum up the counts for each word.
- Collect the results and print them.

####  Prime Numbers
 Given a range of numbers, find all prime numbers within that range using RDDs.

Steps:

- Create an RDD with numbers in the given range.
- Use the filter transformation to find prime numbers.
- Collect and print the prime numbers.
- 

#### Average in Each Category
Given a list of tuples in the form (category, number), compute the average of numbers for each category.

Steps:

- Create an RDD with the given list of tuples.
- Use mapValues to convert each number to a tuple of (number, 1).
- Use reduceByKey to sum the numbers and counts for each category.
- Map each category to its average.
- Collect and print the results.


## Solutions

#### Word Count
```python
from pyspark import SparkContext

sc = SparkContext("local", "Word Count")

# Reading data
text_rdd = sc.textFile("path/to/textfile.txt")

# Processing
word_counts = (text_rdd.flatMap(lambda line: line.split(" "))
                        .map(lambda word: (word, 1))
                        .reduceByKey(lambda a, b: a + b))

# Collecting results
for word, count in word_counts.collect():
    print(f"{word}: {count}")

sc.stop()

```

### Find primes
```python
def is_prime(n):
    if n <= 1:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

# Range for numbers
start, end = 2, 50

# Finding primes
primes = sc.parallelize(range(start, end + 1)).filter(is_prime)

# Print results
print(primes.collect())

sc.stop()

```

### Average in Each Category

```python
def is_prime(n):
    if n <= 1:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

# Range for numbers
start, end = 2, 50

# Finding primes
primes = sc.parallelize(range(start, end + 1)).filter(is_prime)

# Print results
print(primes.collect())

sc.stop()

```
