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

Earlier Java programs used mostly `static` methods called through the class. In OOP, **instance methods** are called through an object and can directly use that object's instance variables.

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


## Inheritance

**Inheritance** lets one class reuse the fields and methods of another class instead of rewriting them.

The existing class is called the **superclass** (or parent class). The new class is called the **subclass** (or child class). A subclass is created using the `extends` keyword.

```java
public class Person {
    protected String name;

    public Person(String name) {
        this.name = name;
    }

    public void introduce() {
        System.out.println("Hi, my name is " + name);
    }
}

public class Student extends Person {
    private int grade;

    public Student(String name, int grade) {
        super(name);
        this.grade = grade;
    }

    public void showGrade() {
        System.out.println(name + " is in grade " + grade);
    }
}
```

`super(name)` calls the parent class's constructor. `Student` automatically gets the `introduce()` method from `Person`, without rewriting it.

```java
Student s1 = new Student("Mitchell", 12);
s1.introduce();  // inherited from Person
s1.showGrade();  // defined in Student
```

Output:

```text
Hi, my name is Mitchell
Mitchell is in grade 12
```

Inheritance is useful when classes share common data or behaviour but also need their own extra features.

## Polymorphism

**Polymorphism** means objects of related classes can be treated in a flexible, interchangeable way — often by overriding a shared method so each subclass behaves differently when that method is called.

```java
public class Person {
    protected String name;

    public Person(String name) {
        this.name = name;
    }

    public void introduce() {
        System.out.println("Hi, I'm a person named " + name);
    }
}

public class Student extends Person {
    public Student(String name) {
        super(name);
    }

    @Override
    public void introduce() {
        System.out.println("Hi, I'm a student named " + name);
    }
}
```

Overriding means the subclass provides its own version of a method that already exists in the superclass. The `@Override` annotation tells Java (and other readers of the code) that this is intentional.

```java
Person p1 = new Person("Marie");
Person p2 = new Student("Mitchell");

p1.introduce();
p2.introduce();
```

Output:

```text
Hi, I'm a person named Marie
Hi, I'm a student named Mitchell
```

Even though `p2` is declared as type `Person`, Java calls the `Student` version of `introduce()` because that is the actual object type. This is polymorphism: the same method call produces different behaviour depending on the object.

## OOP Principles Summary

| Principle | Meaning |
|---|---|
| Encapsulation | Protecting data inside a class |
| Abstraction | Hiding unnecessary details |
| Inheritance | Creating a class based on another class |
| Polymorphism | Allowing related objects to be treated in flexible ways |