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

Forms are important because they allow a website to become interactive. A form can collect information for:

- a contact page,
- a login page,
- a sign-up page,
- a quiz,
- a survey,
- a product order,
- a search bar,
- a feedback form.

In a front-end web development, forms are useful because they combine all three major web technologies:

| Technology | Role in a Form |
|---|---|
| HTML | Creates the form structure and fields |
| CSS | Controls spacing, layout, colours, focus states, and error styles |
| JavaScript | Reads input, checks values, displays messages, and responds to submission |

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

A form usually has:

| Part | Purpose |
|---|---|
| `<form>` | Groups the form fields together |
| `id` | Lets CSS or JavaScript select the form |
| `action` | Tells the form where to send data |
| `method` | Tells the form how to send data |
| `<label>` | Describes an input for the user |
| `<input>` | Collects one piece of user input |
| `<textarea>` | Collects longer written responses |
| `<button type="submit">` | Submits the form |

For this unit, students will often use `action="#"` because the form is not being sent to a real server.

```html
<form action="#">
```

This means the form exists mainly for practice and JavaScript interaction.

## The `form` Element

The `<form>` element wraps the input fields that belong together.

```html
<form id="signup-form">
    <!-- form fields go here -->
</form>
```

The `id` is useful when JavaScript needs to select the form.

```js
const form = document.querySelector("#signup-form");
```

The `method` attribute describes how the form data would be sent to a server.

| Method | Meaning | Common Use |
|---|---|---|
| `get` | Sends data in the URL | Searches and filters |
| `post` | Sends data in the request body | Sign-ups, contact forms, logins |

For beginner front-end work, students usually do not need to send the form to a real server. They still need to understand that real websites often send form data somewhere.

## `id` vs. `name`

Students often confuse `id` and `name`.

They are not the same thing.

```html
<input id="email" name="userEmail" type="email">
```

| Attribute | Used For | Example |
|---|---|---|
| `id` | Connecting labels, CSS, and JavaScript | `document.querySelector("#email")` |
| `name` | Identifying the data when a form is submitted | `userEmail=student@example.com` |

The `id` should be unique on the page.

The `name` is especially important when data is sent to a server or collected using `FormData`.


## Labels

Labels make forms easier to use and more accessible.

```html
<label for="email">Email:</label>
<input type="email" id="email" name="email">
```

The `for` value should match the input's `id`.

```html
<label for="email">Email:</label>
<input id="email">
```

This connection matters because:

- screen readers can identify what the input is for,
- clicking the label can focus the input,
- the form is easier to use on small screens,
- the HTML is more organized.

### Label Wrapped Around an Input

Another valid approach is wrapping the input inside the label.

```html
<label>
    Email:
    <input type="email" name="email">
</label>
```

This is common for checkboxes and radio buttons.

```html
<label>
    <input type="checkbox" name="newsletter">
    Sign me up for the newsletter
</label>
```

## Required Fields and Visual Clarity

If a field is required, the form should make that clear.

```html
<label for="name">Name <span aria-hidden="true">*</span></label>
<input id="name" name="name" type="text" required>
```

The `required` attribute tells the browser that the field cannot be empty.

The `*` helps users see that the field is required.

Do not rely on colour only to show required fields. Some users may not see colour differences clearly.

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


| Input Type | Use It For | Example |
|---|---|---|
| `text` | General short text | Name, username, city |
| `email` | Email addresses | `student@example.com` |
| `password` | Hidden password input | Account passwords |
| `number` | Numeric input | Age, quantity, rating |
| `date` | Date picker | Birthday, deadline |
| `checkbox` | One or more on/off choices | Interests, agreement |
| `radio` | One choice from a group | Payment type, contact method |
| `file` | Uploading files | Image upload, resume upload |
| `tel` | Phone numbers | `416-555-1234` |
| `url` | Website addresses | Portfolio link |
| `search` | Search fields | Search bar |

Input types matter because the browser can give users better controls. For example, phones may show an email keyboard for `type="email"`.

## Textarea

Use `textarea` for longer text.

```html
<textarea id="message" name="message"></textarea>
```

Unlike an `<input>`, it is not written as a single self-contained tag.

You can control the starting size with `rows` and `cols`, but CSS is usually better for layout.

```html
<textarea id="message" name="message" rows="5"></textarea>
```
A dropdown lets the user choose from a list.

```html
<label for="topic">Topic</label>
<select id="topic" name="topic">
    <option value="">Choose one</option>
    <option value="question">Question</option>
    <option value="feedback">Feedback</option>
    <option value="other">Other</option>
</select>
```

The text between the `<option>` tags is what the user sees.

The `value` is what JavaScript or the server reads.

```html
<option value="feedback">Feedback</option>
```

If the user selects this option, the value is:

