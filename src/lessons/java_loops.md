## Loops in Java

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
1. Keep looping while `i <= 10`.
1. Add 1 to `i` each time.

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
| Or | `or` | <code>||</code> |
| Not | `not` | `!` |
| Function/method | `def greet(name):` | `public static void greet(String name) { }` |
| List/array access | `marks[0]` | `marks[0]` or `marks.get(0)` |
| List length | `len(marks)` | `marks.length` or `marks.size()` |
| Add to list | `names.append("Ali")` | `names.add("Ali");` |
| String length | `len(word)` | `word.length()` |
| String compare | `name == "Ali"` | `name.equals("Ali")` |
