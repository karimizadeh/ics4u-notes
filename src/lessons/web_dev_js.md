# Web Development - JavaScript Basics

JavaScript is a programming language that runs in the browser. It can be used to:

- respond to clicks,
- change text or images,
- show or hide content,
- validate forms,
- create interactive features,
- update styles,
- work with page elements through the DOM (Document Object Model).

JavaScript has **nothing** to do with Java. When JavaScript came out, Java was really popular, so they named it JavaScript to gain popularity.

### JavaScript Resources
* [JavaScript on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
    * [JavaScript Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)
    * [JavaScript Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference)
* [Eloquent JavaScript](https://eloquentjavascript.net/)
* [JavaScript for impatient programmers (ES2022 edition)](https://exploringjs.com/impatient-js/index.html)


## Connecting JavaScript

The recommended approach is to use an external JavaScript file.

```html
<script src="js/script.js" defer></script>
```

The `defer` attribute tells the browser to load the script after reading the HTML structure. This helps prevent JavaScript from trying to access elements before they exist.

## Console Output

```javascript
console.log("JavaScript is working.");
```

The console is useful for testing and debugging.

## Comments

Comments are notes for humans. JavaScript ignores comments when the program runs.

Single-line comment:

```javascript
// This message will appear in the console.
console.log("Hello");
```

Multi-line comment:

```javascript
/*
This is a longer comment.
It can take up more than one line.
*/
```

Comments should explain why something is happening, not just repeat what the code already says.

## Variables

Use `let` for values that may change.

```javascript
let studentName = "Mitchell";
let score = 97;
let isComplete = true;

score = score + 1;
```

Use `const` for values that should not be reassigned.

```javascript
const schoolName = "York Mills CI";
```

Use:

- `let` when the value may change
- `const` when the value should not be reassigned


* JavaScript is dynamic, and variables can change value *and* type at runtime:

```js
let a;             // undefined
a = 6;             // 6, Number
a++;               // 7, Number
a--;               // 6, Number
a += 3;            // 9, Number
a = "Value=" + a;  // "Value=9", String
a = !!a;           // true, Boolean
a = null;          // null
```

|Declaration|Type|Value|
|-----------|----|-----|
|`let s1 = "some text";` |`String`|`"some text"`|
|`let s2 = 'some text';` |`String`|`"some text"` |
|`let s3 = '172';`       |`String`|`"172"`|
|`let s4 = '172' + 4;`   |`String`|`"1724"` (concatenation vs. addition)|
|`let n1 = 172;`         |`Number`|`172` (integer)|
|`let n2 = 172.45;`      |`Number`|`172.45` (double-precision float)|
|`let n3 = 9007199254740993n;`         |`BigInt`|`9007199254740993n` (integer)|
|`let b1 = true;`        |`Boolean`| `true` |
|`let b2 = false;`       |`Boolean`| `false`|
|`let b3 = !b2;`         |`Boolean`| `true` |
|`let s = Symbol("Sym");`         |`symbol`| `Symbol(Sym)` |
|`let c;`                |`undefined`| `undefined`|
|`let d = null;`         |`object`|`null`|


console.log(website.title);

## Common JavaScript Operators

|Operator | Operation | Example |
|---------|-----------|----------|
|`+`      | Addition of `Number`s| `3 + 4` |
|`+`      | Concatenation of `String`s| `"Hello " + "World"`|
|`-`      | Subtraction of `Number`s| `x - y`|
|`*`      | Multiplication of `Number`s| `3 * n`|
|`/`      | Division of `Number`s| `2 / 4`|
|`%`      | Modulo | `7 % 3` (gives 1 remainder)|
|`++`     | Post/Pre Increment| `x++`, `++x`|
|`--`     | Post/Pre Decrement| `x--`, `--x`| 
|`=`      | Assignment | `a = 6`|
|`+=`     | Assignment with addition | `a += 7` same as `a = a + 7`. Can be used to join `String`s too|
|`-=`     | Assignment with subtraction | `a -= 7` same as `a = a - 7`|
|`*=`     | Assignment with multiplication | `a *= 7` same as `a = a * 7`|
|`/=`     | Assignment with division | `a /= 7` same as `a = a / 7`|
|`&&`     | Logical `AND` | `if(x > 3 && x < 10)` both must be `true`|
|`()`     | Call/Create | `()` invokes a function, `f()` means invoke/call function stored in variable `f`|
|<code>&#124;&#124;</code>   | Logical `OR` | <code>if(x === 3 &#124;&#124; x === 10)</code> only one must be `true`|
|<code>&#124;</code>     | Bitwise `OR` | <code>3.1345&#124;0</code> gives `3` as an integer|
|`!`      | Logical `NOT` | `if(!(x === 2))` negates an expression |
|`==`     | Equal | `1 == 1` but also `1 == "1"` due to type coercion|
|`===`    | Strict Equal | `1 === 1` but  `1 === "1"` is not `true` due to types. Prefer `===`|
|`!=`     | Not Equal | `1 != 2`, with type coercion|
|`!==`    | Strict Not Equal | `1 !== "1"`. Prefer `!==`|
|`>`      | Greater Than | `7 > 3` |
|`>=`     | Greater Than Or Equal | `7 >=7` and `7 >= 3`|
|`<`      | Less Than | `3 < 10`|
|`<=`     | Less Than Or Equal | `3 < 10` and `3 <=3` |
|`typeof` | Type Of | `typeof "Hello"` gives `'string'`, `typeof 6` gives `'number'`|
| `cond ? a : b` | Ternary | `status = (age >= 18) ? 'adult' : 'minor';` |

## Expressions
```js
let a = 10 / 2;                       // arithmetic expression
let b = !(10 / 2);                    // logical expression evaluates to false
let c = "10 " + "/" + " 2";           // string, evaluates to "10 / 2"
let f = function() { return 10 / 2;}; // function expression, f can now be called via the () operator
let d = f();                          // f() evaluates to 10/2, or the Number 5
```

## Conditionals

```javascript
let age = 17;

if (age >= 18) {
    console.log("Adult");
} else {
    console.log("Not adult yet");
}
```

```javascript
switch(grade) {
    case 'A+':
        // do these steps if grade is A+
        break;
    case 'A':
        // do these steps if grade is A
        break;
    case 'B':
        // do these steps if grade is B
        break;
    case 'C':
        // do these steps if grade is C
        break;
    case 'D':
        // do these steps if grade is D
        break;
    default:
        // do these steps in any other case
        break;
}
```
## Truthy and Falsy Values in JavaScript

In JavaScript, conditions do not always need to be written as direct comparisons.

For example:

```js
if (isLoggedIn === true) {
    console.log("Welcome!");
}
```
can sometimes be written as:
```js
if (isLoggedIn) {
    console.log("Welcome!");
}
```
This works because JavaScript treats some values as truthy and some values as falsy.

What Does Falsy Mean?

A falsy value is a value that JavaScript treats like false when used in a condition.

These are the common falsy values:
```js
false
0
""
null
undefined
NaN
```

Example:
```js
let username = "";

if (username) {
    console.log("Username entered.");
} else {
    console.log("Username is missing.");
}
```
Output: `Username is missing.`

The empty string `""` is falsy, so the else block runs.

### What Does Truthy Mean?

A truthy value is a value that JavaScript treats like true when used in a condition.

Most values in JavaScript are truthy.

```js
true
1
-1
"hello"
"0"
"false"
[]
{}
```

Important: 
* `"false"` is truthy because it is a non-empty string.
* `"0"` is also truthy because it is a non-empty string.

**Becareful!** Truthy and falsy values are useful, but they can also create confusing bugs.

Instead of:
```js
if (score) {
    console.log("Score entered.");
}
```
Write:
```js
if (score !== "") {
    console.log("Score entered.");
}
```
OR

```js
if (score >= 0) {
    console.log("Valid score.");
}
```

| Value | Truthy or Falsy? |
|---|---|
| `false` | Falsy |
| `0` | Falsy |
| `""` | Falsy |
| `null` | Falsy |
| `undefined` | Falsy |
| `NaN` | Falsy |
| `"hello"` | Truthy |
| `"0"` | Truthy |
| `"false"` | Truthy |
| `1` | Truthy |
| `[]` | Truthy |
| `{}` | Truthy |

## Type Conversion

JavaScript sometimes converts values automatically. This is called **type coercion**.

```javascript
console.log("5" + 2); // "52"
console.log("5" - 2); // 3
```

This can be confusing. When working with form input, remember that values usually come in as strings.

```html
<input id="age" type="number">
```

```javascript
const ageInput = document.querySelector("#age");
const age = Number(ageInput.value);

if (age >= 18) {
    console.log("Adult");
}
```

Common conversion functions:

| Function | Purpose | Example |
|---|---|---|
| `Number(value)` | Convert to a number | `Number("42")` gives `42` |
| `String(value)` | Convert to a string | `String(42)` gives `"42"` |
| `Boolean(value)` | Convert to true/false | `Boolean("")` gives `false` |
| `parseInt(value)` | Convert to an integer | `parseInt("42px")` gives `42` |
| `parseFloat(value)` | Convert to a decimal number | `parseFloat("3.14")` gives `3.14` |


## Loops

Loops are used when a program needs to repeat code.

A loop usually needs three things:

1. a starting value,
2. a condition that controls when the loop should stop,
3. an update that moves the loop toward stopping.

Without a proper stopping condition, a loop can become an **infinite loop**, which means it keeps running forever.

### `for` Loops

A `for` loop is useful when you know how many times something should repeat.

```javascript
let total = 0;

for (let i = 1; i <= 10; i++) {
    total += i;
    console.log("i", i, "total", total);
}
```

The three parts of the loop are:

```javascript
for (starting value; condition; update) {
    // repeated code
}
```

Example:

```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

Output:

```text
0
1
2
3
4
```

Important: `i < 5` stops before 5. This is common because counting in programming often starts at 0.

### Counting Backward

Loops can also count down.

```javascript
for (let countdown = 5; countdown >= 1; countdown--) {
    console.log(countdown);
}

console.log("Blast off!");
```

### Looping Through an Array with an Index

Use this approach when you need the position/index of each item.

```javascript
const pages = ["Home", "About", "Gallery", "Contact"];

for (let i = 0; i < pages.length; i++) {
    console.log(i, pages[i]);
}
```

Output:

```text
0 Home
1 About
2 Gallery
3 Contact
```

### `for...of` Loops

A `for...of` loop is useful when you want each value in an array and do not need the index.

```javascript
const pages = ["Home", "About", "Gallery", "Contact"];

for (const page of pages) {
    console.log(page);
}
```

This reads more naturally than a regular `for` loop, but it does not automatically give you the index number.

### `while` Loops

A `while` loop is useful when you do not know exactly how many times the loop will run.

The loop continues while the condition is true.

```javascript
let password = "";

while (password !== "open") {
    password = prompt("Enter the password:");
}

console.log("Access granted.");
```

A `while` loop checks the condition before running the code inside the loop. If the condition is false at the start, the loop may run zero times.

### `do...while` Loops

A `do...while` loop always runs at least once because the condition is checked after the loop body.

```javascript
let choice;

do {
    choice = prompt("Enter A, B, or C:");
} while (choice !== "A" && choice !== "B" && choice !== "C");

console.log("You chose " + choice);
```

This is useful for menus or input validation where the user should be asked at least one time.

### `break`

`break` immediately stops a loop.

```javascript
const scores = [82, 91, 100, 76, 88];

for (const score of scores) {
    if (score === 100) {
        console.log("Perfect score found!");
        break;
    }

    console.log("Checked", score);
}
```

### `continue`

`continue` skips the rest of the current loop cycle and moves to the next cycle.

```javascript
const scores = [82, -1, 91, -1, 76];

for (const score of scores) {
    if (score === -1) {
        continue;
    }

    console.log("Valid score:", score);
}
```

In this example, `-1` is skipped because it represents missing data.

### Loop Type Summary

| Loop Type | Best Used When | Example Use |
|---|---|---|
| `for` | You know how many times to repeat | Count from 1 to 10 |
| `for...of` | You want each value in a list | Print every page name |
| `while` | You repeat until a condition changes | Keep asking until a password is correct |
| `do...while` | The code must run at least once | Show a menu before checking the choice |

### Common Loop Mistakes

#### Mistake 1: Forgetting to update the loop variable

```javascript
let i = 0;

while (i < 5) {
    console.log(i);
    // missing i++
}
```

This loop never ends because `i` always stays at 0.

#### Mistake 2: Off-by-one errors

```javascript
const names = ["Ava", "Noah", "Mia"];

for (let i = 0; i <= names.length; i++) {
    console.log(names[i]);
}
```

This goes too far. The last valid index is `names.length - 1`.

Corrected version:

```javascript
for (let i = 0; i < names.length; i++) {
    console.log(names[i]);
}
```

#### Mistake 3: Using `for...in` for arrays

`for...in` loops through property names, not values. For beginner array work, use `for`, `for...of`, or array methods instead.

```javascript
const colours = ["red", "green", "blue"];

for (const colour of colours) {
    console.log(colour);
}
```


## Functions

Functions let us group code that can be reused.

```javascript
function greetUser(name) {
    return "Hello, " + name + "!";
}

let message = greetUser("Mitchell");
console.log(message);
```

### Parameters and Arguments

A **parameter** is the variable listed in the function definition.

An **argument** is the actual value sent into the function when it is called.

```javascript
function calculateArea(width, height) {
    return width * height;
}

let area = calculateArea(10, 5);
console.log(area); // 50
```

In this example:

- `width` and `height` are parameters,
- `10` and `5` are arguments,
- `return` sends the answer back to the part of the program that called the function.

### Functions Without Return Values

Some functions do an action but do not return a value.

```javascript
function showError(message) {
    const errorBox = document.querySelector("#error");
    errorBox.textContent = message;
}

showError("Please enter your name.");
```

This function changes the page, but it does not calculate and return a new value.

### Function Scope

Variables created inside a function usually only exist inside that function.

```javascript
function addBonus(score) {
    let bonus = 5;
    return score + bonus;
}

console.log(addBonus(80));
// console.log(bonus); // Error: bonus is not defined outside the function
```

This is called **scope**. Scope helps prevent one part of a program from accidentally changing another part.

### Arrow Functions

JavaScript also has arrow functions. These are often used with event listeners and array methods.

```javascript
const greetUser = (name) => {
    return "Hello, " + name + "!";
};

console.log(greetUser("Mitchell"));
```

For this course, regular `function` syntax is easier when learning the basics. Arrow functions are still useful to recognize because examples online often use them.


## Events

Events happen when the user interacts with the page.

Examples:

- click,
- mouseover,
- keydown,
- input,
- change,
- submit.

Avoid putting JavaScript directly inside HTML when possible.

Instead of this:

```html
<button onclick="sayHello()">Click Me</button>
```

Prefer this:

```html
<button id="helloButton">Click Me</button>
```

```javascript
const button = document.querySelector("#helloButton");

button.addEventListener("click", function () {
    console.log("Hello!");
});
```

This keeps HTML and JavaScript separate.


## Strings

```js
let firstName = "Mitchell";
let message = "Hello, " + firstName;
console.log(message);
```

Template literals are often easier:

```js
let message = `Hello, ${firstName}`;
```


## Arrays

Arrays store lists.

```js
let pages = ["Home", "About", "Gallery", "Contact"];

console.log(pages[0]); // Home
console.log(pages.length); // 4
```

Array indexes start at 0.

| Index | Value |
|---|---|
| `0` | `"Home"` |
| `1` | `"About"` |
| `2` | `"Gallery"` |
| `3` | `"Contact"` |

### Changing Array Items

```javascript
pages[2] = "Photos";
console.log(pages);
```

### Adding and Removing Items

```javascript
pages.push("FAQ");      // adds to the end
pages.pop();             // removes from the end
pages.unshift("Start");  // adds to the beginning
pages.shift();           // removes from the beginning
```

### Checking an Array

```javascript
console.log(pages.includes("Contact")); // true
console.log(pages.indexOf("About"));    // 1
```

### Looping Through an Array

```javascript
for (const page of pages) {
    console.log(page);
}
```

### Array of Objects

Websites often use arrays of objects because each item may need more than one piece of information.

```javascript
const projects = [
    {
        title: "Portfolio Website",
        category: "HTML/CSS"
    },
    {
        title: "Quiz App",
        category: "JavaScript"
    }
];

console.log(projects[0].title); // Portfolio Website
```

This structure is useful when creating cards, galleries, menus, or lists on a webpage.

## Objects

Objects store related data using key-value pairs.

```js
let website = {
    title: "My Portfolio",
    pages: 4,
    hasContactForm: true
};
```

Each key describes one piece of data.

```javascript
console.log(website.title);
console.log(website["pages"]);
```

Dot notation is usually easier to read:

```javascript
website.title = "Updated Portfolio";
website.owner = "Mitchell";

console.log(website);
```

Objects are useful when one thing has multiple related properties.

Example:

```javascript
const student = {
    name: "Ava",
    grade: 11,
    isPassing: true
};
```


## What is the DOM?

OM stands for **Document Object Model**.

When the browser loads an HTML page, it creates a live version of the page that JavaScript can access and change.

HTML is the starting file.

The DOM is the page as it currently exists in the browser.

JavaScript can use the DOM to:

- find elements,
- read content,
- change content,
- change styles,
- add classes,
- remove classes,
- create new elements,
- respond to events.

## Selecting Elements

HTML:

```html
<h1 id="page-title">Welcome</h1>
<p class="intro">This is my website.</p>
```

JavaScript:

```js
const title = document.querySelector("#page-title");
const intro = document.querySelector(".intro");
```

Common selectors:

| Selector | Meaning |
|---|---|
| `"#page-title"` | Element with ID `page-title` |
| `".intro"` | First element with class `intro` |
| `"p"` | First paragraph |
| `"nav a"` | First link inside nav |

To select multiple elements:

```js
const links = document.querySelectorAll("nav a");
```

### `querySelector` vs. `querySelectorAll`

| Method | Returns | Example |
|---|---|---|
| `querySelector()` | The first matching element | `document.querySelector(".card")` |
| `querySelectorAll()` | A list of all matching elements | `document.querySelectorAll(".card")` |

When using `querySelectorAll()`, you often need a loop.

```javascript
const cards = document.querySelectorAll(".card");

for (const card of cards) {
    card.classList.add("highlight");
}
```

### Avoiding `null` Errors

If JavaScript cannot find an element, `querySelector()` returns `null`.

```javascript
const button = document.querySelector("#missingButton");
console.log(button); // null
```

This causes an error:

```javascript
button.textContent = "Click me";
```

Safer version:

```javascript
if (button !== null) {
    button.textContent = "Click me";
}
```

## Reading Content

```javascript
const heading = document.querySelector("h1");
console.log(heading.textContent);
```

## Changing Content

```javascript
const heading = document.querySelector("h1");
heading.textContent = "Welcome to My Website";
```

Use `textContent` when inserting plain text.

Use `innerHTML` only when you intentionally want to insert HTML. For beginners, `textContent` is usually safer.

## Changing CSS with JavaScript

```javascript
const box = document.querySelector(".box");
box.style.backgroundColor = "lightyellow";
```

This works, but for larger changes it is usually cleaner to add or remove a CSS class.

## Adding and Removing Classes

CSS:

```css
.hidden {
    display: none;
}

.highlight {
    background-color: yellow;
}
```

JavaScript:

```javascript
const message = document.querySelector("#message");

message.classList.add("highlight");
message.classList.remove("hidden");
message.classList.toggle("hidden");
```

## Example: Show and Hide Content

HTML:

```html
<button id="toggleButton">Show/Hide Details</button>
<p id="details" class="hidden">These are extra details about the project.</p>
```

CSS:

```css
.hidden {
    display: none;
}
```

JavaScript:

```javascript
const button = document.querySelector("#toggleButton");
const details = document.querySelector("#details");

button.addEventListener("click", function () {
    details.classList.toggle("hidden");
});
```

## Example: Image Gallery Interaction

HTML:

```html
<img id="mainImage" src="images/photo1.jpg" alt="Main gallery image">

<button id="photo1">Photo 1</button>
<button id="photo2">Photo 2</button>
```

JavaScript:

```javascript
const mainImage = document.querySelector("#mainImage");
const photo1Button = document.querySelector("#photo1");
const photo2Button = document.querySelector("#photo2");

photo1Button.addEventListener("click", function () {
    mainImage.src = "images/photo1.jpg";
    mainImage.alt = "First gallery image";
});

photo2Button.addEventListener("click", function () {
    mainImage.src = "images/photo2.jpg";
    mainImage.alt = "Second gallery image";
});
```

## Event Listeners

Slightly different from the Events above. This uses the DOM instead.


HTML:

```html
<button id="theme-button">Change Theme</button>
```

JavaScript:

```js
const button = document.querySelector("#theme-button");

button.addEventListener("click", function() {
    document.body.classList.toggle("dark-theme");
});
```

CSS:

```css
.dark-theme {
    background-color: #222;
    color: white;
}
```

This is better than writing JavaScript directly inside HTML because it separates:

- HTML structure
- CSS style
- JavaScript behaviour

## Creating Elements

JavaScript can create new elements.

```js
const list = document.querySelector("#task-list");

const item = document.createElement("li");
item.textContent = "Finish website homepage";

list.appendChild(item);
```