```js
"feedback"
```

A first option with an empty value is useful when students want to force the user to make a real choice.

```html
<option value="">Choose one</option>
```

Then JavaScript can check whether the value is still empty.

```js
if (topicInput.value === "") {
    console.log("Please choose a topic.");
}
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
Use `legend` to give the group a title.

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

This is especially helpful for:

- radio button groups,
- checkbox groups,
- survey sections,
- multi-part forms.

## Radio Buttons

Radio buttons are used when the user should choose one option from a group.

All radio buttons in the same group must share the same `name`.

```html
<fieldset>
    <legend>Preferred Contact Method</legend>

    <label>
        <input type="radio" name="contactMethod" value="email">
        Email
    </label>

    <label>
        <input type="radio" name="contactMethod" value="phone">
        Phone
    </label>
</fieldset>
```

The shared `name` tells the browser that only one option can be selected.

```html
name="contactMethod"
```

To find the selected radio button with JavaScript:

```js
const selectedMethod = document.querySelector("input[name='contactMethod']:checked");

if (selectedMethod !== null) {
    console.log(selectedMethod.value);
}
```

The `:checked` selector finds the selected radio button.

## Checkboxes

Checkboxes are used when the user can turn an option on or off.

```html
<label>
    <input type="checkbox" id="newsletter" name="newsletter">
    Send me updates
</label>
```

For checkboxes, JavaScript usually checks the `checked` property.

```js
const newsletter = document.querySelector("#newsletter");

if (newsletter.checked) {
    console.log("User wants updates.");
}
```

Checkboxes can also be used as a group.

```html
<fieldset>
    <legend>Choose your interests</legend>

    <label>
        <input type="checkbox" name="interests" value="web">
        Web Development
    </label>

    <label>
        <input type="checkbox" name="interests" value="game">
        Game Design
    </label>

    <label>
        <input type="checkbox" name="interests" value="robotics">
        Robotics
    </label>
</fieldset>
```

To collect all checked boxes:

```js
const checkedBoxes = document.querySelectorAll("input[name='interests']:checked");

checkedBoxes.forEach(function(box) {
    console.log(box.value);
});
```

## Buttons

Buttons can have different types.

```html
<button type="submit">Submit</button>
<button type="reset">Reset</button>
<button type="button">Do Something</button>
```

| Button Type | Purpose |
|---|---|
| `submit` | Submits the form |
| `reset` | Resets the form fields |
| `button` | Does not submit by default; useful with JavaScript |

Inside a form, a plain `<button>` acts like a submit button by default.

This can surprise students.

Instead of:

```html
<button>Open Menu</button>
```

Write:

```html
<button type="button">Open Menu</button>
```

Use `type="submit"` only when the button is supposed to submit the form.

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

`box-sizing: border-box;` is useful because it includes padding and borders inside the element's width.

Without it, an input set to `width: 100%;` may overflow its container.

## Focus Styles

A focus style shows which field the user is currently using.

```css
input:focus,
textarea:focus,
select:focus {
    outline: 3px solid #555;
    outline-offset: 2px;
}
```

Do not remove focus outlines unless you replace them with another clear focus style.

This is important for users who navigate with a keyboard.

## Styling Radio Buttons and Checkboxes

Radio buttons and checkboxes usually should not be forced to `width: 100%;`.

A common pattern is to style text inputs separately from choice inputs.

```css
input[type="text"],
input[type="email"],
input[type="password"],
input[type="number"],
textarea,
select {
    width: 100%;
    padding: 10px;
    box-sizing: border-box;
}

input[type="checkbox"],
input[type="radio"] {
    width: auto;
}
```

This avoids giant checkboxes and radio buttons.

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
| `minlength` | Minimum number of characters |
| `maxlength` | Maximum number of characters |
| `pattern` | Regular expression pattern |
| `placeholder` | Hint text inside the field |
| `title` | Extra information about the expected input |
| `step` | Controls allowed number increments |
| `disabled` | Field cannot be used or submitted |
| `readonly` | Field can be read but not edited |
| `autocomplete` | Suggests whether the browser should autofill |

HTML validation is useful for simple rules.

JavaScript validation is useful for more customized rules.

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

For dates, `min` and `max` can also be used.

```html
<input id="event-date" name="eventDate" type="date" min="2026-01-01" max="2026-12-31">
```

### Minlength and Maxlength

```html
<input id="username" name="username" type="text" minlength="5" maxlength="20">
```

The input must be at least 5 characters and no longer than 20 characters.

### Step

The `step` attribute controls allowed number increments.

```html
<input id="rating" name="rating" type="number" min="1" max="5" step="1">
```

This allows whole numbers from 1 to 5.

Another example:

```html
<input id="price" name="price" type="number" min="0" step="0.01">
```

This allows decimal values such as `4.99`.

### Pattern

The `pattern` attribute uses a regular expression.

A regular expression is a pattern that text must match.

Example for a Canadian postal code:

```html
<input
    id="postal-code"
    name="postal-code"
    type="text"
    pattern="[A-Za-z]\d[A-Za-z][ -]?\d[A-Za-z]\d"
    placeholder="A1A 1A1"
    title="Enter a Canadian postal code, such as A1A 1A1"
