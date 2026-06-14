# Algorithms - Sorting

Sorting means arranging data in a specific order.

Common sorting orders include:

```python
[2, 4, 6, 8, 10]      # ascending order
[10, 8, 6, 4, 2]      # descending order
["apple", "banana", "cherry"]  # alphabetical order
```

Sorting algorithms are important because they help us understand:
- how algorithms process data
- how loops and comparisons work together
- how to trace code carefully
- how to compare algorithm efficiency
- how different strategies can solve the same problem

Even though real programs often use built-in sorting tools, learning sorting algorithms helps build problem-solving skills.

Most sorting algorithms repeat the same general pattern:
1. Compare two or more values.
2. Decide whether they are in the correct order.
3. Swap or move values if needed.
4. Repeat until the whole list is sorted.

Different sorting algorithms use different strategies to decide what to compare and when to swap.

Some use swap, like the code below.
```python
numbers = [5, 2, 8]
numbers[0], numbers[1] = numbers[1], numbers[0]
print(numbers)  # [2, 5, 8]
```
This switches the values at index `0` and index `1`.

And some sorting algorithms split the list into two parts:
- the sorted section
- the unsorted section

The sorted section contains values that have already been placed in order. The unsorted section contains values that still need to be checked, moved, or swapped.

## Bubble Sort

Bubble sort compares neighbouring values and swaps them if they are in the wrong order. Large values slowly move, or “bubble,” toward the end of the list.

Bubble sort uses nested loops. For a list with `n` items, the number of comparisons grows roughly with `n²`.

Bubble sort has a time complexity of: `O(n^2)`

Bubble sort is easy to understand, but it is not efficient for large lists.


### How it works

Starting list:

```python
[5, 2, 8, 1]
```

Compare the first two values:

```text
5 and 2
```

Since 5 is greater than 2, swap them:

```python
[2, 5, 8, 1]
```

Compare the next two values:

```text
5 and 8
```

They are already in the correct order, so do nothing:

```python
[2, 5, 8, 1]
```

Compare the next two values:

```text
8 and 1
```

Since 8 is greater than 1, swap them:

```python
[2, 5, 1, 8]
```

After one full pass, the largest value has moved to the end.

### Bubble Sort Code

```python
def bubble_sort(numbers):
    n = len(numbers)

    for pass_num in range(n - 1):
        for i in range(n - 1 - pass_num):
            if numbers[i] > numbers[i + 1]:
                numbers[i], numbers[i + 1] = numbers[i + 1], numbers[i]

    return numbers
```

### Bubble Sort Trace

Starting list:

```python
[5, 2, 8, 1]
```

Pass 1:
```python
[2, 5, 8, 1]
[2, 5, 1, 8]
```

Pass 2:
```python
[2, 1, 5, 8]
```

Pass 3:
```python
[1, 2, 5, 8]
```

Final sorted list:
```python
[1, 2, 5, 8]
```

## Selection Sort
Selection sort repeatedly finds the smallest value from the unsorted part of the list and moves it to the front. The sorted section grows from left to right.

The sorted section contains values that have already been placed in order.

The unsorted section contains values that still need to be checked, moved, or swapped.

Selection sort uses nested loops. It has a time complexity of: `O(n^2)`

Selection sort usually makes fewer swaps than bubble sort, but it still makes many comparisons.


### Example

Starting list:

```python
[5, 2, 8, 1]
```

Find the smallest value in the whole list:

```text
1
```

Swap it with the first value:

```python
[1, 2, 8, 5]
```

Now the first value is sorted.

Next, find the smallest value in the remaining unsorted part:

```python
[2, 8, 5]
```

The smallest value is:

```text
2
```

It is already in the correct position, so nothing changes.

```python
[1, 2, 8, 5]
```

Next, find the smallest value in:

```python
[8, 5]
```

The smallest value is:

```text
5
```

Swap it with 8:

```python
[1, 2, 5, 8]
```

The list is now sorted.

### Selection Sort Code

```python
def selection_sort(numbers):
    n = len(numbers)

    for start in range(n - 1):
        min_index = start

        for i in range(start + 1, n):
            if numbers[i] < numbers[min_index]:
                min_index = i

        numbers[start], numbers[min_index] = numbers[min_index], numbers[start]

    return numbers
```

### Selection Sort Trace

Starting list:

```python
[5, 2, 8, 1]
```

Pass 1:

Smallest value is `1`.

```python
[1, 2, 8, 5]
```

Pass 2:

Smallest value in the unsorted section is `2`.

```python
[1, 2, 8, 5]
```

Pass 3:

Smallest value in the unsorted section is `5`.

```python
[1, 2, 5, 8]
```

Final sorted list:

