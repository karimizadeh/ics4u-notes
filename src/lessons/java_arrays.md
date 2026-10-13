# Arrays in Java

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
