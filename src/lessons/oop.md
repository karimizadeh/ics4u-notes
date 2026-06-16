# Object-Oriented Programming in Java

Object-Oriented Programming, or **OOP**, is a programming style where code is organized around **objects**.

An object can store information and perform actions.

For example, in a school system, we might have objects such as:

- `Student`
- `Teacher`
- `Course`
- `Assignment`

Each object can have:

1. **attributes** - Information the object stores.
2. **methods** - Actions the object can perform.

For example, a `Student` object might store:
- name
- grade
- average

and it might have actions such as:
- display information
- update average
- check if passing

## Important OOP Terms

| Term | Meaning |
|---|---|
| Class | A blueprint for objects |
| Object | An instance of a class |
| Instance variable | Data stored inside an object |
| Method | An action an object can perform |
| Constructor | Runs when an object is created |
| `this` | Refers to the current object |
| `private` | Keeps data protected inside the class |
| Getter | Returns a private value |
| Setter | Changes a private value |
| `toString()` | Controls how an object displays as text |

## Classes and Objects

A **class** is a blueprint.

An **object** is something created from that blueprint.

Example:

```java
public class Student {
    private String name;
    private int grade;
    private double average;
}
```

This class describes what information a student object should have.

To create an object from this class:

```java
Student s1 = new Student();
```

However, this version is incomplete because we have not written a constructor yet.

## Instance Variables

Variables inside a class are called **instance variables** or **fields**.

```java
private String name;
private int grade;
private double average;
```

Each object gets its own copy of the instance variables.

For example:

```java
Student s1 = new Student("Mitchell", 12, 86.5);
Student s2 = new Student("William", 11, 74.0);
```

`s1` and `s2` are both `Student` objects, but they store different data.


## Constructors

A **constructor** is a special method that runs when an object is created.

It is used to give the object its starting values.

```java
public class Student {
    private String name;
    private int grade;
    private double average;

    public Student(String name, int grade, double average) {
        this.name = name;
        this.grade = grade;
        this.average = average;
    }
}
```

Now we can create objects like this:

```java
Student s1 = new Student("Mitchell", 12, 86.5);
Student s2 = new Student("William", 11, 74.0);
```

The constructor lets us create a complete object in one line.


## The `this` Keyword

The keyword `this` refers to the current object.

```java
this.name = name;
this.grade = grade;
this.average = average;
```

In this line:

```java
this.name = name;
```

`this.name` means the instance variable that belongs to the object.

`name` means the parameter passed into the constructor.

This is useful when the parameter and instance variable have the same name.


## Methods

A **method** is an action that an object can perform.

```java
public boolean isPassing() {
    return average >= 50;
}
```

This method checks whether the student is passing.

We can call the method using an object:

```java
Student s1 = new Student("Mitchell", 12, 86.5);

System.out.println(s1.isPassing());
```

Output:

```text
true
```

Methods allow objects to do something with their own data.

## Encapsulation

**Encapsulation** means keeping an object’s data protected inside the class.

In Java, instance variables are usually made `private`.

```java
private String name;
private int grade;
private double average;
```

This prevents outside code from directly changing the data.

For example, this should not be allowed:

```java
s1.average = 150;
```

Instead, we use methods to control how the data is accessed or changed.


## Getters and Setters

A **getter** returns the value of a private variable.

A **setter** changes the value of a private variable.

```java
public double getAverage() {
    return average;
}

public void setAverage(double average) {
    if (average >= 0 && average <= 100) {
        this.average = average;
    }
}
```

The setter protects the object from invalid data.

This means:

```java
s1.setAverage(95);
```

is allowed, but:

```java
s1.setAverage(150);
```

will not change the average.

This is one of the main benefits of encapsulation.


## The `toString()` Method

The `toString()` method controls how an object is displayed as text.

```java
public String toString() {
    return name + " | Grade: " + grade + " | Average: " + average;
}
```

