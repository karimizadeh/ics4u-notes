# Web Development - CSS Basics

CSS stands for **Cascading Style Sheets**. CSS controls how HTML appears on the page.

HTML controls content and structure. CSS controls presentation.

HTML answers:

> What content is on the page?

CSS answers:

> What should it look like?

Example:

```css
body {
    font-family: Arial, sans-serif;
    background-color: #f5f5f5;
    color: #222222;
}
```

## Why CSS Matters

Without CSS, most web pages would appear as plain text, images, and links stacked from top to bottom.

CSS helps control:

- colour,
- fonts,
- spacing,
- page layout,
- navigation menus,
- cards and sections,
- responsive design,
- hover effects,
- visual consistency across pages.

CSS should support the HTML. Good CSS makes the content easier to read, use, and understand.


## Three Ways to Add CSS

CSS can be added in three ways:

| Method | Example | Recommendation |
|---|---|---|
| Inline | `<p style="color: red;">Text</p>` | Avoid for full websites |
| Internal | `<style>` inside HTML | Useful for quick testing |
| External | Separate `.css` file | Best for this unit |

Instead of writing styles inside each HTML file, we place styles in a separate `.css` file. You should use **external CSS**.

```html
<link rel="stylesheet" href="css/style.css">
```
This goes inside the `<head>` section.

Benefits of external CSS:

- Keeps HTML cleaner
- Makes the website easier to update
- Allows one CSS file to style multiple pages
- Helps separate structure from design

## The Cascade

CSS is called “cascading” because multiple rules can apply to the same element.

General priority:

1. Inline style
2. Internal style
3. External CSS
4. Browser default style

You should mostly use **external CSS**.

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
    font-size: 18px;
}
```

- `h1` is the selector.
- `color` and `font-size` are properties.
- `navy` and `18px` are values.

This changes all h1 header text to navy and font-size to 18 pixels.

## CSS Comments

```css
/* This is a CSS comment */
```

## Common CSS Properties

| Property | Purpose |
|---|---|
| `color` | Text colour |
| `background-color` | Background colour |
| `font-family` | Font choice |
| `font-size` | Text size |
| `font-weight` | Text thickness |
| `text-align` | Text alignment |
| `line-height` | Space between lines of text |
| `width` | Element width |
| `max-width` | Maximum width an element can grow to |
| `height` | Element height |
| `margin` | Space outside an element |
| `padding` | Space inside an element |
| `border` | Border around an element |
| `border-radius` | Rounded corners |
| `display` | Controls layout behaviour |
| `gap` | Space between flex or grid items |

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

header,
main,
footer {
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

An ID selector targets one unique element.

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
IDs should be unique on the page.

## Grouping Selectors

If multiple elements share the same style, group them with commas.

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

Other useful pseudo-classes:

| Pseudo-class | Meaning |
|---|---|
| `:hover` | Mouse is over the element |
| `:focus` | Element is selected with keyboard or mouse |
| `:active` | Element is currently being clicked |
| `:visited` | Link has already been visited |
| `:first-child` | Element is the first child of its parent |
| `:last-child` | Element is the last child of its parent |

### Focus Styles

Do not remove focus outlines without replacing them. Focus styles help keyboard users know where they are on the page.

```css
a:focus,
button:focus {
    outline: 3px solid #ffbf47;
}
```



## Specificity

When two CSS rules target the same element, the browser decides which rule wins. A simple way to explain specificity:

```text
inline style > id selector > class selector > element selector > browser default
```

You should avoid inline styles and rely mostly on classes.

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

Good text styling improves readability.

Useful tips:

- Use larger text for headings.
- Keep paragraph line height comfortable.
- Avoid using too many different fonts.
- Use enough colour contrast between text and background.

## Units in CSS

CSS has several units.

| Unit | Meaning | Common Use |
|---|---|---|
| `px` | Fixed pixels | Borders, small spacing, precise sizes |
| `%` | Percentage of parent | Flexible widths |
| `rem` | Relative to root font size | Spacing and font sizes |
| `em` | Relative to current element font size | Component-specific spacing |
| `vh` | Percentage of viewport height | Full-screen sections |
| `vw` | Percentage of viewport width | Width based on browser size |

`rem`, `%`, and `max-width` are often better than fixed pixel widths because they respond better to different screen sizes.



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
- RGBA colours, such as `rgba(0, 0, 0, 0.5)`
- HSL colours, such as `hsl(210, 80%, 40%)`


## The CSS Box Model

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

Example:

```css
.card {
    padding: 1rem;
    margin-bottom: 1rem;
}
```

The text inside the card moves away from the edge because of padding. The card moves away from the next card because of margin.


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

## Display

The `display` property controls how an element behaves in the layout.

| Display Value | Meaning |
|---|---|
| `block` | Starts on a new line and takes full available width |
| `inline` | Stays in the same line and only takes needed width |
| `inline-block` | Stays inline but allows width and height |
| `flex` | Uses flexbox layout |
| `grid` | Uses grid layout |
| `none` | Hides the element completely |

Examples:

```css
nav a {
    display: inline-block;
    padding: 0.75rem 1rem;
}
```

```css
.hidden {
    display: none;
}
```



## Width and Max-Width

```css
main {
    max-width: 1000px;
    margin: 0 auto;
    padding: 1rem;
}
```

This keeps content readable on large screens while still allowing it to shrink on smaller screens.

Avoid setting large fixed widths like this:

```css
main {
    width: 1000px;
}
```

A fixed width can cause horizontal scrolling on small screens.



## Centering a Page

A common website layout uses a container.

HTML:

```html
<div class="container">
    <main>
        <h1>Welcome</h1>
    </main>
</div>
```

CSS:

```css
.container {
    max-width: 1000px;
    margin: 0 auto;
    padding: 20px;
}
```
`margin: 0 auto;` centers the container horizontally.

## Flexbox Basics

Flexbox is useful for arranging items in a row or column.

```css
.cards {
    display: flex;
    gap: 1rem;
}
```

By default, flexbox places items in a row.

Useful flexbox properties:

| Property | Purpose |
|---|---|
| `display: flex` | Turns the element into a flex container |
| `gap` | Adds space between flex items |
| `flex-direction` | Sets row or column direction |
| `justify-content` | Controls spacing along the main axis |
| `align-items` | Controls alignment along the cross axis |
| `flex-wrap` | Allows items to wrap onto a new line |
| `flex` | Controls how much an item can grow or shrink |

Example:

```css
.cards {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
}

.card {
    flex: 1 1 250px;
}
```

This allows cards to sit beside each other when there is space and wrap when the screen is smaller.



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

## CSS Grid Basics

CSS Grid is useful for two-dimensional layouts, where you care about rows and columns.

```css
.gallery {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
}
```

This creates three equal columns.

A more responsive version is:

```css
.gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1rem;
}
```

This lets the browser create as many columns as will fit, with each item at least 200px wide.

## Flexbox vs Grid

| Use Flexbox When... | Use Grid When... |
|---|---|
| You are arranging items in one row or one column | You are arranging rows and columns |
| You are spacing navigation links | You are building a gallery |
| You want items to wrap naturally | You want a structured page layout |
| The content size controls the layout | The layout structure controls the content |

You can use flexbox for navigation and cards, and grid for galleries.



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

nav a:hover,
nav a:focus {
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

Add a class to show the current page.

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



