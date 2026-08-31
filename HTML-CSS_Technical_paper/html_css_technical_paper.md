# CSS Box Model

The CSS Box Model is used to understand the space and size of an HTML element.
You can think of every HTML element as a box.

For example:

```html
<div>Hello World</div>
```

This div is like a box.

The Box Model has four parts:

```text
Content > Padding > Border > Margin
```

## 1. Content

Content is the actual thing inside the element.
It can be text, an image, or another HTML element.

Example:

```html
<div>Hello World</div>
```

Here, Hello World is the content.

You can set the content size using width and height.

```css
.box {
    width: 200px;
    height: 100px;
}
```

## 2. Padding

Padding is the space inside the element.

It creates space between the content and the border.

Example:

```css
.box {
    padding: 20px;
}
```

```text
+-------------------+
|      Padding      |
|                   |
|    Hello World    |
|                   |
|      Padding      |
+-------------------+
```

The text does not touch the border because padding creates space around it.

## 3. Border

Border is a line around the content and padding.

Example:

```css
.box {
    border: 2px solid black;
}
```

Here:

- 2px is the border thickness.
- solid is the border style.
- black is the border color.

## 4. Margin

Margin is the space outside the element.

It creates space between one element and another element.

Example:

```css
.box {
    margin: 20px;
}
```

```text
+-------------------+
|       Box 1       |
+-------------------+

      Margin

+-------------------+
|       Box 2       |
+-------------------+
```

# Inline and Block Elements

HTML elements are mainly divided into two types. They are Block Elements and Inline Elements.

## Block Elements

A block element starts on a new line and usually takes the full available width.

Some common examples of block elements are div, p, h1, h2, ul, and section.

### Example
```html
<div>This is a block element</div>
<p>This is a paragraph</p>
<h1>This is a heading</h1>
```

In this example, each element starts on a new line.

## Inline Elements

An inline element does not start on a new line. It only takes the space needed for its content.

- examples : span, a, strong, em, and img.

### Example
```html
<p>Hello 
<span>World</span>
</p>
```
Here, the span element stays on the same line as the other text.

## Difference Between Block and Inline Elements

- Block elements start on a new line and usually take the full available width.
- Inline elements stay on the same line and take only the space needed for their content.

### Example
```html
    <div>Box One</div>
    <div>Box Two</div>

    <span>Text One</span>
    <span>Text Two</span>
```
- The two div elements appear on different lines because they are block elements.
- The two span elements appear on the same line because they are inline elements.

## Simple Diagram

    Block Elements

    +-------------------+
    |      Box One      |
    +-------------------+

    +-------------------+
    |      Box Two      |
    +-------------------+


    Inline Elements

    +----------+ +----------+
    |  Text 1  | |  Text 2  |
    +----------+ +----------+

- Block elements are mainly used to create the structure of a webpage.
- Inline elements are used for smaller parts of content that can stay on the same line.

# Positioning: Relative and Absolute

- CSS positioning is used to control where an HTML element appears on a webpage.
- There are different types of positioning in CSS. Two common types are relative and absolute positioning.

## Relative Positioning

- Relative positioning moves an element from its normal position.
- The element still keeps its original space on the webpage.
- We use the top, bottom, left, and right properties to move the element.

### Example
```css
.box {
    position: relative;
    left: 30px;
    top: 20px;
}
```
In this example, the box moves 30 pixels to the right and 20 pixels down from its normal position.
The original space of the box is still kept.

## Absolute Positioning

- Absolute positioning places an element at a specific position.
- The element is removed from the normal flow of the webpage.
- An absolute element is positioned relative to its nearest positioned parent.

### Example
```css
.parent {
    position: relative;
    width: 300px;
    height: 200px;
}

.box {
    position: absolute;
    top: 20px;
    right: 20px;
}
```
In this example, the box is placed 20 pixels from the top and 20 pixels from the right side of the parent element.
The parent has position relative, so the absolute element uses the parent as its reference.

## Simple Example
```css
<div class="parent">
    <div class="box">Hello</div>
</div>

.parent {
    position: relative;
    width: 300px;
    height: 200px;
    border: 1px solid black;
}

.box {
    position: absolute;
    top: 20px;
    left: 20px;
}
```
The box will appear inside the parent, 20 pixels from the top and 20 pixels from the left.

## Difference Between Relative and Absolute

- Relative positioning moves the element from its normal position and keeps its original space.
- Absolute positioning removes the element from the normal flow and places it according to its positioned parent.

<br>

# Common CSS Structural Classes

- CSS structural classes are commonly used to organize and style different parts of a webpage.
- They help us give meaningful names to different sections of a webpage.

## Common Structural Classes

Some common structural classes are container, header, nav, main, section, article, aside, and footer.

## Container

A container is used to hold the main content of a webpage.

