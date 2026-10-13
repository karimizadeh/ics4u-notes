# Methods (Java Functions)

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