```python
[1, 2, 5, 8]
```

## Insertion Sort
Insertion sort builds a sorted section one item at a time. It takes each new value and inserts it into the correct position within the already sorted section. This is similar to how many people sort a hand of playing cards.

Insertion sort has a time complexity of: `O(n^2)`

However, insertion sort can be efficient when the list is already mostly sorted. For a nearly sorted list, it may not need to move many values.

### Example

Starting list:

```python
[5, 2, 8, 1]
```

Think of the first item as already sorted:

```text
[5] [2, 8, 1]
```

Now insert `2` into the sorted section.

Since `2` is smaller than `5`, move `5` to the right and place `2` before it.

```text
[2, 5] [8, 1]
```

Now insert `8`.

Since `8` is already bigger than `5`, it stays where it is.

```text
[2, 5, 8] [1]
```

Now insert `1`.

Move `8`, `5`, and `2` to the right.

```python
[1, 2, 5, 8]
```

### Insertion Sort Code

```python
def insertion_sort(numbers):
    n = len(numbers)

    for i in range(1, n):
        current_value = numbers[i]
        position = i

        while position > 0 and numbers[position - 1] > current_value:
            numbers[position] = numbers[position - 1]
            position -= 1

        numbers[position] = current_value

    return numbers
```

### Insertion Sort Trace

Starting list:

```python
[5, 2, 8, 1]
```

Insert `2`:

```python
[2, 5, 8, 1]
```

Insert `8`:

```python
[2, 5, 8, 1]
```

Insert `1`:

```python
[1, 2, 5, 8]
```

Final sorted list:

```python
[1, 2, 5, 8]
```

## Merge Sort

Merge sort uses a divide-and-conquer strategy. It works by:

1. Dividing the list into smaller lists.
2. Sorting the smaller lists.
3. Merging the sorted lists back together.

Merge sort is more efficient than bubble sort, selection sort, and insertion sort for large lists.

Merge sort has a time complexity of: `O(n log n)`. This is more efficient than `O(n^2)` for large lists.

Merge sort is usually faster for large datasets, but it uses extra memory because it creates new lists during the merge process.

### Divide-and-Conquer

Divide-and-conquer means breaking a large problem into smaller versions of the same problem.

For merge sort:

```python
[5, 2, 8, 1]
```

Divide the list:

```text
[5, 2] [8, 1]
```

Divide again:

```text
[5] [2] [8] [1]
```

Each single-item list is already sorted.

Now merge sorted lists:

```text
[2, 5] [1, 8]
```

Merge again:

```python
[1, 2, 5, 8]
```

### Merge Sort Code

```python
def merge_sort(numbers):
    if len(numbers) <= 1:
        return numbers

    middle = len(numbers) // 2

    left_half = numbers[:middle]
    right_half = numbers[middle:]

    sorted_left = merge_sort(left_half)
    sorted_right = merge_sort(right_half)

    return merge(sorted_left, sorted_right)
```

### Merge Helper Function

```python
def merge(left, right):
    result = []

    left_index = 0
    right_index = 0

    while left_index < len(left) and right_index < len(right):
        if left[left_index] < right[right_index]:
            result.append(left[left_index])
            left_index += 1
        else:
            result.append(right[right_index])
            right_index += 1

    while left_index < len(left):
        result.append(left[left_index])
        left_index += 1

    while right_index < len(right):
        result.append(right[right_index])
        right_index += 1

    return result
```

## Quick Sort

Quick sort also uses divide-and-conquer. It works by choosing a value called a pivot. Then it separates the remaining values into two groups:

1. Values less than or equal to the pivot.
2. Values greater than the pivot.

Then it recursively sorts each group.

Quick sort has an average time complexity of: `O(n log n)`. However, quick sort can become slower if the pivot choices are poor. In the worst case, quick sort can become: `O(n^2)`. This can happen if the pivot repeatedly creates very uneven groups.

For example, always choosing the first item as the pivot can be inefficient if the list is already sorted.


### Example

Starting list:

```python
[5, 2, 8, 1]
```

Choose a pivot:

```text
5
```

Values less than or equal to 5:

```python
[2, 1]
```

Values greater than 5:

```python
[8]
```

Sort each side:

```text
[1, 2] 5 [8]
```

Final sorted list:

```python
[1, 2, 5, 8]
```

### Quick Sort Code

```python
def quick_sort(numbers):
    if len(numbers) <= 1:
        return numbers

    pivot = numbers[0]

    less_or_equal = []
    greater = []

    for i in range(1, len(numbers)):
        if numbers[i] <= pivot:
            less_or_equal.append(numbers[i])
        else:
            greater.append(numbers[i])

    sorted_left = quick_sort(less_or_equal)
    sorted_right = quick_sort(greater)

    return sorted_left + [pivot] + sorted_right
```

