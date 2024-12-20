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

