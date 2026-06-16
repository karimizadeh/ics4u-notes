# Web Development - CSS

CSS stands for **Cascading Style Sheets**. CSS controls how HTML appears on the page.

HTML controls content and structure. CSS controls presentation.

Example:

```css
body {
    font-family: Arial, sans-serif;
    background-color: #f5f5f5;
    color: #222222;
}
```

## Three Ways to Add CSS

CSS can be added in three ways:

| Method | Example | Recommendation |
|---|---|---|
| Inline | `<p style="color: red;">Text</p>` | Avoid for full websites |
| Internal | `<style>` inside HTML | Useful for quick testing |
| External | Separate `.css` file | Best for this unit |

Students should use **external CSS**.

```html
<link rel="stylesheet" href="css/style.css">
```

## CSS Rule Structure

```css
selector {
    property: value;
}
```

Example:

```css
h1 {
    color: navy;
    text-align: center;
}
```

- `h1` is the selector.
- `color` and `text-align` are properties.
- `navy` and `center` are values.

## Common CSS Properties

| Property | Purpose |
|---|---|
| `color` | Text colour |
| `background-color` | Background colour |
| `font-family` | Font choice |
| `font-size` | Text size |
| `text-align` | Text alignment |
| `width` | Element width |
| `height` | Element height |
| `margin` | Space outside an element |
| `padding` | Space inside an element |
| `border` | Border around an element |
| `border-radius` | Rounded corners |

## Starter CSS File

```css
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: Arial, sans-serif;
    line-height: 1.6;
    background-color: #f5f5f5;
    color: #222222;
}

header, main, footer {
    max-width: 1000px;
    margin: 0 auto;
    padding: 1rem;
}

img {
    max-width: 100%;
    height: auto;
}
```

## Element Selectors

Element selectors style every element of that type.

```css
p {
    font-size: 1rem;
}
```

This affects all `<p>` elements.

## Class Selectors

Classes are reusable. Multiple elements can share the same class.

HTML:

```html
<p class="highlight">Important text.</p>
<p class="highlight">Another important note.</p>
```

CSS:

```css
.highlight {
    background-color: yellow;
    padding: 0.5rem;
}
```

## ID Selectors

An ID should be unique on a page.

HTML:

```html
<section id="intro">
    <h2>Introduction</h2>
</section>
```

CSS:

```css
#intro {
    border: 2px solid black;
}
```

## Grouping Selectors

Use grouping to apply the same rule to multiple selectors.

```css
h1, h2, h3 {
    font-family: Georgia, serif;
}
```

## Contextual Selectors

Contextual selectors target elements inside other elements.

```css
nav a {
    text-decoration: none;
}
```

This targets links inside a `<nav>`.

## Pseudo-Classes

Pseudo-classes style elements in a specific state.

```css
a:hover {
    text-decoration: underline;
}

button:hover {
    cursor: pointer;
}
```

## Specificity

When two CSS rules target the same element, the browser decides which rule wins. A simple way to explain specificity:

```text
inline style > id selector > class selector > element selector > browser default
```

For this unit, students should avoid inline styles and rely mostly on classes.

## Text Styling

```css
h1 {
    font-size: 2.5rem;
    text-align: center;
    letter-spacing: 1px;
}

p {
    line-height: 1.6;
}
```

## Colour Formats

CSS colours can be written using:

```css
h1 {
    color: navy;
}

.card {
    background-color: #ffffff;
}

.warning {
    color: rgb(180, 0, 0);
}
```

Common formats:

- named colours, such as `blue`, `black`, `white`, `navy`
- hexadecimal colours, such as `#ffffff`
- RGB colours, such as `rgb(255, 255, 255)`

## The Box Model

Every HTML element can be thought of as a box.

From inside to outside, the box contains:

```text
content → padding → border → margin
```

| Part | Meaning |
|---|---|
| Content | The text, image, or other content inside the element |
| Padding | Space between the content and the border |
| Border | A line around the padding/content |
| Margin | Space outside the element |

## Example

```css
.card {
    background-color: white;
    padding: 1rem;
    border: 1px solid #cccccc;
    margin-bottom: 1rem;
    border-radius: 8px;
}
```

## Margin vs Padding

Use **padding** when you want space inside the box.

Use **margin** when you want space between boxes.

## Shorthand

CSS shorthand can reduce repeated code.

```css
.box {
    margin: 10px 20px 10px 20px;
}
```

The order is:

```text
top right bottom left
```

Example:

```css
.box {
    margin: 1rem auto;
}
```

This means:

- top and bottom margin: `1rem`
- left and right margin: `auto`

This is often used to centre a block element.

## Width and Max-Width

```css
main {
    max-width: 1000px;
    margin: 0 auto;
    padding: 1rem;
}
```

This keeps content readable on large screens while still allowing it to shrink on smaller screens.

## Basic Card Layout

HTML:

```html
<section class="cards">
    <article class="card">
        <h2>Project One</h2>
        <p>A short project description.</p>
    </article>

    <article class="card">
        <h2>Project Two</h2>
        <p>Another short project description.</p>
    </article>
</section>
```

CSS:

```css
.cards {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
}

.card {
    flex: 1 1 250px;
    background-color: white;
    padding: 1rem;
    border: 1px solid #dddddd;
    border-radius: 8px;
}
```

## Navigation with Lists

Navigation menus are often written as lists of links.

```html
<nav>
    <ul>
        <li><a href="index.html">Home</a></li>
        <li><a href="about.html">About</a></li>
        <li><a href="projects.html">Projects</a></li>
        <li><a href="contact.html">Contact</a></li>
    </ul>
</nav>
```

## Styling Navigation

```css
nav ul {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    gap: 1rem;
    justify-content: center;
}

nav a {
    display: block;
    padding: 0.75rem 1rem;
    text-decoration: none;
    color: white;
    background-color: #333333;
    border-radius: 6px;
}

nav a:hover {
    background-color: #555555;
}
```

## Consistency Across Pages

All pages in a website should have the same:

- navigation menu,
- header style,
- footer style,
- colour scheme,
- font choices,
- spacing system.

## Active Page Styling

Students can add a class to show the current page.

```html
<a class="active" href="projects.html">Projects</a>
```

```css
nav a.active {
    background-color: #0066cc;
}
```

## Page Layout Example

```html
<header>
    <h1>My Website</h1>
    <nav>
        <ul>
            <li><a href="index.html">Home</a></li>
            <li><a href="about.html">About</a></li>
            <li><a href="projects.html">Projects</a></li>
            <li><a href="contact.html">Contact</a></li>
        </ul>
    </nav>
</header>

<main>
    <h2>Page Title</h2>
    <p>Page content goes here.</p>
</main>

<footer>
    <p>&copy; 2026 My Name</p>
</footer>
```

## File Path Reminder

If the HTML file is in the main folder and images are in an `images` folder:

```html
<img src="images/photo.jpg" alt="Description">
```

If the CSS file is inside a `css` folder and needs to access an image in the `images` folder:

```css
.hero {
    background-image: url("../images/banner.jpg");
}
```

The `..` means “go up one folder.”



