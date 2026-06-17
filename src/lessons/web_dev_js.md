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

## Loops
```javascript
let total = 0;
for(let i = 1; i < 11; i++) {
    total += i;
    console.log("i", i, "total", total);
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
# Objects

Objects store related data using key-value pairs.

```js
let website = {
    title: "My Portfolio",
    pages: 4,
    hasContactForm: true
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
