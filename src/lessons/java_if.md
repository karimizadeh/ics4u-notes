# If Statements in Java

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
| condition has no parentheses | C-style if statement, requires parentheses |
| colon and indentation denotes code block | curly braces denote code block |

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
Boolean values in Java are all lower case, as opposed to Python which capitalizes them.

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

The value of the expression in the parentheses after the `switch` keyword are compared against all cases.
Cases are defined after the `case` keyword within a switch statement.
When a matching case is found, all the code underneath the case will begin to run.

Use `break` to stop the switch from continuing into the next case, skipping to the end of the switch statement.
If no `break` is encountered, execution can continue past any subsequent `case` declarations and run those code blocks.

The `default` case is optional and will run when no other case matches.

The general syntax for `if`, `else if`, and `else` are similar enough to Python, but the `switch` statement should be new and useful to recognize.

# Strings in Java

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
