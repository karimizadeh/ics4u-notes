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

The same thing for the simple algorithm example above. In a list of 5 values, it's easy to find the largest number. But if the list had millions of entries, we would care more about how many steps the algorithm takes, because the algorithm must still check every value at least once.

## Time Complexity vs Space Complexity

Time complexity asks:

```text
How does the number of steps grow as the input grows?
```

Space complexity asks:

```text
How much extra memory does the algorithm need as the input grows?
```

Example:

```python
def copy_items(items):
    result = []

    for item in items:
        result.append(item)

    return result
```

This algorithm is:

- `O(n)` time because it loops through all items
- `O(n)` extra space because it creates a new list with `n` items

Compare that with:

```python
def print_items(items):
    for item in items:
        print(item)
```

This is:

- `O(n)` time
- `O(1)` extra space, because it does not create a new list that grows with the input


## Big-O Notation

**Big-O notation** describes how an algorithm grows as the input size grows. It does not tell us the exact number of seconds a program takes, instead, it tells us the general growth pattern.

Two computers may run the same program at different speeds, but Big-O focuses on how the algorithm grows, not the exact hardware speed.

The input size is usually represented by the letter `n`. 
In Big-O notation, as `n` gets bigger, Big-O helps us figure out how much more work the algoritm has to do as Big-O is about `growth` not exact time.

## Common Big-O Notations

The categories below are ordered from slower-growing to faster-growing functions.

* **Constant is O(1)** - if it takes the same amount of work no matter how large the input is.
* **Linear is O(n)** - if the amount of work grows directly with the input size.
* **Logarithmic is O(log n)** - if the problem size is repeatedly reduced, usually by half.
* **Loglinear/Linearithmic is O(n log n)** - if the amount of work grows with the input size multiplied by the logarithm of the input size.
* **Quadratic is O(n^2)** - if the amount of work grows with the square of the input size.
* **Cubic is O(n^3)** - if the amount of work grows with the cube of the input size.
* **Exponential is O(2^n)** - if the work roughly doubles every time the input size increases by 1.

### Growth Comparison
| n | O(1) | O(log n) | O(n) | O(n log n) | O(n^2) | O(n^3) | O(2^n) |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 10 | 1 | about 3 | 10 | about 30 | 100 | 1,000 | 1,024 |
| 20 | 1 | about 4 | 20 | about 80 | 400 | 8,000 | 1,048,576 |
| 100 | 1 | about 7 | 100 | about 700 | 10,000 | 1,000,000 | enormous |
| 1,000 | 1 | about 10 | 1,000 | about 10,000 | 1,000,000 | 1,000,000,000 | enormous |

### Visualizing Big O Notation
Imagine you have different tasks to do, like sorting a list, finding an item, or calculating something based on your data. How long it takes to do those tasks depends on how much data you have.

* **O(1)**: It’s like flipping a light switch. No matter how many lights are in the room, flipping the switch takes the same time.
* **O(log n)**: It’s like finding a word in a dictionary. You don’t have to check every page; you jump around, cutting down the search space quickly.
* **O(n)**: It’s like reading a book. The longer the book, the longer it takes to read.
* **O(n log n)**: It’s like splitting a pile of papers into smaller piles, organizing each pile, and then merging them back together in order.
* **O(n^2)**: It’s like comparing every student in a class with every other student to see who has worked together before. The bigger the class, the number of comparisons grows quickly.
* **O(n^3)**: It’s like checking every possible group of three students in a class. As the class grows, the number of groups grows very quickly.
* **O(2^n)**: It’s like trying every possible combination of yes/no choices. Each new choice doubles the number of possibilities.