## Comparing Sorting Algorithms

| Algorithm | Main Strategy | Average Time Complexity | Notes |
|---|---|---:|---|
| Bubble Sort | Swap neighbouring values | O(n^2) | Simple, but inefficient |
| Selection Sort | Find the smallest value and move it forward | O(n^2) | Fewer swaps than bubble sort |
| Insertion Sort | Insert values into a sorted section | O(n^2) | Good for mostly sorted lists |
| Merge Sort | Divide, sort, and merge | O(n log n) | Fast, but uses extra memory |
| Quick Sort | Pick a pivot and partition | O(n log n) average | Fast on average, but pivot choice matters |

## Common Sorting Mistakes

### Mistake 1: Going Out of Range

This causes an error:

```python
for i in range(len(numbers)):
    if numbers[i] > numbers[i + 1]:
        print("swap")
```

The problem is that when `i` is the last index, `i + 1` is outside the list.

Correct version:

```python
for i in range(len(numbers) - 1):
    if numbers[i] > numbers[i + 1]:
        print("swap")
```

### Mistake 2: Forgetting to Swap Properly

Incorrect:

```python
numbers[i] = numbers[i + 1]
numbers[i + 1] = numbers[i]
```

This overwrites one value before saving it.

Correct:

```python
numbers[i], numbers[i + 1] = numbers[i + 1], numbers[i]
```

Another correct version:

```python
temp = numbers[i]
numbers[i] = numbers[i + 1]
numbers[i + 1] = temp
```

### Mistake 3: Confusing Index and Value

```python
for i in range(len(numbers)):
    print(i)
```

This prints indexes.

```python
for value in numbers:
    print(value)
```

This prints values.

Sorting algorithms often need indexes because we need to compare and swap values at specific positions.

### Mistake 4: Forgetting the Base Case in Recursive Sorts

Recursive sorting algorithms such as merge sort and quick sort need a base case.

Without a base case, the function keeps calling itself forever.

```python
if len(numbers) <= 1:
    return numbers
```

## Full Example Program

```python
def bubble_sort(numbers):
    n = len(numbers)

    for pass_num in range(n - 1):
        for i in range(n - 1 - pass_num):
            if numbers[i] > numbers[i + 1]:
                numbers[i], numbers[i + 1] = numbers[i + 1], numbers[i]

    return numbers


def selection_sort(numbers):
    n = len(numbers)

    for start in range(n - 1):
        min_index = start

        for i in range(start + 1, n):
            if numbers[i] < numbers[min_index]:
                min_index = i

        numbers[start], numbers[min_index] = numbers[min_index], numbers[start]

    return numbers


def insertion_sort(numbers):
    n = len(numbers)

    for i in range(1, n):
        current_value = numbers[i]
        position = i

        while position > 0 and numbers[position - 1] > current_value:
            numbers[position] = numbers[position - 1]
            position -= 1

        numbers[position] = current_value

    return numbers


def merge(left, right):
    result = []

    left_index = 0
    right_index = 0

    while left_index < len(left) and right_index < len(right):
        if left[left_index] < right[right_index]:
            result.append(left[left_index])
            left_index += 1
        else:
            result.append(right[right_index])
            right_index += 1

    while left_index < len(left):
        result.append(left[left_index])
        left_index += 1

    while right_index < len(right):
        result.append(right[right_index])
        right_index += 1

    return result


def merge_sort(numbers):
    if len(numbers) <= 1:
        return numbers

    middle = len(numbers) // 2

    left_half = numbers[:middle]
    right_half = numbers[middle:]

    sorted_left = merge_sort(left_half)
    sorted_right = merge_sort(right_half)

    return merge(sorted_left, sorted_right)


def quick_sort(numbers):
    if len(numbers) <= 1:
        return numbers

    pivot = numbers[0]

    less_or_equal = []
    greater = []

    for i in range(1, len(numbers)):
        if numbers[i] <= pivot:
            less_or_equal.append(numbers[i])
        else:
            greater.append(numbers[i])

    sorted_left = quick_sort(less_or_equal)
    sorted_right = quick_sort(greater)

    return sorted_left + [pivot] + sorted_right


numbers = [5, 2, 8, 1, 3]

print("Original list:", numbers)

print("Bubble sort:", bubble_sort(numbers.copy()))
print("Selection sort:", selection_sort(numbers.copy()))
print("Insertion sort:", insertion_sort(numbers.copy()))
print("Merge sort:", merge_sort(numbers.copy()))
print("Quick sort:", quick_sort(numbers.copy()))
```