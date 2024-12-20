# Working with Java Data Types

## Preparing the OCP Exam

1. Working with Java data types
2. Controlling program flow
3. Object-oriented programming principles + Annotations
4. Exception handling
5. Arrays and collections
6. Lambda expressions and streams
7. Java Platform Module System
8. Concurrency
9. Input/Output (I/O) + Secure coding practices
10. Database applications with JDBC
11. Localization

This README is focused on **1. Working with Java data types**.

## Summary
This document provides a comprehensive guide to the following topics related to Java data types and their usage:

1. **Major Components of Java**:
    - JDK (Java Development Kit) and its tools.
    - JRE (Java Runtime Environment) and its evolution.

2. **Building Blocks**:
    - Class structure: Fields, methods, and object creation.
    - Comments: Types and usage.
    - The `main()` method: Structure and variations.
    - Packages: Creation, importing, and managing conflicts.

3. **Objects**:
    - Object creation and constructors.

4. **Data Types**:
    - Primitive types: Characteristics and usage.
    - Wrapper classes: Enhancing primitives with object functionality.

5. **Strings**:
    - Common methods and manipulations.
    - String pool behavior and optimizations.

6. **Dates and Times**:
    - Working with date/time classes like `LocalDate`, `LocalTime`, and `ZonedDateTime`.
    - Methods for manipulation and comparisons.
    - Usage of periods and durations.

Each topic is covered in detail to provide practical insights and examples.

---

## Major Components of Java

### Java Development Kit (JDK)
The JDK is essential for Java development. It includes tools needed to compile, run, and package Java programs. Key features include:

- **Oracle's JDK and OpenJDK**: Two common implementations of the JDK. Versions such as 1.8 and 17 are widely used.
- **Key Commands**:
    - `javac`: Compiles `.java` source files into `.class` bytecode files.
    - `java`: Executes compiled Java programs.
    - `jar`: Packages multiple files into a Java Archive (JAR).
    - `javadoc`: Generates documentation from comments in source files.

### Java Runtime Environment (JRE)
The JRE allows the execution of Java programs. Differences across versions include:

- **Java 8 and Earlier**: The JRE was a subset of the JDK.
- **Java 9 and Later**: The full JDK is used to both develop and run Java applications, simplifying the toolset.

---

## Building Blocks of Java

### Class Structure
#### Classes
Classes are fundamental units of a Java program. They serve as blueprints for creating objects. Key points include:

- **Object Creation**: Most often, classes are used to create objects (instances of classes).
- **Instance vs. Blueprint**: An object represents a specific realization of a class.
- **References**: Variables that point to objects.

#### Fields and Methods

- **Fields**: Store data about the object's state.
- **Methods**: Define behaviors or operations on the state of objects.
- Fields and methods together form the core structure of a Java class.

**Example**:
```java
public class Student {
    String name;

    public String getName() {
        return name;
    }

    public void setName(String theName) {
        name = theName;
    }
}
```

### Comments in Java

Java supports three types of comments:

1. **Single-line**: Use `//` to comment until the end of the line.
   ```java
   // This is a single-line comment
   ```
2. **Multi-line**: Use `/* ... */` for blocks of text.
   ```java
   /*
    * Multi-line comment
    */
   ```
3. **Javadoc**: Use `/** ... */` to generate documentation.
   ```java
   /**
    * @author John Doe
    */
   ```

---

### The `main()` Method

The `main()` method is the entry point of a Java program. It must be defined as:

```java
public static void main(String[] args)
```

- **`public`**: The method is accessible from anywhere.
- **`static`**: It belongs to the class rather than instances.
- **`void`**: It does not return any value.
- **`String[] args`**: Accepts command-line arguments as an array of strings.

**Variants**:
```java
static public void main(String[] args) { }
public static void main(String... args) { }
public final static void main(final String[] args) { }
```

**Example**:
```java
public class Names {
    public static void main(String[] args) {
        System.out.println("First name: " + args[0]);
        System.out.println("Last name: " + args[1]);
    }
}
```

To compile and run:
```bash
javac Names.java
java Names John Wayne
```

---

### Packages

Packages group related classes and interfaces. They are analogous to folders in a file system.

- **Syntax**: Use `package` to define the package at the top of a file.
  ```java
  package com.example.app;
  public class MyClass { }
  ```
- **Importing Packages**: Use `import` to access classes from other packages.
  ```java
  import java.util.Random;
  Random rand = new Random();
  ```
- **Wildcard Imports**: Use `*` to import all classes in a package.
  ```java
  import java.util.*;
  ```

---

## Objects

### Creating Objects
Objects are instances of classes created using the `new` keyword. When an object is created, its constructor is invoked.

**Example**:
```java
public class Student {
    public Student() {
        System.out.println("New student created.");
    }
}

public class MyApp {
    public static void main(String[] args) {
        Student s = new Student();
    }
}
```
Output:
```
New student created.
```

---

## Data Types

### Primitive Types