![Big-O complexity graph showing O(1), O(log n), O(n), O(n log n), O(n²), O(n³), O(2ⁿ), and O(n!)](https://commons.wikimedia.org/wiki/Special:Redirect/file/Comparison%20computational%20complexity.svg)
*Image source: Wikimedia Commons*

## Big-O Breakdown

### O(1) - Constant
```python
def get_first_item(items): 
    return items[0]
```
This function only accesses the first item. It does not matter if the list has 5 items or 5 million items.

The function still does one main operation.

### O(n) - Linear
```python
def print_all_items(items): 
    for item in items: 
        print(item)
```
If there are `n` items, the loop runs `n` times. Basically, the loop runs once for every number.

### O(log n) - Logarithmic Time
In Big-O, `log n` usually means we are repeatedly cutting the problem down.

For now, you do not need to calculate exact logarithms. You just need to recognize the pattern:
```text
1000 → 500 → 250 → 125 → 62 → 31 → 15 → 7 → 3 → 1
```

```python
def binary_search(numbers, target): 
    low = 0 
    high = len(numbers) - 1 
    while low <= high: 
        middle = (low + high) // 2 
        if numbers[middle] == target: 
            return True 
        elif numbers[middle] < target: 
            low = middle + 1 
        else: 
            high = middle - 1 
    return False
```
A common example is binary search. Binary search does not check every item but instead it keeps cutting the search area in half. However, binary search only works when the data is already sorted.

Like so:
```
1000 items 
500 items 
250 items 
125 items 
62 items 
31 items 
15 items 
7 items 
3 items 
1 item
```

### O(1) Does Not Always Mean Fast

`O(1)` means the work does not grow with the input size. It does not automatically mean the operation is tiny or instant.

For example, a function might always perform 500 steps no matter how big the list is. That is still constant time because the number of steps does not grow with `n`.

### O(n) with Two Separate Loops

Two separate loops through the same list are still linear.

```python
def print_twice(items):
    for item in items:
        print(item)

    for item in items:
        print(item)
```

This is `O(2n)`, which simplifies to `O(n)`.

The loops are separate, not nested.



### O(n log n) - Loglinear/Linearithmic Time

An algorithm is O(n log n) when the amount of work grows with the input size multiplied by the logarithm of the input size.

This often happens when an algorithm repeatedly divides the data into smaller parts and then processes or combines those parts.

Many efficient sorting algorithms, such as merge sort and efficient quicksort, are O(n log n).

For large inputs, O(n log n) is usually much faster than O(n^2), but slower than O(n).

### O(n^2) - Quadratic Time
```python
def print_pairs(items): 
    for i in range(len(items)): 
        for j in range(len(items)): 
            print(items[i], items[j])
```
If there are 5 items: `5 × 5 = 25 pairs`

If there are 100 items: `100 × 100 = 10,000 pairs`

If there are 1000 items: `1000 × 1000 = 1,000,000 pairs`

### O(n^3) - Cubic Time
Cubic Time happens when there are three nested loops that each depend on the size of the input. It appears in algorithms that compare or process every possible group of three items because it checks every possible combination of three numbers.
```python
def print_triplets(items):
    for i in range(len(items)):
        for j in range(len(items)):
            for k in range(len(items)):
                print(items[i], items[j], items[k])
```
If there are 5 items: `5 × 5 × 5 = 125 operations`

If there are 100 items: `100 × 100 × 100 = 1,000,000 operations`

If there are 1000 items: `1000 × 1000 × 1000 = 1,000,000,000 operations`

### O(2^n) - Exponential Time
These algorithms become very slow very quickly.
Some recursive algorithms that try every possible choice can be exponential.

```python
def fibonacci(n): 
    if n <= 1: 
        return n 
        
    return fibonacci(n - 1) + fibonacci(n - 2)
```
This version of Fibonacci repeats a lot of work. A small increase in `n` can cause huge increase in runtime.

## Best Case, Worst Case, and Average Case

Some algorithms behave differently depending on the input.

For example, in linear search:

```python
def linear_search(items, target):
    for item in items:
        if item == target:
            return True

    return False
```
If the target is the first item, the algorithm finishes right away. This is the best case: O(1).

If the target is the last item, or not in the list at all, the algorithm must check every item. This is the worst case: O(n).

When we talk about Big-O, we usually talk about the worst case unless stated otherwise.


## Simplifying Big-O

Big-O focuses on the fastest-growing part of an algorithm.

### Ignore constants

O(2n) becomes O(n)

O(5n) becomes O(n)

O(100n) becomes O(n)

### Drop smaller terms

O(n + 1) becomes O(n)

O(n² + n) becomes O(n²)

O(n³ + n² + n) becomes O(n³)

Big-O is not about counting every exact operation. It is about describing the overall growth pattern.

## How to Analyze Code for Big-O

When analyzing code, ask:

1. What is the input size, n?
2. Are there loops?
3. Are the loops separate or nested?
4. Does the problem get cut in half?
5. Which part grows the fastest?

### Example

```python
def example(numbers):
    print(numbers[0])

    for number in numbers:
        print(number)

    for i in range(len(numbers)):
        for j in range(len(numbers)):
            print(numbers[i], numbers[j])
```
Breakdown:
```
print(numbers[0]) → O(1)
single loop → O(n)
nested loop → O(n^2)
```
The final answer of this code would be `O(n^2)` because of the nested loop. The O(n²) part grows the fastest, so it dominates the whole algorithm.


## Big-O Quick Reference

| Big-O | Growth Description | Common Pattern |
|---|---|---|
| `O(1)` | Does not grow with input | Access one item, fixed number of steps |
| `O(log n)` | Grows very slowly | Repeatedly cut problem in half |
| `O(n)` | Grows directly with input | One loop through input |
| `O(n log n)` | Efficient divide-and-combine pattern | Merge sort-style algorithms |
| `O(n²)` | Grows quickly | Nested loops over same input |
| `O(n³)` | Grows very quickly | Three nested loops |
| `O(2^n)` | Doubles with each extra input | Trying every yes/no combination |
| `O(n!)` | Extremely fast growth | Trying every possible ordering |