Now if we print the object:

```java
System.out.println(s1);
```

Java automatically calls `toString()`.

Output:

```text
Mitchell | Grade: 12 | Average: 86.5
```

Without a custom `toString()` method, Java prints a less useful memory-style value.


## Complete Student Class

```java
public class Student {
    private String name;
    private int grade;
    private double average;

    public Student(String name, int grade, double average) {
        this.name = name;
        this.grade = grade;
        this.average = average;
    }

    public String getName() {
        return name;
    }

    public int getGrade() {
        return grade;
    }

    public double getAverage() {
        return average;
    }

    public void setAverage(double average) {
        if (average >= 0 && average <= 100) {
            this.average = average;
        }
    }

    public boolean isPassing() {
        return average >= 50;
    }

    public String toString() {
        return name + " | Grade: " + grade + " | Average: " + average;
    }
}
```

Example use:

```java
public class Main {
    public static void main(String[] args) {
        Student s1 = new Student("Mitchell", 12, 86.5);

        System.out.println(s1);
        System.out.println(s1.getName());
        System.out.println(s1.isPassing());

        s1.setAverage(92);
        System.out.println(s1);
    }
}
```

Output:

```text
Mitchell | Grade: 12 | Average: 86.5
Mitchell
true
Mitchell | Grade: 12 | Average: 92.0
```

## Object References

In Java, object variables store **references**.

A reference is like a way to find the object in memory.

```java
Student s1 = new Student("Mitchell", 12, 86.5);
Student s2 = s1;
```

Here, `s1` and `s2` refer to the same object.

If we change the object through `s2`:

```java
s2.setAverage(95);
```

then we will see the change through `s1`:

```java
System.out.println(s1.getAverage());
```

Output:

```text
95.0
```

This matters because linked lists are built using object references.


## `null`

A reference can also be `null`.

```java
Student s1 = null;
```

This means `s1` does not currently refer to any object.

If we try to use it:

```java
System.out.println(s1.getName());
```

Java will produce a `NullPointerException`.

This means the program tried to use an object, but the reference was pointing to nothing.


## Another Class Example: Course

A program can have more than one class.

For example, a `Course` class could store information about a course.

```java
public class Course {
    private String courseCode;
    private String courseName;
    private String teacherName;

    public Course(String courseCode, String courseName, String teacherName) {
        this.courseCode = courseCode;
        this.courseName = courseName;
        this.teacherName = teacherName;
    }

    public String getCourseCode() {
        return courseCode;
    }

    public String getCourseName() {
        return courseName;
    }

    public String getTeacherName() {
        return teacherName;
    }

    public String toString() {
        return courseCode + ": " + courseName + " with " + teacherName;
    }
}
```

Using it:

```java
Course course = new Course("ICS4U", "Computer Science", "Ms. Marie");

System.out.println(course);
```

Output:

```text
ICS4U: Computer Science with Ms. Marie
```

This shows that each class represents one meaningful part of the program.


## Classes Working Together

Objects can also store other objects.

For example, a `Student` could store a `Course`.

```java
public class Student {
    private String name;
    private int grade;
    private Course course;

    public Student(String name, int grade, Course course) {
        this.name = name;
        this.grade = grade;
        this.course = course;
    }

    public String toString() {
        return name + " is in grade " + grade + " and is taking " + course;
    }
}
```

Using it:

```java
Course course = new Course("ICS4U", "Computer Science", "Ms. Marie");
Student student = new Student("Mitchell", 12, course);

System.out.println(student);
```

Output:

```text
Mitchell is in grade 12 and is taking ICS4U: Computer Science with Ms. Marie
```

This is important because OOP programs are usually made of multiple objects working together.

## OOP Principles Summary

| Principle | Meaning |
|---|---|
| Encapsulation | Protecting data inside a class |
| Abstraction | Hiding unnecessary details |
| Inheritance | Creating a class based on another class |
| Polymorphism | Allowing related objects to be treated in flexible ways |

