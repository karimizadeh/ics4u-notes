# Algorithms - Searching

A **searching algorithm** is a step-by-step process used to find a specific value inside a collection of data.

For example, we may want to search for: `target = 42`

inside a list:
```python
numbers = [10, 25, 42, 60, 81]
```

A searching algorithm helps answer questions like:
```text
Is the value in the list?
Where is it located?
How many steps does it take to find it?
```

Searching is one of the most common tasks in computer science.

Programs search all the time:
```text
Finding a student name in a class list
Looking up a username and password
Searching for a file on a computer
Finding a product in an online store
Looking up a word in a dictionary
Checking if an item exists in a game inventory
```
The better the searching algorithm, the faster the program can find information.


## Linear Search

**Linear search** checks each item in a list one at a time, starting from the beginning. It keeps searching until the target is found or the entire list has been checked.

Imagine you are looking for a specific student’s name on an attendance sheet. You start at the top and check each name one by one:

```
Is this the name?
No.
Is this the name?
No.
Is this the name?
Yes.
```
That is linear search.

Example:
```python
numbers = [12, 45, 23, 67, 89, 34]
target = 67

for number in numbers:
    if number == target:
        print("Found")
```

This checks each number in order:
```text
12
45
23
67
```
Once it reaches `67`, the target is found.

### Linear Search with Indexes
Usually, we want to know **where** the target is found.

```python
def linear_search(items, target):
    for i in range(len(items)):
        if items[i] == target:
            return i

    return -1

numbers = [12, 45, 23, 67, 89, 34]

result = linear_search(numbers, 67)

print(result)
```
The variable `i` represents the index. `items[i]` represents the value at that index.
If a function returns `-1`, we can use that to mean: `The item was not found.` because in Python, valid list indexes start at `0`.

Output: `3`

### Linear Search Walkthrough

Given:
```python
numbers = [5, 9, 2, 8, 4]
target = 8
```

The algorithm checks:
```text
Index 0: Is 5 equal to 8? No.
Index 1: Is 9 equal to 8? No.
Index 2: Is 2 equal to 8? No.
Index 3: Is 8 equal to 8? Yes.
```

The function returns: `3`, because `8` is located at index `3`.

## Best, Worst, and Average Case for Linear Search

### Best Case

The target is the first item in the list.

```python
numbers = [8, 5, 9, 2, 4]
target = 8
```
Only one comparison is needed.

Big-O: `O(1)`


### Worst Case

The target is at the end of the list, or the target is not in the list.

```python
numbers = [5, 9, 2, 4, 8]
target = 8
```

The algorithm may need to check every item.

Big-O: `O(n)`
This means the number of steps grows with the size of the list.


### Average Case

On average, the target may be somewhere around the middle of the list.

Even though it may not check every item, the number of steps still grows as the list grows.

Big-O: `O(n)`
This means the number of steps grows with the size of the list.

## Binary Search

**Binary search** is a faster searching algorithm that works by repeatedly cutting the search area in half.

However, binary search only works if the list is already sorted.

For example:

```python
numbers = [3, 8, 12, 19, 25, 31, 42, 56]
```

This list is sorted from smallest to largest.

Binary search requires a sorted list.

This works:

```python
[3, 8, 12, 19, 25, 31, 42, 56]
```

This does not work correctly with binary search:

```python
[25, 3, 56, 12, 42, 8, 31, 19]
```

Binary search depends on knowing whether the target should be on the left side or the right side. That only makes sense when the data is sorted.

Imagine looking for a word in a dictionary. You would not start at page 1 and read every word. Instead, you might open near the middle. If the word you want comes alphabetically before that page, you search the left half. If the word comes after that page, you search the right half. Each step removes about half of the remaining possibilities.

That is binary search.

Binary search keeps track of three important positions:
* **low** - the starting index of the current search area.
* **high** - the ending index of the current search area.
* **mid** - the middle index of the current search area.

The middle index is calculated using:

```python
mid = (low + high) // 2
```

The `//` operator performs integer division.

Example:
```python
mid = (0 + 7) // 2
```

Result: `3`


## Binary Search Walkthrough

Given:
```python
numbers = [3, 8, 12, 19, 25, 31, 42, 56]
target = 42
```

The indexes are:
```text
Index:   0   1   2   3   4   5   6   7
Value:   3   8  12  19  25  31  42  56
```

At the start:
```python
low = 0
high = 7
```

Calculate the middle:
```python
mid = (0 + 7) // 2
mid = 3
```

Check index `3`:
```python
numbers[3] == 19
```

Compare:
```text
19 is less than 42
```

Since the list is sorted, everything to the left of `19` is also too small.

So we search the right half.

Now:
```python
low = mid + 1
low = 4
```

The new search area is:
```text
Index:   4   5   6   7
Value:  25  31  42  56
```

Calculate the new middle:
```python
mid = (4 + 7) // 2
mid = 5
```

Check index `5`:
```python
numbers[5] == 31
```

Compare:
```text
31 is less than 42
```

Search the right half again.

Now:
```python
low = mid + 1
low = 6
```

The new search area is:
```text
Index:   6   7
Value:  42  56
```

Calculate the new middle:
```python
mid = (6 + 7) // 2
mid = 6
```

Check index `6`:
```python
numbers[6] == 42
```

The target is found.
The algorithm returns: `6`

## Binary Search Code