| Keyword   | Type                 | Min Value            | Max Value           | Default | Example   |
|-----------|----------------------|----------------------|---------------------|---------|-----------|
| `boolean` | true/false           | -                    | -                   | `false` | `true`    |
| `byte`    | 8-bit integral value | `-128`               | `127`               | `0`     | `118`     |
| `short`   | 16-bit integral value| `-32,768`            | `32,767`            | `0`     | `-202`    |
| `int`     | 32-bit integral value| `-2,147,483,648`     | `2,147,483,647`     | `0`     | `5106`    |
| `long`    | 64-bit integral value| `-2^63`              | `2^63 - 1`          | `0L`    | `5106L`   |
| `float`   | 32-bit floating point| -                    | -                   | `0.0f`  | `511.18f` |
| `double`  | 64-bit floating point| -                    | -                   | `0.0`   | `511.18`  |
| `char`    | 16-bit Unicode value | `0`                  | `65,535`            | `\u0000`| `'c'`     |

#### Notes on Primitive Types:
- `boolean` values are not related to `1` and `0`.
- Numeric types are signed and can represent negative values.
- `float` and `long` require suffixes (`f`/`L`).

---

### Wrapper Classes

Wrapper classes allow primitive types to be treated as objects. For example:
```java
Integer intObject = Integer.valueOf(5);
```

| Primitive Type | Wrapper Class | Example                     |
|----------------|--------------|-----------------------------|
| `boolean`      | `Boolean`    | `Boolean.valueOf(true);`    |
| `byte`         | `Byte`       | `Byte.valueOf((byte) 12);`  |
| `short`        | `Short`      | `Short.valueOf((short) 12);`|
| `int`          | `Integer`    | `Integer.valueOf(12);`      |
| `long`         | `Long`       | `Long.valueOf(12L);`        |
| `float`        | `Float`      | `Float.valueOf(12.0f);`     |
| `double`       | `Double`     | `Double.valueOf(12.0);`     |
| `char`         | `Character`  | `Character.valueOf('c');`   |

Wrapper classes provide additional methods for type conversion and parsing.

---

### Strings

Strings are sequences of characters and are immutable in Java.

**Examples of String Operations:**

1. **Concatenation**:
   ```java
   String fullName = "John" + " Wayne";
   ```

2. **Methods**:
    - `length()`: Returns the length of the string.
    - `charAt(index)`: Returns the character at a specific index.
    - `toUpperCase()` and `toLowerCase()`.
   ```java
   String name = "John Wayne";
   System.out.println(name.length());
   System.out.println(name.toUpperCase());
   ```

**String Pool:**
The JVM optimizes memory by storing string literals in a common pool. Identical literals reference the same memory location.

---

## Dates and Times

Java provides several classes for handling dates and times in the `java.time` package.

1. **Classes**:
    - `LocalDate`: Represents a date without time.
    - `LocalTime`: Represents a time without a date.
    - `LocalDateTime`: Combines date and time.
    - `ZonedDateTime`: Includes time-zone information.

**Example**:
```java
LocalDate date = LocalDate.of(2022, Month.APRIL, 15);
LocalTime time = LocalTime.of(12, 30);
LocalDateTime dateTime = LocalDateTime.of(date, time);
```

2. **Methods**:
    - `plusDays()` and `minusDays()` for date arithmetic.
    - `isBefore()` and `isAfter()` for comparisons.

**Periods and Durations**:
- **Periods**: Work with dates.
- **Durations**: Work with times.

```java
LocalDate date = LocalDate.of(2022, 11, 15);
Period period = Period.of(1, 2, 10);
date = date.plus(period);
System.out.println(date);
```

---

# Chapter 1: Handling Date, Time, Text, Numeric, and Boolean Values

This document contains questions and answers from **Chapter 1** of the OCP Oracle Certified Professional Java SE 17 Developer Practice Tests. Each question is followed by the available options, with the correct option and explanation provided.

---

### 1. How many of the Duration, LocalDateTime, and LocalTime classes have the concept of a time zone?
- A. None
- B. One
- C. Two
- D. Three

**Answer**: **A. None**  
Explanation: These classes do not include a time zone concept.

---

### 2. How many lines does this print?
```java
System.out.print("""
   "ape"
   "baboon"
   "gorilla"
   """);
```
- A. Three
- B. Four
- C. Five
- D. The code does not compile.

**Answer**: **B. Four**  
Explanation: A blank line is printed after the text block because the closing triple quotes are on a new line.

---

### 3. Which of the following are not valid variable names? (Choose two.)
- A. `_`
- B. `_blue`
- C. `2blue`
- D. `blue$`
- E. `Blue`

**Answer**: **A. `_` and C. `2blue`**  
Explanation: Variable names cannot be a single underscore (`_`) or start with a digit.

---

### 4. Which class has a `getSeconds()` method?
- A. Only the Duration class
- B. Only the Period class
- C. Both the Duration and Period classes
- D. Neither class

**Answer**: **A. Only the Duration class**  
Explanation: `Duration` is measured in seconds, while `Period` is measured in larger units like days, months, and years.

---

### 5. What does the following code output?
```java
var localDate = LocalDate.of(2022, 3, 13);
var localTime = LocalTime.of(1, 0);
var zone = ZoneId.of("America/New_York");
var z = ZonedDateTime.of(localDate, localTime, zone);

var offset = z.getOffset();
var duration = Duration.ofHours(3);
var later = z.plus(duration);

System.out.println(later.getHour() + " " + offset.equals(later.getOffset()));
```
- A. 4 false
- B. 4 true
- C. 5 false
- D. 5 true

**Answer**: **C. 5 false**  
Explanation: The clock skips 2 a.m. due to daylight saving time, so adding three hours results in 5 a.m., and the offset changes.

---

