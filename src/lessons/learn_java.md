# Learning Java
Python and Java can solve the same problems, but they look and behave differently.

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

In Java, single-line comments use //.

```java
// This is a single-line comment
System.out.println("Hello");
```

To do a multi-line comment in Java, use the format: `/*` and `*/`.

```java
/*
This program asks the user for their name.
Then it prints a greeting.
This is written across multiple lines.
*/
String name = "Mitchell";
System.out.println("Hello " + name);
```

### Important Java rules:

- Most Java statements end with a semicolon: `;`
- Code blocks are surrounded by curly braces: `{ }`
- The code inside the braces belongs to that block

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

This looks like a lot, so break it down:

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

## Common Java Types

| Python Type | Java Type | Example |
|---|---|---|
| `int` | `int` | `int age = 17;` |
| `float` | `double` | `double price = 9.99;` |
| `str` | `String` | `String name = "Mitchell";` |
| `bool` | `boolean` | `boolean isDone = false;` |
| list | array / `ArrayList` | `int[] nums = {1, 2, 3};` |

Java is case-sensitive, just like Python.

These are different:

```java
age
Age
AGE
```

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
        String name = input.nextLine(); // clears leftover Enter key

        System.out.print("Enter your age: ");
        int age = input.nextInt();

        System.out.println("Hello " + name + ". You are " + age + " years old.");
    }
}
```

Important Scanner methods:

| Data Needed | Java Scanner Method |
|---|---|
| Whole number | `nextInt()` |
| Decimal number | `nextDouble()` |
| One word | `next()` |
| Whole line of text | `nextLine()` |
| Boolean | `nextBoolean()` |

Be careful when mixing `nextInt()` and `nextLine()`. Because `nextInt()` reads the number, but it does not fully clear the Enter key from the input.
```java
int age = input.nextInt();
input.nextLine(); // clears leftover Enter key
String name = input.nextLine();
```

## If Statements

Python:
```python
mark = 75

if mark >= 80:
    print("Excellent")
elif mark >= 50:
    print("Passing")
else:
    print("Not passing")
```

Java:

```java
int mark = 75;

if (mark >= 80) {
    System.out.println("Excellent");
} else if (mark >= 50) {
    System.out.println("Passing");
} else {
    System.out.println("Not passing");
}
```

Key differences:

| Python | Java |
|---|---|
| `if mark >= 80:` | `if (mark >= 80) {` |
| `elif` | `else if` |
| indentation controls block | braces control block |

## Boolean Operators

| Meaning | Python | Java |
|---|---|---|
| and | `and` | `&&` |
| or | `or` | <code>&#124;&#124;</code> |
| not | `not` | `!` |
| equal to | `==` | `==` |
| not equal to | `!=` | `!=` |

Python:
```python
if age >= 13 and age <= 19:
    print("Teenager")
```

Java:
```java
if (age >= 13 && age <= 19) {
    System.out.println("Teenager");
}
```

## Loops

### While Loops

Python:

```python
count = 1

while count <= 5:
    print(count)
    count += 1
```

Java:

```java
int count = 1;

while (count <= 5) {
    System.out.println(count);
    count++;
}
```

`count++` means increase `count` by 1.

It is the same as:

```java
count = count + 1;
```

### For Loops

Python:

```python
for i in range(5):
    print(i)
```

Java:

```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```

A Java `for` loop has three parts:

```java
for (start; condition; update)
```

Example:

```java
for (int i = 1; i <= 10; i++) {
    System.out.println(i);
}
```

This means:

1. Start `i` at 1.
2. Keep looping while `i <= 10`.
3. Add 1 to `i` each time.

## Methods

Methods in Java are similar to functions in Python.

Python:
```python
def greet(name):
    print("Hello " + name)

greet("Mitchell")
```

Java:
```java
public class Main {
    public static void greet(String name) {
        System.out.println("Hello " + name);
    }

    public static void main(String[] args) {
        greet("Mitchell");
    }
}
```

For now, many of our beginner methods will start with:

```java
public static void
```
`void` means the method does not return a value.

Use `int`, `double`, `String`, or `boolean` if the method returns a value.

```java
public static int add(int a, int b)
```

### Methods That Return Values

Python:

```python
def add(a, b):
    return a + b

total = add(3, 4)
```

Java:

```java
public static int add(int a, int b) {
    return a + b;
}

public static void main(String[] args) {
    int total = add(3, 4);
    System.out.println(total);
}
```

The return type comes before the method name:

```java
public static int add(...)
```

This method returns an `int`.

## Arrays

Python lists are flexible:

```python
marks = [80, 90, 75]
marks.append(88)
print(marks[0])
```

Java arrays have a fixed size:

```java
int[] marks = {80, 90, 75};

System.out.println(marks[0]);
```

Array indexes start at 0, just like Python.

```java
marks[0] = 85;
```

To loop through an array:

```java
for (int i = 0; i < marks.length; i++) {
    System.out.println(marks[i]);
}
```

Notice:

```java
marks.length
```

No parentheses.

## ArrayList

An `ArrayList` is closer to a Python list because it can grow and shrink.

```java
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList<String> names = new ArrayList<String>();

        names.add("Mitchell");
        names.add("Dylan");
        names.add("Eric");

        System.out.println(names.get(0));

        names.set(1, "David");

        names.remove(2);

        System.out.println(names.size());
    }
}
```

| Python List | Java ArrayList |
|---|---|
| `names.append("Mitchell")` | `names.add("Mitchell");` |
| `names[0]` | `names.get(0)` |
| `names[1] = "Dylan"` | `names.set(1, "Dylan");` |
| `len(names)` | `names.size()` |
| `names.remove("Mitchell")` | `names.remove("Mitchell");` |

## Strings

Strings in Java use `String` with a capital `S`.

```java
String word = "computer";
```

Common String methods:

| Task | Python | Java |
|---|---|---|
| Length | `len(word)` | `word.length()` |
| Uppercase | `word.upper()` | `word.toUpperCase()` |
| Lowercase | `word.lower()` | `word.toLowerCase()` |
| Character at index | `word[0]` | `word.charAt(0)` |
| Substring | `word[0:4]` | `word.substring(0, 4)` |

Example:

```java
String word = "computer";

System.out.println(word.length());
System.out.println(word.toUpperCase());
System.out.println(word.charAt(0));
System.out.println(word.substring(0, 4));
```

Output:

```text
8
COMPUTER
c
comp
```

### Comparing Strings

This is very important.

Do not compare Strings using `==`.

Wrong:

```java
if (name == "Mitchell") {
    System.out.println("Hi Mitchell");
}
```

Correct:

```java
if (name.equals("Mitchell")) {
    System.out.println("Hi Mitchell");
}
```

For case-insensitive comparison:

```java
if (name.equalsIgnoreCase("Mitchell")) {
    System.out.println("Hi Mitchell");
}
```

In Python:

```python
if name == "Mitchell":
    print("Hi Mitchell")
```

In Java:

```java
if (name.equals("Mitchell")) {
    System.out.println("Hi Mitchell");
}
```