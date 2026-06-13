# Files

Most programs need to remember information after the program ends. Variables, lists, and dictionaries only store data while the program is running. Files allow a program to save information permanently and load it again later.

File handling is used in many real applications, including:

* saving user settings
* loading game data
* storing usernames or scores
* reading data from a spreadsheet or CSV file
* writing logs or reports
* processing large amounts of text


Without files, a program forgets everything when it stops running.

For example, this program stores a name in a variable:

```python
name = "Marie"
print(name)
```

Once the program ends, the value of `name` is gone. If we want to save the name for later, we need to write it to a file.

Files help programs move from being temporary to being more realistic and useful.



## File Names and File Paths

A **file name** is the name of the file, such as:

```text
students.txt
scores.csv
settings.txt
```

A **file path** tells Python where to find the file.

If the file is in the same folder as your Python program, you can usually just use the file name:

```python
open("students.txt", "r")
```

If the file is inside another folder, you need to include the folder name:

```python
open("data/students.txt", "r")
```

A common beginner mistake is trying to open a file that is not in the same folder as the Python file.



## Opening a File

Before Python can read from or write to a file, the file must be opened.

The basic syntax is:

```python
file = open("filename", "mode")
```

Example:

```python
file = open("myfile.txt", "r")
```

In this example:

* `"myfile.txt"` is the file name.
* `"r"` is the mode.
* `file` is the variable that lets us work with the opened file.



## Common File Modes

| Mode | Name | What it does | Important warning |
|---|---|---|---|
| `"r"` | Read | Opens a file for reading. | The file must already exist. |
| `"w"` | Write | Creates a new file or overwrites an existing file. | Existing content is erased. |
| `"a"` | Append | Adds new content to the end of a file. | Existing content is kept. |
| `"r+"` | Read and write | Opens a file for both reading and writing. | The file must already exist. |

### Important Difference: Write vs Append

This is one of the most important ideas in file handling.

Using `"w"` mode erases the old file content:

```python
file = open("notes.txt", "w")
```

Using `"a"` mode keeps the old content and adds new content to the end:

```python
file = open("notes.txt", "a")
```

Use `"w"` when you want to replace the file. Use `"a"` when you want to add to the file.



## Reading an Entire File

To read a file, open it in read mode using `"r"`.

```python
file = open("example.txt", "r")
content = file.read()
print(content)
file.close()
```

### What the Code Does

1. Opens `example.txt` in read mode.
2. Reads the entire file as one string.
3. Prints the file contents.
4. Closes the file.

### Important Note

`file.read()` reads the whole file at once. This is simple and useful for small files. For larger files, reading line by line is often better.



## Reading a File Line by Line

Sometimes you do not want the entire file at once. You may want to process one line at a time.

```python
file = open("example.txt", "r")

for line in file:
    print(line.strip())

file.close()
```

### Why Use `strip()`?

When Python reads a line from a file, the line often includes the newline character `\n` at the end.

For example, the file might contain:

```text
apple
banana
cherry
```

Python may read each line like this:

```python
"apple\n"
"banana\n"
"cherry\n"
```

The `strip()` method removes extra whitespace from the beginning and end of a string, including newline characters.

```python
line.strip()
```

This makes the output cleaner.



## Writing to a File

Writing means saving information into a file.

```python
file = open("simple_example.txt", "w")
file.write("Hello, this is a simple file example.\n")
file.write("Writing and reading files in Python is useful.\n")
file.close()
```

### What the Code Does

1. Opens `simple_example.txt` in write mode.
2. Writes the first line.
3. Writes the second line.
4. Closes the file.

### Why Use `\n`?

The `write()` method does not automatically move to a new line.

This code:

```python
file.write("Hello")
file.write("World")
```

writes:

```text
HelloWorld
```

This code:

```python
file.write("Hello\n")
file.write("World\n")
```

writes:

```text
Hello
World
```



## Reading Back What You Wrote

A common pattern is to write data to a file, close it, then open it again to read the data back.

```python
file = open("simple_example.txt", "w")
file.write("Hello, this is a simple file example.\n")
file.write("Writing and reading files in Python is useful.\n")
file.close()

file = open("simple_example.txt", "r")
content = file.read()
print(content)
file.close()
```

This helps confirm that the file was written correctly.



## Appending to a File

Appending means adding new content to the end of a file without deleting what is already there.

```python
file = open("journal.txt", "a")
file.write("Today I learned about file handling.\n")
file.close()
```

If the file already has content, the new line is added at the end.

### Example: Appending Multiple Lines

```python
file = open("journal.txt", "a")
file.write("This is the first line being appended.\n")
file.write("Appending more content to the file.\n")
file.close()
```

Then read the file:

```python
file = open("journal.txt", "r")

for line in file:
    print(line.strip())

file.close()
```



## The Problem with Forgetting to Close a File

When you open a file, the computer reserves resources for it. If you forget to close the file, the program may still work sometimes, but it is not good practice.

Forgetting to close files can cause problems such as:
* data not being saved properly
* files being locked by the program
* wasted system resources
* confusing bugs