### 6. What is the value of `tip` after executing the following code snippet?
```java
int meal = 5;
int tip = 2;
var total = meal + (meal > 6 ? tip++ : tip--);
```
- A. 1
- B. 2
- C. 3
- D. 7
- E. None of the above

**Answer**: **A. 1**  
Explanation: The ternary expression evaluates the second branch, decrementing `tip` from 2 to 1.

---

### 7. What does the following output?
```java
int year = 1874;
int month = Month.MARCH;
int day = 24;
LocalDate date = LocalDate.of(year, month, day);
System.out.println(date.isBefore(LocalDate.now()));
```
- A. false
- B. true
- C. The code does not compile.
- D. The code compiles but throws an exception at runtime.

**Answer**: **C. The code does not compile.**  
Explanation: `Month.MARCH` is an enum and cannot be assigned to an `int` variable.

---

### 8. What is the output of the following?
```java
var b = "12";
b += "3";
b.reverse();
System.out.println(b.toString());
```
- A. 12
- B. 21
- C. 123
- D. 321
- E. The code does not compile.

**Answer**: **E. The code does not compile.**  
Explanation: The `String` class does not have a `reverse()` method; it exists in `StringBuilder`.

---

### 9. What is the output of the following?
```java
var line = new StringBuilder("-");
var anotherLine = line.append("-");
System.out.print(line == anotherLine);
System.out.print(" ");
System.out.print(line.length());
```
- A. false 1
- B. false 2
- C. true 1
- D. true 2
- E. It does not compile.

**Answer**: **D. true 2**  
Explanation: `StringBuilder` is mutable, so `line` and `anotherLine` refer to the same object.

---

### 10. Which of the following can fill in the blank so the code doesn't throw an exception?
```java
var localDate = LocalDate.of(2022, 3, 13);
var localTime = LocalTime.of(____________);
var zone = ZoneId.of("America/New_York");
var z = ZonedDateTime.of(localDate, localTime, zone);
```
- A. 2, 0
- B. 3, 0
- C. Either of the above will run without throwing an exception.
- D. Both of these will cause an exception to be thrown.

**Answer**: **C. Either of the above will run without throwing an exception.**  
Explanation: Java adjusts the time to handle daylight saving time transitions.

---

### 11. Which statement is true of this text block?
```java
var block = """
                                      green
                                        yellow
                                      """;
```
- A. There is only essential whitespace.
- B. There is only incidental whitespace.
- C. There is both essential and incidental whitespace.
- D. The code does not compile.

**Answer**: **C. There is both essential and incidental whitespace.**  
Explanation: The spaces before `"green"` and `"yellow"` are essential for formatting, while the spaces before the closing triple quotes are incidental.

---

### 12. What are the return types of `cat`, `moose`, and `penguin`, respectively?
```java
var cat = Math.ceil(65);
var moose = Math.max(7, 8);
var penguin = Math.pow(2, 3);
```
- A. double, double, double
- B. double, int, double
- C. double, int, int
- D. int, double, double
- E. int, int, double
- F. int, int, int

**Answer**: **B. double, int, double**  
Explanation: `Math.ceil()` and `Math.pow()` return `double`, while `Math.max()` returns the type of its arguments (`int` in this case).

---

Let me know if you'd like the remaining questions or need clarifications!

### 13. What is the result of the following?
```java
var waffleDay = LocalDate.of(2022, Month.MARCH, 25);
var period = Period.ofYears(1).ofMonths(6).ofDays(3);
var later = waffleDay.plus(period);
later.plusDays(1);
var thisOne = LocalDate.of(2023, Month.SEPTEMBER, 28);
var thatOne = LocalDate.of(2023, Month.SEPTEMBER, 29);
System.out.println(later.isBefore(thisOne) + " " + later.isBefore(thatOne));
```
- A. false false
- B. false true
- C. true true
- D. true false
- E. The code does not compile.

**Answer**: **B. false true**  
Explanation: `later` represents September 28, 2023. It is not before `thisOne` (equal dates are not before), but it is before `thatOne`.

---

### 14. Which operators work with one or more boolean types? (Choose three.)
- A. `^`
- B. `~`
- C. `&`
- D. `+`
- E. `||`
- F. `@`

**Answer**: **A. ^, C. &, E. ||**  
Explanation: These operators are valid for boolean types, while others are not.

---

### 15. What is a possible result of the following?
```java
var montyPythonDay = LocalDate.of(2023, Month.MAY, 10);
var aprilFools = LocalDate.of(2023, Month.APRIL, 1);
var duration = Duration.ofDays(1);
var result = montyPythonDay.minus(duration);
System.out.println(result + " " + aprilFools.isBefore(result));
```
- A. 2023-05-09 false
- B. 2023-05-09 true
- C. The code does not compile.
- D. None of the above.

**Answer**: **B. 2023-05-09 true**  
Explanation: Subtracting one day results in May 9, 2023. April 1 is before May 9, so the second part prints `true`.

---

### 16. How many of these lines compile?
```java
bool b = null;
Bool bl = null;
int i = null;
Integer in = null;
String s = null;
```
- A. None
- B. One
- C. Two
- D. Three
- E. Four
- F. Five

**Answer**: **C. Two**  
Explanation: `bool` and `Bool` are invalid types, and `int` cannot hold `null`. Only `Integer in` and `String s` compile.

---

