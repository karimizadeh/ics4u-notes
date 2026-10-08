## If Statements in Java

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
| or | `or` | <code>||</code> |
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
