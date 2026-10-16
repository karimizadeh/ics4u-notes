# Intro to Java

Python and Java can solve the same problems, but they look and behave differently.

## How to Install and use Java

[Click the link to learn how to get Java working on your device: ](https://www.geeksforgeeks.org/linux-unix/download-install-java-windows-linux-macos/)

# Learning Java

Python is more flexible and forgiving. Java is more strict and requires more structure.

| Concept | Python | Java |
|---|---|---|
| Typing | Dynamic | Static |
| File structure | Flexible | Class-based |
| Syntax | Indentation-based | Braces `{}` and semicolons `;` |
| Variables | Type is inferred at runtime | Type must be declared |
| Main program | Can start anywhere | Starts in `main` method |
| Comments | `#` | `//` |
| Blocks | Indentation | Curly braces |
| Lists | `list` | arrays or `ArrayList` |
| Functions | `def` | methods |
| Objects | Optional at first | Central to Java |

## Big Idea: Java Is More Structured Than Python

In Python, a small program can begin immediately:

```python
print("Hello")
```

In Java, almost all code must be inside a **class**, and the program usually begins inside the `main` method.

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello");
    }
}
```

This can feel like extra typing at first, but it gives Java a clear structure.

Remember this basic pattern:

```java
public class Main {
    public static void main(String[] args) {
        // your code goes here
    }
}
```

## Comments in Python vs Java

Comments are notes written in code for humans to read. The computer ignores comments when the program runs.

Comments are useful for:

- explaining what a section of code does
- leaving reminders for yourself
- making code easier for others to understand
- temporarily disabling code while testing

### Single-Line Comments

In Python, single-line comments use `#`.

```python
# This is a single-line comment
print("Hello")
```

In Java, single-line comments use `//`.

```java
// This is a single-line comment
System.out.println("Hello");
```

### Multi-Line Comments

In Java, multi-line comments start with `/*` and end with `*/`.

```java
/*
This program asks the user for their name.
Then it prints a greeting.
This is written across multiple lines.
*/
String name = "Mitchell";
System.out.println("Hello " + name);
```

### Commenting Style

A comment should explain **why** something is happening, not just repeat the code.

Weak comment:

```java
// Add 1 to count
count++;
```

Better comment:

```java
// Move to the next student in the list
count++;
```

## Important Java Rules

Java is strict about syntax.

- Most Java statements end with a semicolon: `;`
- Code blocks are surrounded by curly braces: `{ }`
- The code inside the braces belongs to that block
- Java is case-sensitive
- The file name must usually match the public class name

For example, if the file is named `Main.java`, the public class should be:

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello");
    }
}
```

If the class is named `StudentProgram`, the file should usually be named:

```text
StudentProgram.java
```

## Compile-Time Errors vs Run-Time Errors

Java checks many mistakes before the program runs.

A **compile-time error** happens when Java cannot translate the code into a program.

Examples:

```java
System.out.println("Hello") // missing semicolon
```

```java
int age = "seventeen"; // wrong data type
```

A **run-time error** happens while the program is running.

Example:

```java
int[] marks = {80, 90, 75};
System.out.println(marks[5]); // index does not exist
```

Python also has errors, but Java catches many type and syntax mistakes earlier.

## Your First Program

Python:

```python
print("Hello, world!")
```

Java:

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello, world!");
    }
}
```

This looks like a lot, so break it down.

```java
public class Main
```

This creates a class named `Main`. In Java, code lives inside classes.

```java
public static void main(String[] args)
```

This is the starting point of the program. Java looks for this method first.

```java
System.out.println("Hello, world!");
```

This prints to the screen/console.

### `print` vs `println`

`println` prints and then moves to the next line.

```java
System.out.println("Hello");
System.out.println("World");
```

Output:

```text
Hello
World
```

`print` prints but stays on the same line.

```java
System.out.print("Hello ");
System.out.print("World");
```

Output:

```text
Hello World
```

## Variables and Data Types

In Python, you can write:

```python
age = 17
name = "Mitchell"
average = 86.5
is_passing = True
```

Unlike Python, in Java you must declare the type:

```java
int age = 17;
String name = "Mitchell";
double average = 86.5;
boolean isPassing = true;
```

The type tells Java what kind of value the variable is allowed to store.

This is allowed:

```java
int score = 90;
score = 95;
```

This is not allowed:

```java
int score = 90;
score = "excellent"; // error
```

Once `score` is declared as an `int`, it must store whole numbers.

## Common Java Types

| Python Type | Java Type | Example | Notes |
|---|---|---|---|
| `int` | `int` | `int age = 17;` | Whole number |
| `float` | `double` | `double price = 9.99;` | Decimal number |
| `str` | `String` | `String name = "Mitchell";` | Text, capital `S` |
| `bool` | `boolean` | `boolean isDone = false;` | `true` or `false` |
| list | array / `ArrayList` | `int[] nums = {1, 2, 3};` | Stores multiple values |
| none | `null` | `String name = null;` | Means no object/value reference |