### 17. Which of these can replace `isEmpty()` and `trim()` to produce the same output? (Choose two.)
```java
String curious = "george likes bananas ";
System.out.println(curious.isEmpty());
System.out.println(curious.trim());
```
- A. `empty()`
- B. `isBlank()`
- C. `isMissing()`
- D. `removeBlanks()`
- E. `shorten()`
- F. `strip()`

**Answer**: **B. `isBlank()` and F. `strip()`**  
Explanation: `isBlank()` checks for whitespace, and `strip()` removes leading and trailing whitespace, similar to `trim()`.

---

### 18. How many lines does this print?
```java
System.out.print("""
   "ape"
   "baboon"
   "gorilla"
   """);
```
- A. Three
- B. Four
- C. Five
- D. The code does not compile.

**Answer**: **B. Four**  
Explanation: The blank line after the text block is due to the closing triple quotes on a new line.

---

### 19. What is a possible value of the `ZonedDateTime` obtained by adding an hour?
The original `ZonedDateTime` is:  
`2012-11-06T01:00-04:00[America/New_York]`
- A. 2022-11-06T01:00-04:00[America/New_York]
- B. 2022-11-06T02:00-04:00[America/New_York]
- C. 2022-11-06T01:00-05:00[America/New_York]
- D. 2022-11-06T02:00-05:00[America/New_York]

**Answer**: **C. 2022-11-06T01:00-05:00[America/New_York]**  
Explanation: The time zone offset changes when the hour is repeated due to daylight saving time ending.

---

### 20. How many of these lines compile?
```java
35: Boolean.valueOf("8").booleanValue();
36: Character.valueOf('x').byteValue();
37: Double.valueOf("9_.3").byteValue();
38: Long.valueOf(88).byteValue();
```
- A. None
- B. One
- C. Two
- D. Three
- E. Four

**Answer**: **D. Three**  
Explanation: Line 36 does not compile because `Character` is not a numeric type. Lines 35, 37, and 38 compile successfully (though 37 throws an exception at runtime).

---

### 21. What is the output of the following?
```java
var date1 = LocalDate.of(2022, Month.JULY, 17);
var time = LocalTime.of(10, 0);
var zone = ZoneId.of("America/New_York");
var iceCreamDay = ZonedDateTime.of(date1, time, zone);
date1 = date1.plusMonths(1);
System.out.println(iceCreamDay.getMonthValue());
```
- A. 6
- B. 7
- C. 8
- D. The code does not compile.
- E. An exception is thrown at runtime.

**Answer**: **B. 7**  
Explanation: `iceCreamDay` remains in July (`7`) as it is immutable. Adding a month to `date1` does not affect `iceCreamDay`.

---
Here are questions 22 to 35 with their answers formatted for your README:

---

### 22. What is the output of the following code?
```java
var sum = 0.0;
sum = sum + Math.min(3, 5);
sum = sum + Math.floor(1.8);
sum = sum + Math.round(5.6);

System.out.println(sum);
```
- A. 9
- B. 9.0
- C. 10
- D. 10.0
- E. 11
- F. 11.0
- G. None of the above

**Answer**: **D. 10.0**  
Explanation: `Math.min(3, 5)` returns `3`, `Math.floor(1.8)` returns `1.0`, and `Math.round(5.6)` returns `6`. Adding them results in `10.0`.

---

### 23. What is the output of the following?
```java
var line = new String("-");
line.concat("-");
System.out.print(line.length());
```
- A. 1
- B. 2
- C. The code compiles but outputs something else.
- D. The code does not compile.

**Answer**: **A. 1**  
Explanation: Strings are immutable. `concat()` creates a new string but does not modify `line`. The original `line` remains unchanged with a length of `1`.

---

### 24. Which of the following is not a valid wrapper class?
- A. `Boolean`
- B. `Char`
- C. `Double`
- D. `Integer`
- E. `Long`
- F. All of these are valid wrapper classes.

**Answer**: **B. Char**  
Explanation: The correct wrapper class for `char` is `Character`, not `Char`.

---

### 25. How many pairs of parentheses can be removed and still have the code print `6`?
```java
System.out.println((((1+1))*((1+2))));
```
- A. None
- B. One pair
- C. Two pairs
- D. Three pairs
- E. Four pairs
- F. Five pairs

**Answer**: **D. Three pairs**  
Explanation: Parentheses around `(1+1)` and `(1+2)` must remain to maintain precedence. The rest are unnecessary, resulting in `(1+1)*(1+2)`.

---

### 26. What is the output of the following class?
```java
package rocket;
public class Countdown {
    public static void main(String[] fuel) {
        var builder = new StringBuilder("54321");
        builder.substring(2);
        System.out.println(builder.charAt(1));
    }
}
```
- A. 1
- B. 2
- C. 3
- D. 4
- E. 5
- F. Does not compile

**Answer**: **B. 2**  
Explanation: `substring()` does not modify the original `StringBuilder`. The second character (index 1) of `"54321"` is `2`.

---

### 27. What is the output of the following?
```java
var baa = 8;
var bleat = ~baa;
var sheep = ~bleat;
System.out.printf(bleat + " " + sheep);
```
- A. -8 8
- B. -8 9
- C. -9 8
- D. -9 9
- E. None of the above

**Answer**: **C. -9 8**  
Explanation: The bitwise complement operator `~` inverts the bits. For `baa = 8`, `bleat = -9`, and applying `~` to `bleat` gives `sheep = 8`.

---

