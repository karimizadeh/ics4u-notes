# Recursion in Python

## What is Recursion?
To put it simply, recursion is when a function calls itself. It is a technique that solves a problem by breaking it into smaller versions of the same problem.

Recursion is like asking the next person to solve a smaller version of the same problem, until someone reaches the easiest possible case.

or

To clean a stack of plates, you clean the top plate, then clean the rest of the stack.

## How Recursion Works
* Base Case: the condition that stops the recursion. Without a Base Case, the function would call itself indefinitely, leading to a stack overflow (i.e., running out of memory).
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
The function keeps calling itself because it has no Base Case. Eventually, Python will stop the program and give an error: ``` RecursionError: maximum recursion depth exceeded```

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
The function starts with ```n = 5``` and each time the function runs, it prints the current number and then calls itself with a smaller number:

```python
countdown(5)
countdown(4)
countdown(3)
countdown(2)
countdown(1)
countdown(0)
```

When ```n == 0```, the function stops called itself.

## Tracing Recursive Calls
When a recursive function runs, Python places each ```call``` onto the ```call stack```. The ```call stack``` has to remember each unfinished function calls.
TLDR: The call stack keeps track of functions that are currently running but not finished yet. It follows LIFO (Last In, First Out).

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
The function stops when ```n == 0```.

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
Both versions will return ```15```.

So why would we use recursion? Well, recursion is useful when a problem naturally breaks into smaller versions of itself.

## How to write a Recursive Function

### Step 1: find the base case
You need to find the smallest/easiest version of the problem that does not need recursion.

### Step 2: decide how the problem gets smaller
A deduction of some sort that gets you closer to the base case.

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