Example
```html
<div class="container">
    <h1>My Website</h1>
    <p>This is my website.</p>
</div>
```
```css
.container {
    width: 80%;
    margin: auto;
}
```

## Header

The header is usually used for the top part of a webpage.

Example
```html
<header class="header">
    <h1>My Website</h1>
</header>
```
```css
.header {
    background-color: lightblue;
    padding: 20px;
}
```
## Navigation

The navigation class is used for menus and links.

Example
```html
<nav class="nav">
    <a href="#">Home</a>
    <a href="#">About</a>
    <a href="#">Contact</a>
</nav>
```
## Main

The main class is used for the main content of the webpage.

Example
```html
<main class="main">
    <h2>Welcome</h2>
    <p>This is the main content.</p>
</main>
```
## Section

A section is used to divide a webpage into different parts.

Example
```html
<section class="section">
    <h2>About Us</h2>
    <p>This section contains information about us.</p>
</section>
```
## Article

The article class is used for independent content such as a blog post or news article.

Example
```html
<article class="article">
    <h2>My First Blog</h2>
    <p>This is my first blog post.</p>
</article>
```
## Aside

The aside class is used for additional content such as a sidebar.

Example
```html
<aside class="aside">
    <h3>Related Links</h3>
    <p>Some additional information.</p>
</aside>
```
## Footer

The footer is usually used for the bottom part of a webpage.

Example
```html
    <footer class="footer">
      <p>Copyright 2026</p>
    </footer>
```
## Simple Structure
```html
<div class="container">

    <header class="header">
    Header
    </header>

    <nav class="nav">
    Navigation
    </nav>

    <main class="main">

        <section class="section">
            Main Section
        </section>

        <article class="article">
            Article Content
        </article>

    </main>

    <footer class="footer">
    Footer
    </footer>

</div>
```

# Common CSS Styling Classes

- CSS styling classes are used to change the appearance of HTML elements.
- They can be used to change colors, text, spacing, size, alignment, and other styles.

## Text Alignment

The text center class is used to align text in the center.

### HTML

~~~html
<p class="text-center">Hello World</p>
~~~

### CSS

~~~css
.text-center {
  text-align: center;
}
~~~

## Bold Text

The text bold class is used to make text bold.

### HTML

~~~html
<p class="text-bold">This is bold text</p>
~~~

### CSS

```css
.text-bold {
  font-weight: bold;
}
```

## Text Color

The text danger class is used to change the text color to red.

### HTML

~~~html
<p class="text-danger">This is an error message</p>
~~~

### CSS

~~~css
.text-danger {
  color: red;
}
~~~

## Background Color

The bg primary class is used to add a background color to an element.

### HTML

~~~html
<div class="bg-primary">
  This is a box
</div>
~~~

### CSS

~~~css
.bg-primary {
  background-color: blue;
  color: white;
}
~~~

## Multiple Styling Classes

We can use more than one class on the same HTML element.

### HTML

~~~html
<div class="box text-center rounded shadow">
  <h2>Hello World</h2>
  <p>This is a styled box.</p>
</div>
~~~

### CSS

~~~css
.box {
  padding: 20px;
  background-color: lightblue;
}

.text-center {
  text-align: center;
}

.rounded {
  border-radius: 10px;
}

.shadow {
  box-shadow: 0 2px 5px gray;
}
~~~


# CSS Specificity

CSS Specificity is used when more than one CSS rule is applied to the same HTML element.

It helps the browser decide which CSS rule should be used.

In simple words, when different CSS selectors try to change the same thing, the selector with higher priority wins.

## Example

```html
<p id="title" class="text">Hello World</p>
```

```css
p {
    color: blue;
}

.text {
    color: green;
}

#title {
    color: red;
}
```

- Here, all three CSS rules are trying to change the color of the same paragraph.
- The final color will be red.
- This is because the ID selector has higher priority than the class selector and the element selector.

## Specificity Order

The basic order of CSS specificity is:

```text
Inline style
ID selector
Class selector
Element selector
```

We can also write it like this:

```text
style > #id > .class > element
```

## Element Selector

An element selector has lower priority.

Example:

```css
p {
    color: blue;
}
```

- This selects all `<p>` elements.

## Class Selector

A class selector has more priority than an element selector.

Example:

```css
.text {
    color: green;
}
```

Here, the class selector will win over the `p` selector.

## ID Selector

An ID selector has more priority than a class selector.

Example:

```css
#title {
    color: red;
}
```

The ID selector will win if both the ID and class are trying to change the same property.

## Inline Style

An inline style is written directly inside an HTML element.

Example:

```html
<p style="color: purple;">Hello World</p>
```

Inline styles have very high priority compared to normal CSS selectors.

# CSS Responsive Queries

CSS Responsive Queries, also called **Media Queries**, are used to change a website's design based on the screen size.

