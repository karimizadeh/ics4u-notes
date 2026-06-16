# Web Development - Forms and Validations

## What is a Form?

An HTML form collects user input.

Forms can include:

- text fields,
- email fields,
- password fields,
- radio buttons,
- checkboxes,
- dropdown menus,
- text areas,
- submit buttons.

## Basic Form Structure

```html
<form id="contactForm" action="#" method="post">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name">

    <label for="email">Email:</label>
    <input type="email" id="email" name="email">

    <label for="message">Message:</label>
    <textarea id="message" name="message"></textarea>

    <button type="submit">Send</button>
</form>

<div id="errors"></div>
```

## Labels

Labels make forms easier to use and more accessible.

```html
<label for="email">Email:</label>
<input type="email" id="email" name="email">
```

The `for` value should match the input's `id`.

## Common Input Types

```html
<input type="text">
<input type="email">
<input type="password">
<input type="number">
<input type="date">
<input type="checkbox">
<input type="radio">
<input type="file">
```

## HTML5 Validation Attributes

HTML includes some built-in validation tools.

```html
<input type="text" id="name" name="name" required>
<input type="email" id="email" name="email" required>
<input type="number" id="age" name="age" min="13" max="120">
<input type="text" id="phone" name="phone" pattern="^\d{3}-\d{3}-\d{4}$">
```

Useful attributes:

| Attribute | Purpose |
|---|---|
| `required` | Field must be filled in |
| `min` | Minimum number/date value |
| `max` | Maximum number/date value |
| `maxlength` | Maximum number of characters |
| `pattern` | Regular expression pattern |
| `placeholder` | Hint text inside the field |
| `title` | Extra information about the expected input |

## Why Use JavaScript Validation?

HTML5 validation is helpful, but JavaScript gives more control. With JavaScript, students can:

- display custom error messages,
- check multiple fields together,
- highlight invalid fields,
- stop the form from submitting,
- give immediate feedback.

Important: client-side validation is helpful, but real websites also need server-side validation. For this unit, students only need to implement client-side validation.

## Validation Example

HTML:

```html
<form id="contactForm" action="#" method="post">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name">

    <label for="email">Email:</label>
    <input type="email" id="email" name="email">

    <label for="message">Message:</label>
    <textarea id="message" name="message"></textarea>

    <button type="submit">Send</button>
</form>

<div id="errors"></div>
```

CSS:

```css
.error {
    border: 2px solid red;
}

#errors {
    color: darkred;
    font-weight: bold;
}
```

JavaScript:

```javascript
const form = document.querySelector("#contactForm");
const nameInput = document.querySelector("#name");
const emailInput = document.querySelector("#email");
const messageInput = document.querySelector("#message");
const errors = document.querySelector("#errors");

form.addEventListener("submit", function (event) {
    let errorMessages = [];

    nameInput.classList.remove("error");
    emailInput.classList.remove("error");
    messageInput.classList.remove("error");

    if (nameInput.value.trim() === "") {
        errorMessages.push("Name is required.");
        nameInput.classList.add("error");
    }

    if (emailInput.value.trim() === "") {
        errorMessages.push("Email is required.");
        emailInput.classList.add("error");
    }

    if (messageInput.value.trim().length < 10) {
        errorMessages.push("Message must be at least 10 characters.");
        messageInput.classList.add("error");
    }

    if (errorMessages.length > 0) {
        event.preventDefault();
        errors.innerHTML = errorMessages
            .map(function (message) {
                return "<p>" + message + "</p>";
            })
            .join("");
    } else {
        errors.textContent = "";
    }
});
```

## Validation Tests Students Can Use

| Test Type | Example |
|---|---|
| Presence test | Did the user leave the field empty? |
| Value test | Did the user choose a required option? |
| Range test | Is the number within the allowed range? |
| Length test | Is the message long enough? |
| Consistency test | Do two fields match or make sense together? |