```python
def binary_search(items, target):
    low = 0
    high = len(items) - 1

    while low <= high:
        mid = (low + high) // 2

        if items[mid] == target:
            return mid
        elif items[mid] < target:
            low = mid + 1
        else:
            high = mid - 1

    return -1

numbers = [3, 8, 12, 19, 25, 31, 42, 56]

result = binary_search(numbers, 42)

print(result)
```

Output: `6`

If the middle item is the target:
```python
if items[mid] == target:
    return mid
```
The target has been found, so the function returns the index.

If the middle item is too small:
```python
elif items[mid] < target:
    low = mid + 1
```
The target must be to the right. So we move `low` forward.


If the middle item is too large:
```python
else:
    high = mid - 1
```
The target must be to the left. So we move `high` backward.


## Binary Search when the Target is not found

Given:

```python
numbers = [3, 8, 12, 19, 25, 31, 42, 56]
target = 50
```

Binary search keeps cutting the list in half. Eventually, `low` becomes greater than `high`. At that point, there is no search area left.

```python
while low <= high:
```

When this condition is no longer true, the loop stops.

The function returns: `-1` This means the target was not found.

### Why `low <= high`?

The loop continues while there is still a valid search area.

```python
while low <= high:
```

For example:

```text
low = 4
high = 6
```

There are still items to search.

```text
low = 6
high = 6
```

There is still one item left to check.

```text
low = 7
high = 6
```

Now the search area is empty, so the loop stops.


## Binary Search Efficiency

Binary search is much faster than linear search for large sorted lists.

Each step cuts the search area in half.

For a list of 8 items:

```text
8 → 4 → 2 → 1
```

For a list of 1,000,000 items:

```text
1,000,000 → 500,000 → 250,000 → 125,000 → ...
```

It only takes about 20 steps to search through one million sorted items.


## Binary Search Big-O

The worst-case time complexity of binary search is: `O(log n)`. This means the number of steps grows very slowly as the input size grows.


### Linear Search vs Binary Search

| Feature | Linear Search | Binary Search |
|---|---|---|
| Works on unsorted lists? | Yes | No |
| Requires sorted data? | No | Yes |
| Checks items | One at a time | Middle item, then halves |
| Worst-case Big-O | O(n) | O(log n) |
| Easier to code? | Yes | Slightly harder |
| Best for | Small or unsorted lists | Large sorted lists |


### Comparing Step Counts

| List Size | Linear Search Worst Case | Binary Search Worst Case |
|---:|---:|---:|
| 10 | 10 steps | About 4 steps |
| 100 | 100 steps | About 7 steps |
| 1,000 | 1,000 steps | About 10 steps |
| 1,000,000 | 1,000,000 steps | About 20 steps |

Binary search becomes much more powerful as the list gets larger. Even though Binary search is fast, the list must already be sorted. If the list is not sorted, we may need to sort it first.


## Searching Strings

Searching algorithms can also work with strings.
```python
def linear_search(items, target):
    for i in range(len(items)):
        if items[i] == target:
            return i

    return -1
names = ["David", "Eric", "Dylan", "Mitchell", "William"]

result = linear_search(names, "Mitchell")

print(result)
```
Output: `3`

Binary search can also work with strings if the list is sorted alphabetically.


## Searching With Duplicates

Sometimes a list may contain the same value more than once.
```python
numbers = [4, 7, 2, 7, 9, 7]
target = 7
```

A normal linear search returns the first match.

```python
def linear_search(items, target):
    for i in range(len(items)):
        if items[i] == target:
            return i

    return -1
```

Output: `1`


This is because the first `7` appears at index `1`.

### Finding All Matches

If we want all indexes where the target appears, we can store them in a list.

```python
def find_all(items, target):
    indexes = []

    for i in range(len(items)):
        if items[i] == target:
            indexes.append(i)

    return indexes
```

Example:

```python
numbers = [4, 7, 2, 7, 9, 7]

result = find_all(numbers, 7)

print(result)
```

Output:

```text
[1, 3, 5]
```


## Common Mistakes

### Mistake 1: Using Binary Search on an Unsorted List

Incorrect:

```python
numbers = [20, 5, 12, 8, 30]
binary_search(numbers, 8)
```
The list is not sorted, so binary search may give the wrong result.

Correct:
```python
numbers = [5, 8, 12, 20, 30]

binary_search(numbers, 8)
```

### Mistake 2: Forgetting to Update `low` or `high`

Incorrect:

```python
elif items[mid] < target:
    low = mid
```

This can cause an infinite loop.

Correct:

```python
elif items[mid] < target:
    low = mid + 1
```

We use `mid + 1` because we already checked `mid`.


### Mistake 3: Using `<` Instead of `<=` in the While Loop

Incorrect:

```python
while low < high:
```

This may skip the final remaining item.

Correct:

```python
while low <= high:
```

This allows the algorithm to check the last possible item.


### Mistake 4: Returning Too Early

Incorrect:

```python
def linear_search(items, target):
    for i in range(len(items)):
        if items[i] == target:
            return i
        else:
            return -1
```

This only checks the first item.

Correct:

```python
def linear_search(items, target):
    for i in range(len(items)):
        if items[i] == target:
            return i

    return -1
```

The `return -1` should happen only after the entire list has been checked.


## Use Linear Search When:

```text
The list is small
The list is unsorted
You only need to search once
Simplicity matters more than speed
```


## Use Binary Search When:

```text
The list is sorted
The list is large
You need to search many times
Efficiency matters
```

Linear search removes one item from the search area each time, whereas, Binary search removes about half of the remaining items each time.

The main idea is that different algorithms can solve the same problem, but some are much more efficient than others.