This is why Python programmers usually use the `with` statement.



## Better Practice: Using `with open(...)`

The `with` statement automatically closes the file when the block of code is finished.

```python
with open("myfile.txt", "r") as file:
    content = file.read()
    print(content)
```

You do not need to write:

```python
file.close()
```

Python handles it automatically.

### Writing with `with open(...)`

```python
with open("notes.txt", "w") as file:
    file.write("This file was written using with open.\n")
```

### Appending with `with open(...)`

```python
with open("notes.txt", "a") as file:
    file.write("This line was added later.\n")
```

### Recommended Habit

For most beginner programs, use `with open(...)` instead of manually opening and closing files.

## Handling File Errors

If you try to read a file that does not exist, Python will give an error.

```python
file = open("missing.txt", "r")
```

This causes a `FileNotFoundError`.

A safer version uses `try` and `except`:

```python
try:
    with open("missing.txt", "r") as file:
        content = file.read()
        print(content)
except FileNotFoundError:
    print("File not found. Please check the file name and location.")
```

This prevents the program from crashing and gives the user a clearer message.

## Reading Data into a List

A useful pattern is reading each line of a file into a list.

Suppose `names.txt` contains:

```text
David
Eric
Dylan
Mitchell
```

You can read it into a list like this:

```python
names = []

with open("names.txt", "r") as file:
    for line in file:
        names.append(line.strip())

print(names)
```

Output:

```python
['David', 'Eric', 'Dylan', 'Mitchell']
```

This is useful when a program needs to store file data in a collection and then process it.

## Writing a List to a File

You can also take data from a list and write it to a file.

```python
names = ["David", "Eric", "Dylan", "Mitchell"]

with open("names.txt", "w") as file:
    for name in names:
        file.write(name + "\n")
```

Each name is written on its own line.


## Example: Saving Scores

This example asks a user for a name and score, then appends the result to a file.

```python
name = input("Enter your name: ")
score = input("Enter your score: ")

with open("scores.txt", "a") as file:
    file.write(name + ": " + score + "\n")

print("Score saved.")
```

If the program runs multiple times, each new score is added to the end of the file.

## CSV Files

A CSV file stores data in rows and columns. CSV stands for **comma-separated values**.

Example CSV file:

```csv
Name,Age,Occupation
Helen,28,Engineer
Fred,34,Videographer
Marie,25,Teacher
```

CSV files are useful because they can be opened by spreadsheet programs and processed by Python.

## Writing to a CSV File

Python has a built-in `csv` module for working with CSV files.

```python
import csv

data = [
    ["Name", "Age", "Occupation"],
    ["Helen", 28, "Engineer"],
    ["Fred", 34, "Videographer"],
    ["Marie", 25, "Teacher"]
]

with open("people.csv", "w", newline="") as file:
    writer = csv.writer(file)
    writer.writerows(data)
```

### What the Code Does

1. Imports the `csv` module.
2. Creates a list of lists.
3. Opens a file called `people.csv` in write mode.
4. Creates a CSV writer.
5. Writes all rows into the file.

### Why Use `newline=""`?

When writing CSV files, `newline=""` helps prevent extra blank lines from appearing on some systems.

## Reading from a CSV File

```python
import csv

with open("people.csv", "r") as file:
    reader = csv.reader(file)

    for row in reader:
        print(row)
```

Output:

```python
['Name', 'Age', 'Occupation']
['Helen', '28', 'Engineer']
['Fred', '34', 'Videographer']
['Marie', '25', 'Teacher']
```

Notice that CSV values are read as strings. Even though the ages were written as numbers, they are read back as text.

If you need to use age as a number, convert it:

```python
age = int(row[1])
```

## Reading CSV Data with Headers

Sometimes you want to skip the header row.

```python
import csv

with open("people.csv", "r") as file:
    reader = csv.reader(file)
    header = next(reader)

    for row in reader:
        name = row[0]
        age = int(row[1])
        occupation = row[2]

        print(name, age, occupation)
```

`next(reader)` reads the first row before the loop starts. In this example, it stores the header row so the loop only processes the actual data.

## Common Mistakes

### Mistake 1: Forgetting the File Extension

Wrong:

```python
open("students", "r")
```

Better:

```python
open("students.txt", "r")
```

Unless the file really has no extension, include `.txt`, `.csv`, or the correct file type.

### Mistake 2: File Is in the Wrong Folder

If Python says the file does not exist, check that the file is in the same folder as the Python program or use the correct path.

### Mistake 3: Using Write Mode by Accident

This erases the old file:

```python
open("scores.txt", "w")
```

Use append mode if you want to keep old data:

```python
open("scores.txt", "a")
```

### Mistake 4: Forgetting Newline Characters

Wrong:

```python
file.write("First")
file.write("Second")
```

Output:

```text
FirstSecond
```

Better:

```python
file.write("First\n")
file.write("Second\n")
```

### Mistake 5: Not Converting Data Types

Data read from a text file is usually a string.

```python
score = "85"
```

If you need to do math, convert it:

```python
score = int(score)
```