### 28. How many of these lines contain a compiler error?
```java
double num1 = 2.718;
double num2 = 2._718;
double num3 = 2.7_1_8;
double num4 = _2.718;
```
- A. 0
- B. 1
- C. 2
- D. 3
- E. 4

**Answer**: **C. 2**  
Explanation: `num2` has an underscore adjacent to the decimal point, and `num4` starts with an underscore, both of which are invalid.

---

### 29. Which contains a constant named `HOURS`?
- A. `ChronoUnit`
- B. `Duration`
- C. `Instant`
- D. `Period`
- E. None of the above

**Answer**: **A. ChronoUnit**  
Explanation: The `ChronoUnit` enum includes constants for various time units, including `HOURS`.

---

### 30. Which methods, when combined, match the functionality of the `strip()` method? (Choose two.)
- A. `stripAfter()`
- B. `stripBefore()`
- C. `stripEnding()`
- D. `stripIndent()`
- E. `stripLeaders()`
- F. `stripTrailing()`

**Answer**: **D. stripIndent() and F. stripTrailing()**  
Explanation: These two methods replicate the behavior of `strip()` for removing unwanted whitespace.

---

### 31. What is the output of the following application?
```java
public class Airplane {
   static int start = 2;
   final int end;
   public Airplane(int x) {
      x = 4;
      end = x;
   }
   public void fly(int distance) {
      System.out.print(end - start + " ");
      System.out.print(distance);
   }
   public static void main(String... start) {
      new Airplane(10).fly(5);
   }
}
```
- A. `2 5`
- B. `8 5`
- C. `6 5`
- D. The code does not compile.
- E. None of the above

**Answer**: **A. 2 5**  
Explanation: The `end` variable is initialized to `4`, and `start` is `2`. Subtracting `start` from `end` results in `2`, and `distance` is printed as `5`.

---

### 32. What is the output of the following?
```java
var sb = new StringBuilder("radical")
   .insert(sb.length(), "robots");
System.out.println(sb);
```
- A. `radicarobots`
- B. `radicalrobots`
- C. `radical robots`
- D. The code does not compile.
- E. The code compiles but throws an exception at runtime.

**Answer**: **D. The code does not compile.**  
Explanation: The variable `sb` is used before it is declared in the chained call, causing a compilation error.

---

### 33. How many lines compile?
```java
bool b = null;
Bool bl = null;
int i = null;
Integer in = null;
String s = null;
```
- A. None
- B. One
- C. Two
- D. Three
- E. Four

**Answer**: **C. Two**  
Explanation: `bool` and `Bool` are invalid types, and `int` cannot hold `null`. Only `Integer in` and `String s` compile.

---

### 34. How many pairs of parentheses can be removed without changing the value of the text block?
```java
var quotes = """
   \"The Quotes that Could\"
   \"\"\"
   """;
```
- A. Zero
- B. One
- C. Two
- D. Three
- E. Four
- F. The code does not compile.

**Answer**: **E. Four**  
Explanation: Four backslashes can be removed without altering the value: two from the first line and two from the second line while keeping the triple quotes valid.

---

### 35. What is the output of the following code?
```java
var date1 = LocalDate.of(2022, Month.JULY, 17);
var time = LocalTime.of(10, 0);
var zone = ZoneId.of("America/New_York");
var iceCreamDay = ZonedDateTime.of(date1, time, zone);
date1 = date1.plusMonths(1);
System.out.println(iceCreamDay.getMonthValue());
```
- A. 6
- B. 7
- C. 8
- D. The code does not compile.
- E. An exception is thrown at runtime.

**Answer**: **B. 7**  
Explanation: `iceCreamDay` remains in July (`7`) as it is immutable. Adding a month to `date1` does not affect `iceCreamDay`.

---

### 36. How many of these lines compile?
```java
35: Boolean.valueOf("8").booleanValue();
36: Character.valueOf('x').byteValue();
37: Double.valueOf("9_.3").byteValue();
38: Long.valueOf(88).byteValue();
```
- A. None
- B. One
- C. Two
- D. Three
- E. Four

**Answer**: **D. Three**  
Explanation: Line 36 does not compile because `Character` does not have a `byteValue()` method. Lines 35, 37, and 38 compile successfully (though 37 throws an exception at runtime).

---

### 37. What is the output of the following application?
```java
public class Rematerialize {
   public static void main(String[] input) {
      int init = 11;
      int split = 3;
      int partA = init / split;
      int partB = init % split;
      int result = split * (partB + partA);
      System.out.print(result);
   }
}
```
- A. 9
- B. 11
- C. 12
- D. 15
- E. The code does not compile.
- F. None of the above

**Answer**: **D. 15**  
Explanation: `partA = 3`, `partB = 2`. The calculation becomes `3 * (2 + 3)`, resulting in `15`.

---

### 38. What is a possible result of the following?
```java
var montyPythonDay = LocalDate.of(2022, Month.MAY, 13);
var time = LocalTime.of(10, 0);
var dateTime = LocalDateTime.of(montyPythonDay, time);
var duration = Duration.ofDays(1);
var result = dateTime.minus(duration);
System.out.println(result);
```
- A. `2022-05-12T10:00`
- B. `2022-05-13T10:00`
- C. The code does not compile.
- D. None of the above.

**Answer**: **A. 2022-05-12T10:00**  
Explanation: Subtracting one day from May 13, 2022, results in May 12, 2022, at the same time of `10:00`.

