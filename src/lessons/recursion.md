# Recursion in Python

## What is Recursion?
To put it simply, recursion is when a function calls itself. It is a technique that solves a problem by breaking it into smaller versions of the same problem.

Recursion is like asking the next person to solve a smaller version of the same problem, until someone reaches the easiest possible case.

or

To clean a stack of plates, you clean the top plate, then clean the rest of the stack.

## How Recursion Works
* Base Case: the condition that stops the recursion. Without a base case, the function may keep calling itself until Python stops the program with a `RecursionError`.
* Recursive Case: this is where the function calls itself with a smaller or simpler version of the problem. Moving closer to the Base Case.

## Important Considerations
* Performance: Recursive solutions can be elegant, but they are sometimes less efficient than iterative
solutions.
* Stack Overflow: Deep recursion can lead to stack overflow if the base case is not reached quickly
enough, especially with large input sizes.

## Simple Example: Countdown

Consider this function:

```python
def countdown(n):
  print(n)
  countdown(n - 1)

countdown(5) #Initial Function Call
```
This code has no obvious errors. It will run perfectly fine, however, this function never stops. 
```
5
4
3
2
1
0
-1
-2
-3
...
```
The function keeps calling itself because it has no Base Case. Eventually, Python will stop the program and give an error: `RecursionError: maximum recursion depth exceeded`

```python
def countdown(n):
  if n == 0: #Base Case
    print("Blast off!")
  else:
    print(n)
    countdown(n - 1) #Recursive Case

countdown(5) #Initial Function Call
```

```
5
4
3
2
1
Blast off!
```

### What is happening?
The function starts with `n = 5` and each time the function runs, it prints the current number and then calls itself with a smaller number:

```python
countdown(5)
countdown(4)
countdown(3)
countdown(2)
countdown(1)
countdown(0)
```

When `n == 0`, the function stops called itself.

## Tracing Recursive Calls (Call Stack)
When a recursive function runs, Python places each `call` onto the `call stack`. The `call stack` has to remember each unfinished function calls.
TLDR: The call stack keeps track of functions that are currently running but not finished yet. 

example:

```python
def say_hi(n):
  if n == 0: #Base Case
    return
  print("Hi")
  say_hi(n - 1) #Recursive Case

say_hi(3) #Initial Function Call
```
Trace
```
say_hi(3)
  ↪ print("Hi")
  ↪ say_hi(2)
    ↪ print("Hi")
    ↪ say_hi(1)
      ↪ print("Hi")
      ↪ say_hi(0)
        ↪ return
```
Output
```
Hi
Hi
Hi
```
The function stops when `n == 0`.

The `call stack` follows `LIFO` (Last In, First Out). LIFO is like undoing your steps. The last thing you did is the first thing you go back to.

```python
def count(n):
  if n == 0:
    return

  print("Before:", n)
  count(n - 1)
  print("After:", n)

count(3)
```

Output:
```
Before: 3
Before: 2
Before: 1
After: 1
After: 2
After: 3
```
The function calls are added to the stack like this:
```
Top of stack
------------
count(0)
count(1)
count(2)
count(3)
------------
Bottom of stack
```

`count(0)` was the last call added, so it finishes first.

Then Python goes back to `count(1)`, then `count(2)`, then `count(3)`.

This is why recursion often feels like it goes “down” first, then comes back “up.”


## Recursion with Return Values
The Countdown example used recursion to print values but recursive functions can also return values.

```python
def sum_to(n):
  if n == 1: #Base Case
    return 1
  else:
    return n + sum_to(n - 1) #Recursive Case

print(sum_to(5)) #Initial Function Call
```

Output:
```
15
```

### What does this calculate?

5 + 4 + 3 + 2 + 1 = 15

### Trace
```
sum_to(5)
= 5 + sum_to(4)
= 5 + 4 + sum_to(3)
= 5 + 4 + 3 + sum_to(2)
= 5 + 4 + 3 + 2 + sum_to(1)
= 5 + 4 + 3 + 2 + 1
= 15
```

## Recursion with Strings
Recursion is not only for numbers.

```python
def print_letters(word):
  if word == "": #Base Case
    return
  else:
    print(word[0])
    print_letters(word[1:]) #Recursive Case

print_letters("cat") #Initial Function Call
```
Output
```
c
a
t
```
### What is happening?
```python
print_letters("cat")
print_letters("at")
print_letters("t")
print_letters("")
```

## Recursion vs Loops
Many recursive problems can also be solved with loops. 

### Loop version
```python
def sum_to(n):
  total = 0
  for i in range(1, n + 1):
    total += i
  return total

print(sum_to(5))
```
### Recursive version
```python
def sum_to(n):
  if n == 1:
    return 1
  else:
    return n + sum_to(n - 1)

print(sum_to(5))
```
Both versions will return `15`.

So why would we use recursion? Well, recursion is useful when a problem naturally breaks into smaller versions of itself.

## How to write a Recursive Function

### Step 1: find the base case
You need to find the smallest/easiest version of the problem that does not need recursion.

### Step 2: decide how the problem gets smaller
A reduction of some sort that gets you closer to the base case.

Examples:
```python
n - 1
words[1:]
```

### Step 3: call the function again
Once the base case has been established, you need to set the recursion case so the function calls itself using the smaller problem.

### Step 4: combine the result
What are you going to do with the result from the smaller problem? 
```python
return n + sum_to(n - 1)
```

## Other Examples of Recursion

### Sum of a List
```python
def sum_list(numbers):
  if len(numbers) == 0: #Base case
    return 0
  else:
    return numbers[0] + sum_list(numbers[1:]) #Recursive Case

print(sum_list([1, 2, 3, 4, 5])) #Initial Function Call
```
Output: `15`

### Reverse a String
```python
def reverse_string(s):
  if len(s) == 0: #Base case
    return ""
  else:
    return reverse_string(s[1:]) + s[0] #Recursive Case

print(reverse_string("hello")) #Initial Function Call
```
Output: `"olleh"`

### Factorial of a Number
```python
def factorial(n):
  if n == 0 or n == 1: #Base Case
    return 1
  else:
    return n * factorial(n - 1) #Recursive Case

print(factorial(5)) #Initial Function Call
```
Output: `120`

### Fibonacci Sequence
```python
def fibonacci(n):
  if n == 0 or n == 1: #Base Case
    return n
  else:
    return fibonacci(n - 1) + fibonacci(n - 2) #Recursive Case

print(fibonacci(6)) #Initial Function Call
```
Output: `8`

## Common Mistakes

### Mistake 1: No Base Case
```python
def countdown(n):
  print(n)
  countdown(n - 1)
```
This function never stops because there is no base case.

### Mistake 2: Moving Away from the Base Case
```python
def countdown(n):
  if n == 0:
    return

  print(n)
  countdown(n + 1)
```
This function has a base case, but it never reaches it because n keeps getting larger.

### Mistake 3: Forgetting to Return

Incorrect:
```python
def factorial(n):
  if n == 0:
    return 1

  n * factorial(n - 1)
```
Correct:
```python
def factorial(n):
  if n == 0:
    return 1

  return n * factorial(n - 1)
```
If a recursive function is calculating something, the recursive result usually needs to be returned.