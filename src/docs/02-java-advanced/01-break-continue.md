# Break and Continue
Let's dive into the break and continue statements in Java. Both of these statements are used to alter the flow of loops (for, while, and do-while).

### break Statement
The break statement is used to terminate the loop or a switch-case statement in which it is present. Once the loop is terminated, the program control resumes at the next statement following the loop.

Example: Using break in a for loop

```java
for (int i = 0; i < 10; i++) {
  if (i == 5)
    break;
  System.out.println(i);
}

// Output:
// 0
// 1
// 2
// 3
// 4
```
In the example above, the loop breaks when i becomes 5, so numbers from 5 to 9 are not printed.

### continue Statement
The continue statement skips the current iteration and jumps to the next iteration of the loop. It's used when you don't want a certain condition to process further, but you don't want to exit the loop entirely.

Example: Using continue in a for loop

```java
for (int i = 0; i < 10; i++) {
  if (i == 5) {
    continue;
  }
  System.out.print(i);
}

// Output:
// 0
// 1
// 2
// 3
// 4
// 6
// 7
// 8
// 9
```
In the example above, the number 5 is skipped because of the continue statement, but the loop continues with the next iteration.

### Labeled break and continue
In Java, we can also label loops. This is particularly useful when you have nested loops and you want to break out of or continue a specific outer loop.

Example: Using labeled break with nested loops

```java
outer:
for (int i = 0; i < 5; i++) {
  for (int j = 0; j < 5; j++) {
    if (i == 2 && j == 2) 
      break outer;
    System.out.println("i: " + i + ", j: " + j);
  }
}
```
Here, when i is 2 and j is 2, the break outer; statement terminates the outer loop completely, not just the inner loop.

Example: Using labeled continue with nested loops

```java
outer:
for (int i = 0; i < 5; i++) {
  for (int j = 0; j < 5; j++) {
    if (i == 2 && j == 2) 
      continue outer;
    System.out.println("i: " + i + ", j: " + j);
  }
}
```
Here, when i is 2 and j is 2, the continue outer; statement skips the current iteration of the outer loop, effectively terminating the current inner loop's execution and moving to the next iteration of the outer loop.

## Exercises

### First Non-Repeating Character
Problem Statement:

Given a string, find and print the first non-repeating character in it. If all characters are repeating, print "All characters repeat." Use loops and the break statement.

Sample Input & Output:
```text
Input: "swiss"
Output: "w"

Input: "apple"
Output: "a"

Input: "aabbcc"
Output: "All characters repeat."
```

### Skipping Even Numbers
Problem Statement:

Print numbers from 1 to 20, but skip even numbers using the continue statement.

Expected Output:
```text
1
3
5
7
9
11
13
15
17
19
```

### Labeled Break in Nested Loops
Problem Statement:

Given a 2D array (matrix) of numbers, find the first occurrence of the number 5. When you find it, print its position and break out of the loops.

Sample Input & Output:

```java
int[][] matrix = {
  {1, 2, 3},
  {4, 5, 6},
  {7, 8, 9}
};
```
Output:
```text
Number 5 found at position (1, 1)
```
Hint: Use labeled break to exit the nested loops once the number is found.


## Solutions
### First Non-Repeating Character
```java
public char firstNonRepeatingCharacter(String s) {
  for (int i = 0; i < s.length(); i++) {
    char c = s.charAt(i);
    if (s.indexOf(c) == s.lastIndexOf(c)) 
       return c;
  }
  return '#'; 
}
```

### Skipping Even Numbers
```java
public void printOddNumbers() {
  for (int i = 1; i <= 20; i++) {
    if (i % 2 == 0) 
      continue;
    System.out.println(i);
  }
}
```
### Labeled Break in Nested Loops
```java
public void findNumberInMatrix(int[][] matrix) {
  outer:
  for (int i = 0; i < matrix.length; i++) {
    for (int j = 0; j < matrix[i].length; j++) {
      if (matrix[i][j] == 5) {
        System.out.println("Number 5 found at position (" + i + ", " + j + ")");
        break outer;
      }
    }
  }
}
```