---

### 39. Which of the following can replace `isEmpty()` and `trim()` to produce the same output? (Choose two.)
```java
String curious = "george likes bananas ";
System.out.println(curious.isEmpty());
System.out.println(curious.trim());
```
- A. `empty()`
- B. `isBlank()`
- C. `isMissing()`
- D. `removeBlanks()`
- E. `shorten()`
- F. `strip()`

**Answer**: **B. `isBlank()` and F. `strip()`**  
Explanation: `isBlank()` checks for whitespace, and `strip()` removes leading and trailing whitespace, similar to `trim()`.

---

### 40. What is the output of the following?
```java
var sb = new StringBuilder();
sb.append("red");
sb.deleteCharAt(0);
sb.delete(1, 2);
System.out.println(sb);
```
- A. `e`
- B. `ed`
- C. `d`
- D. None of the above

**Answer**: **A. e**  
Explanation: `"red"` becomes `"ed"` after removing the first character, and removing index `1` leaves `"e"`.

---

### 41. What is the output of the following?
```java
var date1 = LocalDate.of(2022, Month.MARCH, 3);
var date2 = LocalDate.of(2022, Month.FEBRUARY, 31);
System.out.println(date1.equals(date2));
```
- A. false
- B. true
- C. The code does not compile.
- D. The code compiles but throws an exception at runtime.

**Answer**: **D. The code compiles but throws an exception at runtime.**  
Explanation: `LocalDate.of(2022, Month.FEBRUARY, 31)` is invalid because February does not have 31 days. This throws a `DateTimeException`.

---

### 42. What is the output of the following class?
```java
package rocket;
public class Countdown {
    public static void main(String[] fuel) {
        var builder = new StringBuilder("54321");
        builder.substring(2);
        System.out.println(builder.charAt(1));
    }
}
```
- A. 1
- B. 2
- C. 3
- D. 4
- E. 5
- F. Does not compile

**Answer**: **B. 2**  
Explanation: `substring()` does not modify the original `StringBuilder`; it returns a new `String`. The second character (index 1) of `"54321"` is `2`.

---

### 43. What is the output of the following?
```java
var baa = 8;
var bleat = ~baa;
var sheep = ~bleat;
System.out.printf(bleat + " " + sheep);
```
- A. -8 8
- B. -8 9
- C. -9 8
- D. -9 9
- E. None of the above

**Answer**: **C. -9 8**  
Explanation: The bitwise complement operator `~` inverts all bits. For `baa = 8`, `bleat = -9`. Applying `~` again to `bleat` gives `sheep = 8`.

---

### 44. How many of these lines contain a compiler error?
```java
double num1 = 2.718;
double num2 = 2._718;
double num3 = 2.7_1_8;
double num4 = _2.718;
```
- A. 0
- B. 1
- C. 2
- D. 3
- E. 4

**Answer**: **C. 2**  
Explanation: `num2` has an underscore adjacent to the decimal, and `num4` starts with an underscore, both of which are invalid.

---

### 45. What is the output of the following?
```java
var waffleDay = LocalDate.of(2022, Month.MARCH, 25);
var period = Period.ofYears(1).ofMonths(6).ofDays(3);
var later = waffleDay.plus(period);
System.out.println(later);
```
- A. 2023-09-28
- B. 2023-03-28
- C. 2022-09-28
- D. The code does not compile.

**Answer**: **A. 2023-09-28**  
Explanation: `Period.ofYears(1).ofMonths(6).ofDays(3)` creates a period of 1 year, 6 months, and 3 days. Adding this to March 25, 2022, results in September 28, 2023.

---

### 46. What is the output of the following?
```java
var block = """
   ant  antelope \s \n
   cat "kitten" \
   seal sea lion
   """;
System.out.print(block);
```
- A. It contains two quotes.
- B. It contains eight quotes.
- C. It is three lines.
- D. One line is blank.
- E. Two lines are blank.
- F. The first line contains trailing whitespace.
- G. The first line does not contain trailing whitespace.

**Answer**: **A. It contains two quotes, C. It is three lines, F. The first line contains trailing whitespace.**  
Explanation: The `\s` in the first line adds trailing whitespace. The block contains three lines and two quotes around `"kitten"`.

---

### 47. Which of the following local variable declarations does not compile?
- A. `double num1, int num2 = 0;`
- B. `int num1, num2;`
- C. `int num1, num2 = 0;`
- D. `int num1 = 0, num2 = 0;`
- E. All of the above
- F. None of the above

**Answer**: **A. double num1, int num2 = 0;**  
Explanation: Java does not allow mixing variable types in a single declaration.

---

### 48. What is the output of the following code snippet?
```java
var sb = new StringBuilder("radical")
   .insert(sb.length(), "robots");
System.out.println(sb);
```
- A. `radicarobots`
- B. `radicalrobots`
- C. `radical robots`
- D. The code does not compile.
- E. The code compiles but throws an exception at runtime.

**Answer**: **D. The code does not compile.**  
Explanation: The variable `sb` is used before it is declared, causing a compilation error.

---

### 49. What is the result of the following?
```java
var teams = new String("694");
teams.concat(" 1155");
teams.concat(" 2265");
teams.concat(" 2869");
System.out.println(teams);
```
- A. 694
- B. 694 1155
- C. 694 1155 2265 2869
- D. The code compiles but outputs something else.
- E. The code does not compile.

