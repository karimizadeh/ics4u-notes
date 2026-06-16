# Web Development - HTML Basics

A website is made of files that are loaded by a web browser. The browser reads the files and displays the page for the user.

Front-end web development focuses on what happens in the browser. The main front-end technologies are:

| Technology | Role | Simple Description |
|---|---|---|
| HTML | Structure and content | What appears on the page |
| CSS | Style and layout | How the page looks |
| JavaScript | Behaviour and interactivity | What the page does |
| DOM | Page representation | How JavaScript accesses and changes the page |

A useful way to describe this is:

- **HTML** is the skeleton.
- **CSS** is the appearance.
- **JavaScript** is the behaviour.
- **The DOM** is the browser's live model of the page.

## Client and Server

Most websites use a client-server model.

- The **client** is the user's browser.
- The **server** is the computer that stores and sends the website files.
- The browser sends a request.
- The server sends back files such as HTML, CSS, JavaScript, images, and data.

For this unit, students will focus mainly on **client-side development**, meaning the code runs in the browser.

## Developer Tools

Students should become comfortable using browser developer tools.

Useful tools include:

- **Elements/Inspector:** view HTML and CSS.
- **Console:** see JavaScript output and error messages.
- **Sources:** view loaded files.
- **Network:** see which files were requested by the browser.

## Mini Demonstration

Create three files:

```text
website-demo/
├── index.html
├── css/
│   └── style.css
└── js/
    └── script.js
```

Show that each file has a different job:

```html
<!-- index.html -->
<h1>Hello Web</h1>
<p>This is my first web page.</p>
```

```css
/* css/style.css */
h1 {
    color: darkblue;
}
```

```javascript
// js/script.js
console.log("JavaScript is connected.");
```

## What is HTML?

HTML stands for **HyperText Markup Language**. It is used to define the structure and content of a web page.

HTML uses **elements**. Most elements have:

- an opening tag,
- content,
- and a closing tag.

Example:

```html
<p>This is a paragraph.</p>
```

In this example:

- `<p>` is the opening tag.
- `This is a paragraph.` is the content.
- `</p>` is the closing tag.
- The whole thing is the paragraph element.

Some HTML elements are empty, meaning they do not wrap around content.

Example:

```html
<img src="image.jpg" alt="Description of image">
```

## Basic HTML5 Template

Every page should start with a proper HTML5 structure.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Website</title>
    <link rel="stylesheet" href="css/style.css">
    <script src="js/script.js" defer></script>
</head>
<body>
    <h1>My Website</h1>
    <p>Welcome to my page.</p>
</body>
</html>
```

## Important Parts

| Code | Purpose |
|---|---|
| `<!DOCTYPE html>` | Tells the browser this is an HTML5 document |
| `<html lang="en">` | Starts the HTML page and identifies the language |
| `<head>` | Contains information about the page |
| `<meta charset="UTF-8">` | Allows many characters and symbols to display correctly |
| `<meta name="viewport">` | Helps pages display properly on different screen sizes |
| `<title>` | Sets the browser tab title |
| `<link>` | Connects the CSS file |
| `<script>` | Connects the JavaScript file |
| `<body>` | Contains the visible page content |

## Attributes

Attributes provide extra information about an element.

Example:

```html
<a href="about.html">About Me</a>
```

Here, `href` is an attribute. It tells the link where to go.

Common attributes include:

| Attribute | Used For |
|---|---|
| `id` | A unique name for one element |
| `class` | A reusable group name for styling or JavaScript |
| `href` | Link destination |
| `src` | File path for images or scripts |
| `alt` | Text description for an image |
| `title` | Extra tooltip information |

## Good HTML Habits

Students should:

- use lowercase tag names,
- close elements properly,
- indent nested elements,
- use meaningful file names,
- use descriptive image `alt` text,
- validate their HTML,
- separate HTML, CSS, and JavaScript into different files.

## Headings

Headings organize content.

```html
<h1>Main Page Title</h1>
<h2>Section Title</h2>
<h3>Subsection Title</h3>
```

Use headings in order. Avoid jumping from `<h1>` directly to `<h4>` just because of size. CSS should control appearance; HTML should control meaning.

## Paragraphs

```html
<p>This is a paragraph of text.</p>
```

## Lists

Unordered list:

```html
<ul>
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ul>
```

Ordered list:

```html
<ol>
    <li>Plan the page.</li>
    <li>Write the HTML.</li>
    <li>Style with CSS.</li>
</ol>
```

## Links

Links use the `<a>` element.

```html
<a href="about.html">About</a>
<a href="https://www.example.com">Visit Example</a>
```

For a multi-page website, students should use relative links:

```html
<a href="index.html">Home</a>
<a href="about.html">About</a>
<a href="contact.html">Contact</a>
```

## Images

Images use the `<img>` element.

```html
<img src="images/logo.png" alt="Website logo">
```

The `alt` attribute is important because it:

- supports accessibility,
- displays if the image cannot load,
- helps screen readers describe the image.

## Figures and Captions

When an image needs a caption, use `<figure>` and `<figcaption>`.

```html
<figure>
    <img src="images/project.jpg" alt="Student web project screenshot">
    <figcaption>My final website homepage design.</figcaption>
</figure>
```

## Tables

Tables should be used for tabular data, not page layout.

```html
<table>
    <caption>Project Timeline</caption>
    <thead>
        <tr>
            <th>Task</th>
            <th>Due Date</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Website Plan</td>
            <td>Friday</td>
        </tr>
        <tr>
            <td>Final Website</td>
            <td>Next Friday</td>
        </tr>
    </tbody>
</table>
```

## What is Semantic HTML?

Semantic HTML means using elements that describe the meaning of the content.

Instead of using only `<div>` elements, students should use meaningful structure where possible.

Common semantic elements:

| Element | Purpose |
|---|---|
| `<header>` | Introductory content, logo, title, top navigation |
| `<nav>` | Navigation links |
| `<main>` | Main content of the page |
| `<section>` | A themed section of content |
| `<article>` | A self-contained piece of content |
| `<aside>` | Related side content |
| `<footer>` | Footer information |

## Example Page Structure

```html
<body>
    <header>
        <h1>My Portfolio</h1>
        <nav>
            <ul>
                <li><a href="index.html">Home</a></li>
                <li><a href="projects.html">Projects</a></li>
                <li><a href="contact.html">Contact</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section>
            <h2>Welcome</h2>
            <p>This website shows my work in computer science.</p>
        </section>
    </main>

    <footer>
        <p>&copy; 2026 My Name</p>
    </footer>
</body>
```

## Planning a Website

Before coding, students should plan:

- What is the purpose of the website?
- Who is the audience?
- How many pages will it have?
- What are the file names?
- What content belongs on each page?
- What images or media are needed?
- What JavaScript interaction will be included?
- What form will be included?

## Suggested Folder Structure

```text
final-website/
├── index.html
├── about.html
├── gallery.html
├── contact.html
├── css/
│   └── style.css
├── js/
│   └── script.js
└── images/
    ├── logo.png
    └── banner.jpg
```

## Template Strategy

A good workflow is:

1. Create `template.html`.
2. Add the basic HTML structure.
3. Connect the CSS and JavaScript files.
4. Add a header, navigation, main area, and footer.
5. Copy the template to create each page.
6. Rename each file.
7. Change the page-specific content.

This helps ensure all pages have a consistent layout.

