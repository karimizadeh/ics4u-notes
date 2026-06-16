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
let score = 0;
score = score + 1;
```

Use `const` for values that should not be reassigned.

```javascript
const schoolName = "York Mills CI";
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

## Functions

Functions let us group code that can be reused.

```javascript
function greetUser(name) {
    return "Hello, " + name + "!";
}

console.log(greetUser("Ava"));
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

## Better Event Handling

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

## What is the DOM?

When a browser loads an HTML page, it creates a live model of the page called the **Document Object Model**, or **DOM**.

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

Select one element:

```javascript
const heading = document.querySelector("h1");
const intro = document.querySelector("#intro");
const firstCard = document.querySelector(".card");
```

Select many elements:

```javascript
const allCards = document.querySelectorAll(".card");
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