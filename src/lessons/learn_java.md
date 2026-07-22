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
| no semicolon after condition | semicolon after statements inside block |

### Common If Statement Mistake

Do not put a semicolon immediately after the condition.

Wrong:

```java
if (mark >= 50); {
    System.out.println("Passing");
}
```

The semicolon ends the `if` statement too early.

Correct:

```java
if (mark >= 50) {
    System.out.println("Passing");
}
```

## Boolean Operators

| Meaning | Python | Java |
|---|---|---|
| and | `and` | `&&` |
| or | `or` | <code>&#124;&#124;</code> |
| not | `not` | `!` |
| equal to | `==` | `==` |
| not equal to | `!=` | `!=` |
| greater than | `>` | `>` |
| less than | `<` | `<` |
| greater than or equal to | `>=` | `>=` |
| less than or equal to | `<=` | `<=` |

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

### Boolean Expressions

A boolean expression evaluates to `true` or `false`.

```java
int age = 17;
boolean isTeenager = age >= 13 && age <= 19;

System.out.println(isTeenager);
```

Output:

```text
true
```

## Switch Statements

A `switch` statement can be useful when checking one variable against several exact values.

```java
String day = "Monday";

switch (day) {
    case "Monday":
        System.out.println("Start of the week");
        break;
    case "Friday":
        System.out.println("Almost the weekend");
        break;
    default:
        System.out.println("Regular day");
        break;
}
```

Use `break` to stop the switch from continuing into the next case.

`if`, `else if`, and `else` are usually enough, but `switch` is useful to recognize.

## Loops

Loops repeat code.

Use a loop when you need to:

- count through numbers
- repeat until input is valid
- process every item in an array or `ArrayList`
- keep asking a question until the user chooses to stop

### While Loops

A `while` loop repeats while a condition is true.

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

Use a `while` loop when you do not know exactly how many times the loop will run.

Example: keep asking until the password is correct.

```java
Scanner input = new Scanner(System.in);
String password = "";

while (!password.equals("java123")) {
    System.out.print("Enter password: ");
    password = input.nextLine();
}

System.out.println("Access granted.");
```

### For Loops

A `for` loop is useful when you know how many times the loop should run.

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

### Counting Backwards

```java
for (int i = 10; i >= 1; i--) {
    System.out.println(i);
}
```

### Counting by 2

```java
for (int i = 0; i <= 20; i += 2) {
    System.out.println(i);
}
```

### Enhanced For Loop

An enhanced `for` loop is used to go through every item in an array or `ArrayList`.

```java
int[] marks = {80, 90, 75};

for (int mark : marks) {
    System.out.println(mark);
}
```

This is similar to Python:

```python
for mark in marks:
    print(mark)
```

Use an enhanced `for` loop when you want to read each value.

Use a regular index-based `for` loop when you need the index.

```java
for (int i = 0; i < marks.length; i++) {
    System.out.println("Index " + i + ": " + marks[i]);
}
```

### Do-While Loops

A `do-while` loop always runs at least once.

```java
Scanner input = new Scanner(System.in);
int choice;

do {
    System.out.println("1. Play");
    System.out.println("2. Quit");
    System.out.print("Choose: ");
    choice = input.nextInt();
} while (choice != 2);
```

This is useful for menus because the menu should appear before the condition is checked.

### Break and Continue

`break` exits a loop immediately.

```java
for (int i = 1; i <= 10; i++) {
    if (i == 5) {
        break;
    }
    System.out.println(i);
}
```

Output:

```text
1
2
3
4
```

`continue` skips the rest of the current loop cycle and moves to the next cycle.

```java
for (int i = 1; i <= 5; i++) {
    if (i == 3) {
        continue;
    }
    System.out.println(i);
}
```

Output:

```text
1
2
4
5
```

### Common Loop Mistakes

Infinite loop:

```java
int count = 1;

while (count <= 5) {
    System.out.println(count);
    // missing count++
}
```

Off-by-one error:

```java
for (int i = 0; i <= marks.length; i++) {
    System.out.println(marks[i]); // error when i equals marks.length
}
```

Correct:

```java
for (int i = 0; i < marks.length; i++) {
    System.out.println(marks[i]);
}
```

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

For now, many of our methods will start with:

```java
public static void
```

`void` means the method does not return a value.

Use `int`, `double`, `String`, or `boolean` if the method returns a value.

```java
public static int add(int a, int b)
```

### Method Structure

```java
public static returnType methodName(parameterType parameterName) {
    // method body
}
```

Example:

```java
public static double calculateTax(double price) {
    return price * 0.13;
}
```

### Parameters and Arguments

A **parameter** is the variable listed in the method definition.