They help websites work well on:

* Mobile
* Tablet
* Laptop
* Desktop

## Basic Syntax

```css
@media (condition) {
    /* CSS code */
}
```

The CSS inside the media query works only when the condition is true.

## Example

```css
p {
    font-size: 24px;
}

@media (max-width: 600px) {
    p {
        font-size: 16px;
    }
}
```

Here, the font size is `24px` normally. On screens **600px or smaller**, it becomes `16px`.

## `max-width` and `min-width`

`max-width` applies CSS when the screen is **equal to or smaller than** the given size.

```css
@media (max-width: 600px) {
    .container {
        width: 100%;
    }
}
```

`min-width` applies CSS when the screen is **equal to or larger than** the given size.

```css
@media (min-width: 768px) {
    .container {
        display: flex;
    }
}
```

## Breakpoints

Breakpoints are screen sizes where we change the layout.

```css
/* Mobile */
@media (max-width: 600px) { }

/* Tablet */
@media (min-width: 601px) and (max-width: 1024px) { }

/* Desktop */
@media (min-width: 1025px) { }
```

## Mobile-First Approach

In the mobile-first approach, we write CSS for mobile first and use `min-width` for larger screens.

```css
.container {
    display: block;
}

@media (min-width: 768px) {
    .container {
        display: flex;
    }
}
```

**In simple words:**

```text
Mobile → Block layout
Desktop → Flex layout
```

# Flexbox

Flexbox is a CSS layout system used to arrange elements in one direction. The elements can be arranged in a row or in a column.

To use Flexbox, we set display flex on the parent element. All direct child elements become flex items.

Example

```html
<div class="container">
    <div class="item">One</div>
    <div class="item">Two</div>
    <div class="item">Three</div>
</div>
```

```css
.container {
    display: flex;
}
```

By default, the items are displayed in a row.

The flex direction property changes the direction of the items.

```css
.container {
    display: flex;
    flex-direction: column;
}
```

Now the items are displayed from top to bottom.

The justify content property controls the alignment on the main axis.

```css
.container {
    display: flex;
    justify-content: center;
}
```

This places the items in the center.

Some common values are flex start, flex end, center, space between, and space around.

The align items property controls alignment in the other direction.

```css
.container {
    display: flex;
    align-items: center;
}
```

The gap property creates space between flex items.

```css
.container {
    display: flex;
    gap: 20px;
}
```

The flex wrap property allows items to move to the next line when there is not enough space.

```css
.container {
    display: flex;
    flex-wrap: wrap;
}
```

Flexbox is commonly used for navigation bars, buttons, menus, and simple layouts.

## Grid

CSS Grid is a layout system used to arrange elements in rows and columns. It gives more control over a page layout.

To use Grid, we set display grid on the parent element.

Example

```html
<div class="container">
    <div class="item">One</div>
    <div class="item">Two</div>
    <div class="item">Three</div>
</div>
```

```css
.container {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
}
```

- This creates three equal columns.
- The fr unit means a fraction of the available space.
- We can also create columns with different sizes.

```css
.container {
    display: grid;
    grid-template-columns: 1fr 2fr 1fr;
}
```

Here, the second column gets twice as much space as the first and third columns.

The gap property creates space between rows and columns.

```css
.container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
}
```

The grid template rows property creates rows.

```css
.container {
    display: grid;
    grid-template-rows: 100px 100px;
}
```

We can also make Grid responsive using repeat and minmax.

```css
.container {
    display: grid;
    grid-template-columns:
        repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
}
```

This creates as many columns as possible. When the screen becomes smaller, items automatically move to the next row.

Grid is commonly used for page layouts, dashboards, image galleries, and card sections.

## Common Header Meta Tags

Meta tags provide information about the web page.

Example

```html
<head>
    <meta charset="UTF-8">

    <meta
        name="viewport"
        content="width=device-width, initial-scale=1.0"
    >

    <meta
        name="description"
        content="Simple CSS website"
    >

    <title>My Website</title>
</head>
```

- The charset tag supports different characters.
- The viewport tag helps the page work properly on mobile devices.
- The description tag gives information about the web page.
- The title tag shows the page title in the browser tab.

## Another Important Topic

The CSS cascade decides which styles are applied when multiple rules target the same element.

For example, if two rules have the same specificity, the rule written later is usually applied.

```css
p {
    color: blue;
}

p {
    color: green;
}
```

The paragraph will be green because the second rule is written later.

## References

- CSS Concepts - https://www.learn-html-css.com/learn-html-css/learn-to-code-css/css-box-model/
- CSS Specificity Youtube Video - https://youtu.be/uTcpbPMZlFE?si=ugp8Pirm8A_JWKyV
- I took help from ChatGPT to create the box diagrams used in this file.