## Linked Lists

A linked list is a data structure made of connected nodes.

Each node stores:

1. data
2. a reference to the next node

A linked list looks like this:

```text
[10] -> [20] -> [30] -> null
```

Each box is a node.

The final node points to `null`, meaning the list has ended.

Linked lists are a good example of OOP because they use objects and references.

A linked list usually has:

| Class | Responsibility |
|---|---|
| `Node` | Stores one piece of data and a reference to the next node |
| `LinkedList` | Manages the whole list |

This shows an important OOP design idea: each class should have a clear job.


### The Node Class

```java
public class Node {
    int data;
    Node next;

    public Node(int data) {
        this.data = data;
        this.next = null;
    }
}
```

A node stores an integer and a reference to another node.

```java
Node next;
```

means this node can point to another node.

### Manually Linking Nodes

```java
Node first = new Node(10);
Node second = new Node(20);
Node third = new Node(30);

first.next = second;
second.next = third;
third.next = null;
```

This creates:

```text
[10] -> [20] -> [30] -> null
```

### Traversing a Linked List

To traverse a linked list, start at the first node and follow the `next` links.

```java
Node current = first;

while (current != null) {
    System.out.println(current.data);
    current = current.next;
}
```

Output:

```text
10
20
30
```

This line moves to the next node:

```java
current = current.next;
```

The loop stops when `current` becomes `null`.

### LinkedList Class

Instead of manually connecting nodes, we can create a class to manage the list.

```java
public class LinkedList {
    private Node head;

    public LinkedList() {
        head = null;
    }

    public void addFirst(int data) {
        Node newNode = new Node(data);

        newNode.next = head;
        head = newNode;
    }

    public void addLast(int data) {
        Node newNode = new Node(data);

        if (head == null) {
            head = newNode;
            return;
        }

        Node current = head;

        while (current.next != null) {
            current = current.next;
        }

        current.next = newNode;
    }

    public boolean contains(int target) {
        Node current = head;

        while (current != null) {
            if (current.data == target) {
                return true;
            }

            current = current.next;
        }

        return false;
    }

    public void display() {
        Node current = head;

        while (current != null) {
            System.out.print(current.data + " -> ");
            current = current.next;
        }

        System.out.println("null");
    }
}
```

### Using the Linked List

```java
public class Main {
    public static void main(String[] args) {
        LinkedList list = new LinkedList();

        list.addLast(10);
        list.addLast(20);
        list.addLast(30);

        list.display();

        list.addFirst(5);
        list.display();

        System.out.println(list.contains(20));
        System.out.println(list.contains(99));
    }
}
```

Output:

```text
10 -> 20 -> 30 -> null
5 -> 10 -> 20 -> 30 -> null
true
false
```

### Why `head` is Private

In the `LinkedList` class, `head` is private.

```java
private Node head;
```

This is an example of encapsulation.

Outside code should not directly change the head of the list.

Instead of doing this:

```java
list.head = null;
```

outside code should use the public methods provided by the class.

For example:

```java
list.addFirst(5);
list.addLast(10);
list.display();
```

The linked list hides the details of how nodes are connected.

This is also an example of abstraction.

### Arrays vs Linked Lists

| Feature | Array | Linked List |
|---|---|---|
| Size | Fixed | Can grow and shrink |
| Access by index | Fast | Slow |
| Add to front | Slow | Fast |
| Search | Linear | Linear |
| Structure | Stored side by side | Connected through references |

With an array, values are stored in order beside each other.

With a linked list, each node stores a reference to the next node.

### Big-O Summary

For a basic singly linked list:

| Operation | Big-O |
|---|---:|
| Add to front | `O(1)` |
| Add to end | `O(n)` |
| Search | `O(n)` |
| Display | `O(n)` |

Adding to the front is fast because the list only needs to update the head.

Adding to the end is slower because the list has to find the last node first.