```java
public static void greet(String name) {
    System.out.println("Hello " + name);
}
```

`name` is a parameter.

An **argument** is the actual value passed into the method.

```java
greet("Mitchell");
```

`"Mitchell"` is an argument.

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

### Void Methods vs Return Methods

A `void` method performs an action.

```java
public static void printGreeting(String name) {
    System.out.println("Hello " + name);
}
```

A return method gives a value back.

```java
public static String createGreeting(String name) {
    return "Hello " + name;
}
```

Use the returned value later:

```java
String message = createGreeting("Mitchell");
System.out.println(message);
```

### Common Method Mistakes

Returning the wrong type:

```java
public static int getName() {
    return "Mitchell"; // error: String is not an int
}
```

Forgetting to return a value:

```java
public static int add(int a, int b) {
    int total = a + b;
    // missing return total;
}
```

Correct:

```java
public static int add(int a, int b) {
    int total = a + b;
    return total;
}
```

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

### Creating Arrays

Create an array with values:

```java
int[] marks = {80, 90, 75};
```

Create an empty array with a fixed size:

```java
int[] marks = new int[3];

marks[0] = 80;
marks[1] = 90;
marks[2] = 75;
```

Once an array is created, its size does not change.

### Looping Through an Array

Index-based loop:

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

Enhanced `for` loop:

```java
for (int mark : marks) {
    System.out.println(mark);
}
```

### Finding a Total and Average

```java
int[] marks = {80, 90, 75};
int total = 0;

for (int mark : marks) {
    total += mark;
}

double average = (double) total / marks.length;
System.out.println(average);
```

### Common Array Mistake

Wrong:

```java
System.out.println(marks[3]);
```

If the array has 3 items, the valid indexes are:

```text
0, 1, 2
```

Index `3` is out of range.

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

### Array vs ArrayList

| Feature | Array | ArrayList |
|---|---|---|
| Size | Fixed | Can grow and shrink |
| Syntax for access | `marks[0]` | `marks.get(0)` |
| Length/size | `marks.length` | `marks.size()` |
| Stores primitive types directly | Yes | No, use wrapper types |

`ArrayList` cannot use primitive types like `int` directly.

Wrong:

```java
ArrayList<int> marks = new ArrayList<int>();
```

Correct:

```java
ArrayList<Integer> marks = new ArrayList<Integer>();
```

Other wrapper types:

| Primitive | Wrapper Type |
|---|---|
| `int` | `Integer` |
| `double` | `Double` |
| `boolean` | `Boolean` |
| `char` | `Character` |

### Looping Through an ArrayList

```java
ArrayList<String> names = new ArrayList<String>();
names.add("Mitchell");
names.add("Dylan");
names.add("Eric");

for (int i = 0; i < names.size(); i++) {
    System.out.println(names.get(i));
}
```

Enhanced `for` loop:

```java
for (String name : names) {
    System.out.println(name);
}
```

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
| Contains text | `"a" in word` | `word.contains("a")` |
| Starts with | `word.startswith("com")` | `word.startsWith("com")` |
| Ends with | `word.endswith("er")` | `word.endsWith("er")` |

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

### String Indexes

Java string indexes start at 0.

```java
String word = "computer";

System.out.println(word.charAt(0)); // c
System.out.println(word.charAt(1)); // o
```

The last index is:

```java
word.length() - 1
```

Example:

```java
char lastLetter = word.charAt(word.length() - 1);
System.out.println(lastLetter);
```

Output:

```text
r
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

### Why Not Use `==` for Strings?

`==` checks whether two references point to the same object.

`.equals()` checks whether the text content is the same.

For Java, use this rule:

> When comparing Strings, use `.equals()` or `.equalsIgnoreCase()`.


## Python to Java Quick Reference

| Task | Python | Java |
|---|---|---|
| Print | `print("Hi")` | `System.out.println("Hi");` |
| Variable | `age = 17` | `int age = 17;` |
| String | `name = "Ali"` | `String name = "Ali";` |
| Boolean | `done = True` | `boolean done = true;` |
| If | `if age > 18:` | `if (age > 18) { }` |
| Else if | `elif` | `else if` |
| And | `and` | `&&` |
| Or | `or` | <code>&#124;&#124;</code> |
| Not | `not` | `!` |
| Function/method | `def greet(name):` | `public static void greet(String name) { }` |
| List/array access | `marks[0]` | `marks[0]` or `marks.get(0)` |
| List length | `len(marks)` | `marks.length` or `marks.size()` |
| Add to list | `names.append("Ali")` | `names.add("Ali");` |
| String length | `len(word)` | `word.length()` |
| String compare | `name == "Ali"` | `name.equals("Ali")` |