**Answer**: **A. 694**  
Explanation: `String` is immutable, so `concat()` does not change the value of `teams`.

---

### 50. What is the result of the following?
```java
var sb = new StringBuilder();
sb.append("red");
sb.deleteCharAt(0);
sb.delete(1, 2);
System.out.println(sb);
```
- A. `ed`
- B. `e`
- C. `d`
- D. None of the above

**Answer**: **B. e**  
Explanation: `"red"` becomes `"ed"` after removing the first character, and removing index `1` leaves `"e"`.

---

Here’s the continuation:

---

### 51. What is the output of the following code?
```java
var numPigeons = Long.valueOf("100");
System.out.println(numPigeons.toString());
```
- A. The code does not compile.
- B. The code throws an exception.
- C. The output is `100`.
- D. None of the above.

**Answer**: **C. The output is 100.**  
Explanation: `Long.valueOf("100")` parses the string into a `Long` object, and `toString()` converts it back to the string representation.

---

### 52. What is the result of the following code?
```java
var waffleDay = LocalDate.of(2022, Month.MARCH, 25);
var period = Period.ofYears(1).ofMonths(6).ofDays(3);
var later = waffleDay.plus(period);
later.plusDays(1);
var thisOne = LocalDate.of(2022, Month.SEPTEMBER, 28);
var thatOne = LocalDate.of(2022, Month.SEPTEMBER, 29);
System.out.println(later.isBefore(thisOne) + " " + later.isBefore(thatOne));
```
- A. false false
- B. false true
- C. true true
- D. true false
- E. The code does not compile.

**Answer**: **B. false true**  
Explanation: The `Period` sets `later` to September 28, 2023. The first comparison is false (equal dates are not "before"), and the second comparison is true.

---

### 53. Which statement is true of this text block?
```java
var block = """
   green
   yellow
   """;
```
- A. There is only essential whitespace.
- B. There is only incidental whitespace.
- C. There is both essential and incidental whitespace.
- D. The code does not compile.

**Answer**: **C. There is both essential and incidental whitespace.**  
Explanation: The indentation before `"green"` and `"yellow"` is essential, while any leading whitespace in the closing triple quotes is incidental.

---

### 54. What is the output of the following code?
```java
var date1 = LocalDate.of(2022, Month.MARCH, 3);
var date2 = date1.plusDays(2).minusDays(1).minusDays(1);
System.out.println(date1.equals(date2));
```
- A. false
- B. true
- C. The code does not compile.
- D. The code compiles but throws an exception at runtime.

**Answer**: **B. true**  
Explanation: The operations cancel out, resulting in `date1` being equal to `date2`.

---

### 55. What is the output of the following application?
```java
public class Legos {
    public static void main(String[] duplo) {
        var sb = new StringBuilder();
        sb.append("red");
        sb.deleteCharAt(0);
        sb.delete(1, 2);
        System.out.println(sb);
    }
}
```
- A. `e`
- B. `ed`
- C. `d`
- D. None of the above

**Answer**: **A. e**  
Explanation: `"red"` becomes `"ed"` after removing the first character, and removing index `1` leaves `"e"`.

---

### 56. Which operators work with one or more boolean types? (Choose three.)
- A. `^`
- B. `~`
- C. `&`
- D. `+`
- E. `||`
- F. `@`

**Answer**: **A. ^, C. &, E. ||**  
Explanation: These operators are valid for boolean types, while others are not.

---

### 57. What is the result of the following?
```java
var waffleDay = LocalDate.of(2022, Month.MARCH, 25);
var period = Period.ofYears(1).ofMonths(6).ofDays(3);
var later = waffleDay.plus(period);
later.plusDays(1);
var thisOne = LocalDate.of(2022, Month.SEPTEMBER, 28);
var thatOne = LocalDate.of(2022, Month.SEPTEMBER, 29);
System.out.println(later.isBefore(thisOne) + " " + later.isBefore(thatOne));
```
- A. false false
- B. false true
- C. true true
- D. true false
- E. The code does not compile.

**Answer**: **B. false true**  
Explanation: `later` represents September 28, 2023. It is not before `thisOne` (equal dates are not before), but it is before `thatOne`.

---

### 58. What is the output of the following?
```java
var baa = 8;
var bleat = ~baa;
var sheep = ~bleat;
System.out.printf(bleat + " " + sheep);
```
- A. -8 8
- B. -8 9
- C. -9 8
- D. -9 9
- E. None of the above

**Answer**: **C. -9 8**  
Explanation: The bitwise complement operator `~` inverts the bits. For `baa = 8`, `bleat = -9`, and applying `~` to `bleat` gives `sheep = 8`.

---

### 59. What is the output of the following code snippet?
```java
var sb = new StringBuilder("radical")
   .insert(sb.length(), "robots");
System.out.println(sb);
```
- A. `radicarobots`
- B. `radicalrobots`
- C. `radical robots`
- D. The code does not compile.
- E. The code compiles but throws an exception at runtime.

**Answer**: **D. The code does not compile.**  
Explanation: The variable `sb` is used before it is declared in the chained call, causing a compilation error.

---

### 60. How many lines compile?
```java
bool b = null;
Bool bl = null;
int i = null;
Integer in = null;
String s = null;
```
- A. None
- B. One
- C. Two
- D. Three
- E. Four

