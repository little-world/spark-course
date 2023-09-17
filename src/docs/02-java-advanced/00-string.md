# String, StringBuilder


### Creation:
   Strings can be created in various ways:

```java
String str1 = "Hello, World!";
String str2 = new String("Hello, World!");
```

### String Properties
   Immutable: Once a String object is created, it cannot be changed. Any operation that seems to change a string actually creates a new string.
   Stored in String Pool: Literal strings (e.g., "Hello") are stored in a special pool in memory to save space. When you create a string using a literal, Java first looks in the string pool to see if an identical string already exists. If it does, the new string simply refers to the existing one. If it doesn't, a new string is created in the pool. 
###  Common Operations
#### Concatenation
```java
String str1 = "Hello";
String str2 = "World";
String str3 = str1 + ", " + str2 + "!";  // Results in "Hello, World!"
```

#### Length
```java
int len = str1.length();  // Returns 5
```
#### Substring
```java
String sub = str3.substring(7, 12);  // Returns "World"
```
### Replace
```java
String replaced = str3.replace("World", "Java");  // Returns "Hello, Java!"
```
#### Convert to Upper/Lower Case:
```java
String upper = str1.toUpperCase();  // Returns "HELLO"
String lower = str1.toLowerCase();  // Returns "hello"
```
#### Trim 
(removes leading and trailing whitespace)
```java
String str = "   Hello   ";
String trimmed = str.trim();  // Returns "Hello"
```
### Checking Equality
Always use equals method to check string content equality and == to check reference equality:

```java
String a = new String("Hello");
String b = new String("Hello");
boolean contentEquals = a.equals(b);  // Returns true
boolean referenceEquals = (a == b);   // Returns false
```
#### CharAt
```java
char ch = str1.charAt(1);  // Returns 'e'
```
#### Split
```java
String str = "apple,banana,orange";
String[] fruits = str.split(",");  // Results in array ["apple", "banana", "orange"]
```
### StringBuilder and StringBuffer:
If you need to perform many string modifications, consider using StringBuilder (not thread-safe) or StringBuffer (thread-safe). These classes are mutable and can help optimize performance for heavy string operations:

```java
StringBuilder sb = new StringBuilder();
sb.append("Hello");
sb.append(", ");
sb.append("World");
sb.append("!");
String result = sb.toString();  // Returns "Hello, World!"
```
### Important Methods
- `contains()`: Returns true if the string contains the specified sequence of char values.
- `endsWith()`: Tests if the string ends with the specified suffix.
- `startsWith()`: Tests if the string begins with the prefix.
- `indexOf()`: Returns the position of the first occurrence of specified character(s) in a string.
- `astIndexOf()`: Returns the position of the last occurrence of specified character(s) in a string.
- `isEmpty()`: Checks if the string is empty.
- `compareTo()`: Compares two strings lexicographically.


## Exercises


### String Length & Concatenation:
Problem Statement:

Given two strings, str1 and str2, concatenate them. If the length of the concatenated string is odd, add a ! at the end.

Sample Input & Output:

```text
Input: str1 = "Hello", str2 = "World"
Output: "HelloWorld!"

Input: str1 = "Java", str2 = "Land"
Output: "JavaLand"
```
### Uppercase & Lowercase
Problem Statement:

Given a string s, return the string where every odd-indexed character is in uppercase and every even-indexed character is in lowercase.

Sample Input & Output:

```text
Input: s = "programming"
Output: "pRoGrAmMiNg"
```
### Replace
Problem Statement:

Given a string, replace all vowels (a, e, i, o, u) with the # character.

Sample Input & Output:

```text
Input: s = "hello world"
Output: "h#ll# w#rld"
```
### Substring
   Problem Statement:

Find if the second string str2 exists as a substring in the first string str1. If it does, return the index where it starts. If it doesn't, return -1.

Sample Input & Output:

```text
Input: str1 = "I love programming", str2 = "love"
Output: 2

Input: str1 = "Java", str2 = "Python"
Output: -1
```
### CharAt
Problem Statement:

Given a string s and an integer n, return the nth character of the string if it exists. If n is larger than the string's length, return Out of bounds.

Sample Input & Output:

```text
Input: s = "apple", n = 3
Output: "p"

Input: s = "apple", n = 10
Output: "Out of bounds"
```
### Split
Problem Statement:

Given a sentence (words separated by spaces), return the number of words in the sentence.

Sample Input & Output:

```text
Input: s = "Java is a programming language"
Output: 5
```




### Exercise: Palindrome Checker
Problem Statement:

Write a function that checks if a given word or phrase is a palindrome.   
A palindrome is a word, phrase, number, or other sequences of characters which reads the same backward or forward. Ignore spaces, punctuation, and letter casing.

Sample Input & Output:
```text
Input: "A man a plan a canal Panama"
Output: true

Input: "Java"
Output: false
```
Hint: Consider converting the string to lowercase, removing non-alphanumeric characters, and then comparing it to its reverse.

### Exercise: Longest Substring Without Repeating Characters
Problem Statement:

Given a string, find the length of the longest substring without repeating characters.

Sample Input & Output:

```text
Input: "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.

Input: "bbbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.

Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
```
Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
Hint: Consider using the sliding window technique. Start with two pointers at the beginning of the string and move the second pointer to the right. As you move, keep track of the characters you've seen in a set. If you encounter a repeating character, move the first pointer to the right and remove characters from the set until the character is no longer in the set. Keep track of the maximum length of the substring you've found as you go.


## Solutions

### String Length & Concatenation
```java
public String concatenateStrings(String str1, String str2) {
    String result = str1 + str2;
    return (result.length() % 2 == 1) ? result + "!" : result;
}
```
### Uppercase & Lowercase:
```java
public String alterCase(String s) {
   StringBuilder sb = new StringBuilder();
   for (int i = 0; i < s.length(); i++) {
      char ch = (i % 2 == 0) ? Character.toLowerCase(s.charAt(i)) : Character.toUpperCase(s.charAt(i));
      sb.append(ch);
   }
   return sb.toString();
}
```
### Replace:
```java
public String replaceVowels(String s) {
   return s.replaceAll("[AEIOUaeiou]", "#");
}
```   
### Substring:
``` java
public int findSubstring(String str1, String str2) {
   return str1.indexOf(str2);
}
```
### CharAt:
```java
public String getNthCharacter(String s, int n) {
   if (n < s.length()) {
      return String.valueOf(s.charAt(n));
   } else {
      return "Out of bounds";
   }
}
```
### Split:
```java
public int countWords(String s) {
   return s.split(" ").length;
}
```

