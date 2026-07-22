# Linked Lists in Java

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