>
```

This pattern means:

| Part | Meaning |
|---|---|
| `[A-Za-z]` | One letter |
| `\d` | One digit |
| `[ -]?` | Optional space or hyphen |

Patterns can be useful, but they can also become complicated. For beginner projects, use patterns only when the expected format is clear.

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

Do not use placeholder text instead of a label.

Weak:

```html
<input type="email" placeholder="Email">
```

Better:

```html
<label for="email">Email</label>
<input id="email" name="email" type="email" placeholder="student@example.com">
```

The label remains visible even after the user starts typing.

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

`event.preventDefault()` stops the browser from refreshing or submitting the form to a server.

This is important when students want JavaScript to process the form on the same page.

## Reading Different Input Values

Different form controls are read in different ways.

| Control | JavaScript Property or Selector |
|---|---|
| Text input | `.value` |
| Email input | `.value` |
| Password input | `.value` |
| Number input | `.value` or `Number(input.value)` |
| Textarea | `.value` |
| Select dropdown | `.value` |
| Checkbox | `.checked` |
| Radio group | `input[name='groupName']:checked` |

Example:

```js
const nameInput = document.querySelector("#name");
const newsletterInput = document.querySelector("#newsletter");
const topicInput = document.querySelector("#topic");

console.log(nameInput.value);
console.log(newsletterInput.checked);
console.log(topicInput.value);
```

## Input Values Are Usually Strings

A common JavaScript mistake is forgetting that input values are usually strings.

```html
<input id="age" type="number">
```

```js
const ageInput = document.querySelector("#age");
const age = ageInput.value;

console.log(typeof age); // string
```

Even though the input type is `number`, the value is read as a string.

Convert it when you need to do math or numeric comparisons.

```js
const age = Number(ageInput.value);

if (age >= 18) {
    console.log("Adult");
}
```

Be careful with empty input.

```js
Number(""); // 0
```

This can cause confusing bugs. Check for an empty value before converting.

```js
if (ageInput.value.trim() === "") {
    console.log("Age is required.");
} else {
    const age = Number(ageInput.value);
    console.log(age);
}
```

## Trimming Input

Users may accidentally type spaces before or after their answer.

```js
const username = usernameInput.value.trim();
```

The `trim()` method removes extra spaces from the beginning and end of a string.

Example:

```js
"  Alex  ".trim(); // "Alex"
```

This is helpful for validation.

```js
if (usernameInput.value.trim() === "") {
    console.log("Username is required.");
}
```

## Form Events

Forms and inputs can respond to different events.

| Event | When It Happens | Common Use |
|---|---|---|
| `submit` | User submits the form | Final validation |
| `input` | User types or changes a value | Live feedback |
| `change` | User finishes changing a field | Dropdowns, checkboxes, radio buttons |
| `focus` | User enters a field | Highlighting help text |
| `blur` | User leaves a field | Checking one field |

Example using `input`:

```js
const usernameInput = document.querySelector("#username");
const usernameHint = document.querySelector("#username-hint");

usernameInput.addEventListener("input", function() {
    usernameHint.textContent = `${usernameInput.value.length}/20 characters used`;
});
```

Example using `change`:

```js
const topicInput = document.querySelector("#topic");

 topicInput.addEventListener("change", function() {
    console.log(`Topic changed to ${topicInput.value}`);
});
```

## What is Validation?

Validation checks whether user input follows the rules.

Examples:

- Required fields are filled in
- Email addresses are formatted correctly
- Numbers are within a range
- Text follows a pattern
- A password meets requirements
- Two fields match each other
- A checkbox has been accepted
- A dropdown choice has been selected

Validation does not mean the information is true.

For example, this may pass email validation:

```text
fake@example.com
```

It is formatted like an email address, but that does not prove it belongs to the user.

Validation checks format and rules, not truth.

## Client-Side vs. Server-Side Validation

| Type | Where it happens | Purpose |
|---|---|---|
| Client-side validation | In the browser | Gives quick feedback before submission |
| Server-side validation | On the server | Protects the application and data |

In this unit, we focus on client-side validation.

Important note:

> Client-side validation is helpful, but it should not be the only validation used in real applications.

Why?

A user can turn off JavaScript, change the HTML in DevTools, or send fake data another way.

For class projects, client-side validation is enough.

For real websites, server-side validation is also required.

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