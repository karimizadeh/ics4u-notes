# Web Development - HTML Basics

## The Internet vs. the Web

The **Internet** is a global network of connected computers.

The **World Wide Web** is one service that runs on the Internet. It uses web pages, hyperlinks, browsers, servers, and HTTP/HTTPS.

A simple way to explain it:

> The Internet is the road system.  
> The Web is one kind of traffic that travels on those roads.

Other Internet services include email, file transfer, messaging, and online games.

## Front-End Web Development

In this unit, we are focusing on **front-end web development**.

Front-end code runs in the user’s browser.

The main parts are:

| Technology | Purpose |
|---|---|
| HTML | Structure and content |
| CSS | Appearance and layout |
| JavaScript | Behaviour and interactivity |
| DOM | The browser’s live version of the page that JavaScript can change |

A useful shortcut:

> HTML is the content.  
> CSS is the design.  
> JavaScript is the behaviour.

## URLs

A **URL** is the address of a web resource.

Example:

```text
https://example.com/about.html
```

Parts of a URL:

| Part | Example | Meaning |
|---|---|---|
| Protocol | `https://` | How the browser communicates |
| Domain | `example.com` | The server name |
| Path | `/about.html` | The file or resource being requested |

For local projects, students may open files directly or use a simple local server.

## HTML

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

## Browser Developer Tools

Students should learn early that errors are normal.

Developer tools help students:

- Inspect HTML
- Test CSS changes
- View JavaScript errors
- Use the console
- Debug broken links or images

Common shortcut:

```text
Right-click page → Inspect
```

or

```text
F12
```

On many browsers, the console is found under the **Console** tab.

## Folder Setup

Recommended folder structure:

```text
my-website/
│
├── index.html
├── about.html
├── gallery.html
├── contact.html
│
├── css/
│   └── styles.css
│
├── js/
│   └── script.js
│
└── images/
    └── example.jpg
```

### Why organize files this way?

- HTML files stay in the main folder
- CSS files go in a `css` folder
- JavaScript files go in a `js` folder
- Images go in an `images` folder
- It is easier to debug broken links and missing files


## Mini Task

Create a folder called `web-unit-practice`.

Inside it, create three files:

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

In this example:

- `a` is the tag
- `href` is the attribute
- `https://www.example.com` is the attribute value

Another example:

```html
<img src="images/logo.png" alt="School logo">
```

The `alt` attribute is important because it describes the image for users who cannot see it and for cases where the image does not load.

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

## Common HTML Elements

### Headings

Headings organize content.

```html
<h1>Main Page Title</h1>
<h2>Section Title</h2>
<h3>Subsection Title</h3>
```

Use headings in order. Avoid jumping from `<h1>` directly to `<h4>` just because of size. CSS should control appearance; HTML should control meaning.

### Paragraphs

```html
<p>This is a paragraph of text.</p>
```

### Lists

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

### Hyperlinks

Links are created using the `<a>` element.

```html
<a href="about.html">About</a>
```

The `href` attribute tells the browser where to go.

For a multi-page website, students should use relative links:

```html
<a href="index.html">Home</a>
<a href="about.html">About</a>
<a href="contact.html">Contact</a>
```

### Internal Page Links

To link to a section on the same page, use an `id`.

```html
<a href="#contact">Go to Contact Section</a>

<section id="contact">
    <h2>Contact</h2>
</section>
```


### External Links

To link to another website:

```html
<a href="https://www.wikipedia.org">Wikipedia</a>
```

To open in a new tab:

```html
<a href="https://www.wikipedia.org" target="_blank">Wikipedia</a>
```

When using `target="_blank"`, it is good practice to add:

```html
rel="noopener noreferrer"
```

Full example:

```html
<a href="https://www.wikipedia.org" target="_blank" rel="noopener noreferrer">
    Wikipedia
</a>
```

### Images

Images use the `<img>` element. The `img` element is an empty element, meaning it does not have a closing tag.

```html
<img src="images/logo.png" alt="Website logo">
```

| Attribute | Purpose |
|---|---|
| `src` | Path to the image file |
| `alt` | Text description of the image |

### Figures and Captions

When an image needs a caption, use `<figure>` and `<figcaption>`.

```html
<figure>
    <img src="images/project.jpg" alt="Student web project screenshot">
    <figcaption>My final website homepage design.</figcaption>
</figure>
```

### Tables

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

### Div and Span

Sometimes there is no semantic element that fits.

Use:

```html
<div>
```

for a generic block container.

Use:

```html
<span>
```

for a generic inline container.

Example:

```html
<p>This word is <span class="highlight">important</span>.</p>
```

Use semantic elements when possible. Use `div` and `span` when you need a generic container for styling or JavaScript.

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

