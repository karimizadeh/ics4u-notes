# Algorithms

As you may remember from Computational Thinking in ICS3U, an algorithm is a step-by-step process used to solve a problem.

In Computer Science, an algorithm usually takes some `input`, performs a series of steps, and produces an `output`.

### Simple Algorithm Example
Problem: Find the largest number in a list

Input: `[4, 9, 2, 15, 7]`

Output: `15`

Algorithm:
1. Start by assuming the first number is the largest.
1. Look at each number in the list.
1. If the current number is larger than the largest number so far, update the largest number.
1. When finished, return the largest number.

Algorithm written as code:
```python
def find_largest(numbers): 
    largest = numbers[0] 
    for number in numbers: 
        if number > largest: 
            largest = number 
            return largest 

values = [4, 9, 2, 15, 7] 
print(find_largest(values))
```

## Algorithm Analysis

Algorithm analysis is the process of studying how efficient an algorithm is.

When we analyze an algorith, we usually care about two things:
- **Time Complexity** - How long it takes the algorithm to run
- **Space Complexity** - How much extra memory the algorithm uses.

Different algorithms can solve the same problem, but some are much faster or more efficient than others. For small inputs (or batches of data), the difference may not matter nor be noticeable. For large inputs (or batches of data), the difference can be huge.

Searching for a student name in a class of 30 students is easy. However, searching for a student name in a database of 235,000+ students requires a more efficient approach.

The same thing for the simple algorithm example above. In a list of 5 values, its easy to find the largest number. But if the list had millions of entries, a different approach is necessary.

## Big-O Notation

**Big-O notation** describes how an algorithm grows as the input size grows. It does not tell us the exact number of seconds a program takes, instead, it tells us the general growth pattern.

The input size is usually represented by the letter `n`. 
In Big-O notation, as `n` gets bigger, it needs to figure out how much more work the algoritm has to do as Big-O is about `growth` not exact time.

## Common Big-O Notations
* Constant - O(1) - if it takes the same amount of work no matter how large the input is.
* Linear - O(n) - if the amount of work grows directly with the input size.
* Logarithmic - O(log n) - f the problem size is repeatedly reduced, usually by half.
* Loglinear - O(n log n) - when it does a logarithmic amount of work for each item, or when the work is split and combined efficiently.
* Quadratic - O(n^2) - if the amount of work grows with the square of the input size.
* Cubic - O(n^3)
* Exponential - O(2^n) - if the work roughly doubles every time the input size increases by 1.

### Order of Algorithms from Best to Worst:
1. O(1) – Constant Time - if it takes the same amount of work no matter how large the input is.
1. O(log n) – Logarithmic Time - if the problem size is repeatedly reduced, usually by half.
1. O(n) – Linear Time - if the amount of work grows directly with the input size.
1. O(n log n) – Loglinear/Linearithmic Time
1. O(n^2) – Quadratic Time - if the amount of work grows with the square of the input size.
1. O (n^3) - Cubic Time - if the amount of work grows with the cube of the input size.
1. O(2n) – Exponential Time - if the work roughly doubles every time the input size increases by 1.

### Visualizing Big O Notation
Imagine you have different tasks to do, like sorting a list, finding an item, or calculating something based on your data. How long it takes to do those tasks depends on how much data you have.

* O(1): It’s like flipping a light switch. No matter how many lights are in the room, flipping the switch takes the same time.
* O(log n): It’s like finding a word in a dictionary. You don’t have to check every page; you jump around,
cutting down the search space quickly.
* O(n): It’s like reading a book. The longer the book, the longer it takes to read.
* O(n2): It’s like comparing every student in a class with every other student to find the tallest one. The
bigger the class, the longer it takes.