**Answer**: **C. Two**  
Explanation: `bool` and `Bool` are invalid types, and `int` cannot hold `null`. Only `Integer in` and `String s` compile.

---
Here’s the continuation:

---

### 61. What is the output of the following application?
```java
public class Airplane {
    static int start = 2;
    final int end;
    public Airplane(int x) {
        x = 4;
        end = x;
    }
    public void fly(int distance) {
        System.out.print(end - start + " ");
        System.out.print(distance);
    }
    public static void main(String... start) {
        new Airplane(10).fly(5);
    }
}
```
- A. `2 5`
- B. `8 5`
- C. `6 5`
- D. The code does not compile.
- E. None of the above

**Answer**: **A. 2 5**  
Explanation: The `end` variable is initialized to `4`, and `start` is `2`. Subtracting `start` from `end` results in `2`, and `distance` is printed as `5`.

---

### 62. How many pairs of parentheses can be removed and still have the code print `6`?
```java
System.out.println((((1+1))*((1+2))));
```
- A. None
- B. One pair
- C. Two pairs
- D. Three pairs
- E. Four pairs
- F. Five pairs

**Answer**: **D. Three pairs**  
Explanation: Parentheses around `(1+1)` and `(1+2)` must remain to maintain precedence. The rest are unnecessary, resulting in `(1+1)*(1+2)`.

---

### 63. What is the output of the following code?
```java
var teams = new String("694");
teams.concat(" 1155");
teams.concat(" 2265");
teams.concat(" 2869");
System.out.println(teams);
```
- A. `694`
- B. `694 1155`
- C. `694 1155 2265 2869`
- D. The code compiles but outputs something else.
- E. The code does not compile.

**Answer**: **A. 694**  
Explanation: Strings are immutable in Java. The `concat()` method creates a new String, but it is not assigned to `teams`. The original value remains `694`.

---

### 64. Which statement is true of this text block?
```java
var block = """
   green
   yellow
   """;
```
- A. There is only essential whitespace.
- B. There is only incidental whitespace.
- C. There is both essential and incidental whitespace.
- D. The code does not compile.

**Answer**: **C. There is both essential and incidental whitespace.**  
Explanation: The indentation before `"green"` and `"yellow"` is essential for formatting, while any leading whitespace in the closing triple quotes is incidental.

---

### 65. How many of these lines compile?
```java
35: Boolean.valueOf("8").booleanValue();
36: Character.valueOf('x').byteValue();
37: Double.valueOf("9_.3").byteValue();
38: Long.valueOf(88).byteValue();
```
- A. None
- B. One
- C. Two
- D. Three
- E. Four

**Answer**: **D. Three**  
Explanation: Line 36 does not compile because `Character` does not have a `byteValue()` method. Lines 35, 37, and 38 compile successfully (though 37 throws an exception at runtime).

---

### 66. What is a possible output of the following?
```java
var montyPythonDay = LocalDate.of(2023, 5, 13);
var time = LocalTime.of(10, 0);
var dateTime = LocalDateTime.of(montyPythonDay, time);
var duration = Duration.ofDays(1);
var result = dateTime.minus(duration);
System.out.println(result);
```
- A. `2023-05-12T10:00`
- B. `2023-05-13T10:00`
- C. The code does not compile.
- D. None of the above.

**Answer**: **A. 2023-05-12T10:00**  
Explanation: Subtracting one day from May 13, 2023, results in May 12, 2023, at the same time of `10:00`.

---

### 67. What is the result of the following code?
```java
var block = """
   green
   yellow
   """;
System.out.println(block);
```
- A. It prints `"green"` followed by `"yellow"` on separate lines.
- B. It prints `"green yellow"` on one line.
- C. It prints `"green"` on one line and `"yellow"` with extra spaces.
- D. It prints `"green yellow"` with extra spaces.

**Answer**: **A. It prints "green" followed by "yellow" on separate lines.**  
Explanation: Each line of the text block is preserved exactly as entered, with no extra spaces added between `"green"` and `"yellow"`.

---

### 68. What is a possible output of this text block?
```java
var textBlock = """
   green
   yellow
   """;
System.out.println(textBlock.stripIndent());
```
- A. `green` on one line and `yellow` indented.
- B. `green` and `yellow` aligned with no indentation.
- C. The code does not compile.
- D. None of the above.

**Answer**: **B. green and yellow aligned with no indentation.**  
Explanation: The `stripIndent()` method removes incidental whitespace to align all text to the left margin.

---

### 69. Which contains a constant named `HOURS`?
- A. `ChronoUnit`
- B. `Duration`
- C. `Instant`
- D. `Period`
- E. None of the above

**Answer**: **A. ChronoUnit**  
Explanation: The `ChronoUnit` enum includes constants for various time units, including `HOURS`.

---

### 70. What is the output of the following?
```java
var date1 = LocalDate.of(2022, Month.JULY, 17);
var time = LocalTime.of(10, 0);
var zone = ZoneId.of("America/New_York");
var iceCreamDay = ZonedDateTime.of(date1, time, zone);
date1 = date1.plusMonths(1);
System.out.println(iceCreamDay.getMonthValue());
```
- A. 6
- B. 7
- C. 8
- D. The code does not compile.
- E. An exception is thrown at runtime.

**Answer**: **B. 7**  
Explanation: `iceCreamDay` remains in July (`7`) as it is immutable. Adding a month to `date1` does not affect `iceCreamDay`.

---