Java is case-sensitive, just like Python.

These are different:

```java
age
Age
AGE
```

### Primitive Types vs Reference Types

Java has **primitive types** and **reference types**.

Primitive types store simple values directly.

Examples:

```java
int age = 17;
double average = 86.5;
boolean isPassing = true;
char letter = 'A';
```

Reference types refer to objects.

Examples:

```java
String name = "Mitchell";
int[] marks = {80, 90, 75};
ArrayList<String> names = new ArrayList<String>();
```

The main thing to remember is:

- `int`, `double`, `boolean`, and `char` are primitive types
- `String`, arrays, and `ArrayList` are reference types
- `String` uses a capital `S`

## Java Naming Conventions

Java has common naming styles.

| Item | Convention | Example |
|---|---|---|
| Class names | PascalCase | `StudentRecord` |
| Variables | camelCase | `studentName` |
| Methods | camelCase | `calculateAverage()` |
| Constants | UPPER_CASE | `MAX_SIZE` |

Python usually uses snake case:

```python
student_name
calculate_average()
```

Java usually uses camel case:

```java
studentName
calculateAverage()
```

Constants are values that should not change.

```java
final double TAX_RATE = 0.13;
```

`final` means the value cannot be reassigned.

## Printing Output

Python:

```python
name = "Mitchell"
print("Hello", name)
```

Java:

```java
String name = "Mitchell";
System.out.println("Hello " + name);
```

Java uses `+`, not commas, to join text and variables.

```java
int age = 17;
System.out.println("You are " + age + " years old.");
```

### Joining Text and Numbers

When `+` is used with a `String`, Java joins the values as text.

```java
int x = 5;
int y = 3;

System.out.println(x + y);
System.out.println("Answer: " + x + y);
System.out.println("Answer: " + (x + y));
```

Output:

```text
8
Answer: 53
Answer: 8
```

The second line prints `53` because Java starts joining text from left to right.

Use parentheses when you want math to happen first.

## Math Operators

| Operator | Meaning | Example | Result |
|---|---|---|---|
| `+` | Addition | `5 + 2` | `7` |
| `-` | Subtraction | `5 - 2` | `3` |
| `*` | Multiplication | `5 * 2` | `10` |
| `/` | Division | `5 / 2` | `2` if both are `int` |
| `%` | Modulo/remainder | `5 % 2` | `1` |
| `++` | Increase by 1 | `count++` | Adds 1 |
| `--` | Decrease by 1 | `count--` | Subtracts 1 |

### Integer Division

This is one of the most common mistakes in Java.

```java
System.out.println(5 / 2);
```

Output:

```text
2
```

Because both numbers are integers, Java does integer division.

To get a decimal result, at least one value must be a `double`.

```java
System.out.println(5.0 / 2);
System.out.println(5 / 2.0);
```

Output:

```text
2.5
2.5
```

### Casting

Casting changes a value from one type to another.

```java
int total = 17;
int count = 4;

double average = (double) total / count;
System.out.println(average);
```

Output:

```text
4.25
```

Without `(double)`, Java would do integer division first.

## Input in Java

Python input is simple:

```python
name = input("Enter your name: ")
age = int(input("Enter your age: "))
```

Java uses a `Scanner`.

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.print("Enter your name: ");
        String name = input.nextLine();

        System.out.print("Enter your age: ");
        int age = input.nextInt();

        System.out.println("Hello " + name + ". You are " + age + " years old.");
    }
}
```

Important Scanner methods:

| Data Needed | Java Scanner Method | Example |
|---|---|---|
| Whole number | `nextInt()` | `int age = input.nextInt();` |
| Decimal number | `nextDouble()` | `double price = input.nextDouble();` |
| One word | `next()` | `String word = input.next();` |
| Whole line of text | `nextLine()` | `String sentence = input.nextLine();` |
| Boolean | `nextBoolean()` | `boolean answer = input.nextBoolean();` |

### `next()` vs `nextLine()`

`next()` reads only one word.

```java
String firstName = input.next();
```

If the user types:

```text
Mary Jane
```

`next()` only reads:

```text
Mary
```

`nextLine()` reads the whole line.

```java
String fullName = input.nextLine();
```

### The `nextInt()` and `nextLine()` Problem

Be careful when mixing `nextInt()` and `nextLine()`.

`nextInt()` reads the number, but it does not fully clear the Enter key from the input.

```java
System.out.print("Enter your age: ");
int age = input.nextInt();

System.out.print("Enter your name: ");
String name = input.nextLine(); // may be skipped
```

Fix:

```java
System.out.print("Enter your age: ");
int age = input.nextInt();
input.nextLine(); // clears leftover Enter key

System.out.print("Enter your name: ");
String name = input.nextLine();
```
