# Control Structures 

In Java, control structures are used to control the flow of execution of a program. They are used to make decisions, to repeat statements, and to jump to different parts of the program. There are three main types of control structures in Java: conditional statements, loops, and branching statements.

##Conditional Statements
Conditional statements are used to execute different blocks of code based on certain conditions. There are two main types of conditional statements in Java: if statements and switch statements.

### if
If statements are used to execute a block of code if a certain condition is true. Here is an example:

```java
int x = 5;
if (x < 10) {
  System.out.println("x is less than 10");
}
```
In this example, the code inside the curly braces will only be executed if the condition inside the parentheses is true.

### switch
Switch statements are used to execute different blocks of code based on the value of a variable. Here is an example:

```java
int dayOfWeek = 3;
switch (dayOfWeek) {
  case 1:
    System.out.println("Monday");
  break;
  case 2:
    System.out.println("Tuesday");
  break;
  case 3:
    System.out.println("Wednesday");
  break;
  default:
    System.out.println("Invalid day");
  break;
}
```
In this example, the code inside the block associated with the value of the variable dayOfWeek will be executed.

## Loops
Loops are used to execute a block of code multiple times. There are three main types of loops in Java: for loops, while loops, and do-while loops.

### for loop
For loops are used to execute a block of code a specific number of times. Here is an example:

```java
for (int i = 0; i < 10; i++) {
  System.out.println("i is " + i);
}
```
In this example, the block of code inside the curly braces will be executed 10 times.

### while loop
While loops are used to execute a block of code while a certain condition is true. Here is an example:

```java
int i = 0;
while (i < 10) {
  System.out.println("i is " + i);
  i++;
}
```
In this example, the block of code inside the curly braces will be executed as long as the condition inside the parentheses is true.

### do-while loop
Do-while loops are similar to while loops, but they will always execute the block of code at least once. Here is an example:

```java
int i = 0;
do {
  System.out.println("i is " + i);
  i++;
} while (i < 10);
```
In this example, the block of code inside the curly braces will be executed at least once, and then it will continue to execute as long as the condition inside the parentheses is true.

##Branching Statements
Branching statements are used to jump to different parts of the program. There are two main types of branching statements in Java: break statements and continue statements.

### Break
Break statements are used to exit a loop or switch statement. Here is an example:

```java
for (int i = 0; i < 10; i++) {
  if (i == 5) 
    break;
  System.out.println("i is " + i);
}
```
In this example, the loop will exit when i is equal to 5.

### continue
Continue statements are used to skip the current iteration of a loop. Here is an example:

```java
for (int i = 0; i < 10; i++) {
  if (i == 5) 
    continue;
  System.out.println("i is " + i);
}
```
In this example, the loop will skip the value 5.
