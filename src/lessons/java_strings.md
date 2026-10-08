## Strings in Java

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
