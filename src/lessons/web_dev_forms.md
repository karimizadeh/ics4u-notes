# Web Development - Forms and Validations

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

Forms can send data to a server, but in this unit students can also use forms for in-browser processing with JavaScript.

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

## Textarea

Use `textarea` for longer text.

```html
<textarea id="message" name="message"></textarea>
```

## Select Dropdown

```html
<label for="topic">Topic</label>
<select id="topic" name="topic">
    <option value="">Choose one</option>
    <option value="question">Question</option>
    <option value="feedback">Feedback</option>
    <option value="other">Other</option>
</select>
```

## Fieldset and Legend

Use `fieldset` to group related inputs.

```html
<fieldset>
    <legend>Preferred Contact Method</legend>

    <label>
        <input type="radio" name="contact-method" value="email">
        Email
    </label>

    <label>
        <input type="radio" name="contact-method" value="phone">
        Phone
    </label>
</fieldset>
```

## Styling Forms

```css
form {
    max-width: 600px;
    margin: 20px auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 10px;
}

label {
    display: block;
    margin-top: 12px;
    font-weight: bold;
}

input,
textarea,
select,
button {
    width: 100%;
    padding: 10px;
    margin-top: 4px;
    box-sizing: border-box;
}
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


## Accessing Form Values with JavaScript

HTML:

```html
<form id="contact-form">
    <input id="name" name="name" type="text">
    <button type="submit">Submit</button>
</form>

<p id="form-output"></p>
```

JavaScript:

```js
const form = document.querySelector("#contact-form");
const output = document.querySelector("#form-output");

form.addEventListener("submit", function(event) {
    event.preventDefault();

    const name = document.querySelector("#name").value;
    output.textContent = `Thank you, ${name}. Your form was submitted.`;
});
```

`event.preventDefault()` stops the browser from refreshing or submitting the form to a server.

## What is Validation?

Validation checks whether user input follows the rules.

Examples:

- Required fields are filled in
- Email addresses are formatted correctly
- Numbers are within a range
- Text follows a pattern
- A password meets requirements

## Client-Side vs. Server-Side Validation

| Type | Where it happens | Purpose |
|---|---|---|
| Client-side validation | In the browser | Gives quick feedback before submission |
| Server-side validation | On the server | Protects the application and data |

In this unit, we focus on client-side validation.

Important note:

> Client-side validation is helpful, but it should not be the only validation used in real applications.


## HTML Validation Attributes

### Required

```html
<input id="name" name="name" type="text" required>
```

The field must be filled in.


### Min and Max

```html
<input id="age" name="age" type="number" min="13" max="120">
```

The number must be within the range.


### Maxlength

```html
<input id="username" name="username" type="text" maxlength="20">
```

The input cannot be longer than 20 characters.


### Pattern

The `pattern` attribute uses a regular expression.

Example for a Canadian postal code:

```html
<input
    id="postal-code"
    name="postal-code"
    type="text"
    pattern="[A-Za-z]\d[A-Za-z][ -]?\d[A-Za-z]\d"
    placeholder="A1A 1A1"
>
```


### Placeholder and Title

```html
<input
    id="phone"
    name="phone"
    type="tel"
    placeholder="555-555-5555"
    title="Enter a phone number in the format 555-555-5555"
>
```

`placeholder` gives an example.

`title` can give more instructions.

## CSS Validation Pseudo-Classes

CSS can style inputs based on validation state.

```css
input:valid {
    border-color: green;
}

input:invalid {
    border-color: red;
}

input:required {
    background-color: #fff8e1;
}
```

Other useful pseudo-classes:

| Selector | Meaning |
|---|---|
| `:valid` | Input meets validation rules |
| `:invalid` | Input does not meet validation rules |
| `:required` | Input has the required attribute |
| `:optional` | Input does not have the required attribute |
| `:in-range` | Number is within range |
| `:out-of-range` | Number is outside range |


## JavaScript Validation

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

## Good Error Messages

Good error messages should:

- Be specific
- Be polite
- Tell the user how to fix the issue
- Appear near the problem when possible

Weak:

```text
Invalid input.
```

Better:

```text
Username must be at least 5 characters.
```

## Validation Tests Students Can Use

| Test Type | Example |
|---|---|
| Presence test | Did the user leave the field empty? |
| Value test | Did the user choose a required option? |
| Range test | Is the number within the allowed range? |
| Length test | Is the message long enough? |
| Consistency test | Do two fields match or make sense together? |