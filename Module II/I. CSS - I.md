# Introduction to Cascading Style Sheets (CSS)

## What is CSS?
CSS (Cascading Style Sheets) is a stylesheet language used to control the appearance and layout of web pages. It allows developers to separate content (HTML) from presentation, making websites easier to design, maintain, and scale.

## Key Features of CSS:
- **Separation of content and design**: HTML handles structure, while CSS manages the presentation.
- **Styling flexibility**: Control over color, layout, fonts, and much more.
- **Responsive design**: Adapt the layout to different devices and screen sizes.
- **Cascading rules**: Styles can be applied hierarchically, combining multiple stylesheets.

## Why Use CSS?
1. **Consistency**: Apply a uniform design across multiple web pages.
2. **Efficiency**: Update design globally by modifying a single CSS file.
3. **Customization**: Create visually appealing and user-friendly designs.

---

## Introduction to CSS3
CSS3 is the latest standard of CSS, bringing new features, modules, and functionalities. It builds on CSS2 and introduces capabilities that enhance web design.

#### Key Features of CSS3:
1. **Selectors**: Advanced selectors like `:nth-child`, `:not`, etc.
2. **Box Model Enhancements**: Rounded corners (`border-radius`), box shadows.
3. **Media Queries**: For responsive designs based on screen size or device type.
4. **Transitions and Animations**: Smooth state changes and interactive effects.
5. **New Color Models**: Support for RGBA, HSLA, gradients, and more.
6. **Web Fonts**: Use custom fonts with `@font-face`.

---

## Basic Syntax and Structure of CSS

CSS is written in the form of **rules**. Each rule consists of:
1. **Selector**: Targets the HTML element(s) to style.
2. **Declaration Block**: Contains one or more declarations enclosed in curly braces `{}`.

### Syntax:
```css
selector {
    property: value;
    property: value;
}
```

### Components:
- **Selector**: Specifies which HTML element(s) to style (e.g., `h1`, `.class`, `#id`).
- **Property**: A specific style attribute (e.g., `color`, `font-size`).
- **Value**: The desired value for the property (e.g., `red`, `16px`).

### Example:
```css
/* Selects all paragraph elements and sets their text color to blue */
p {
    color: blue;
    font-size: 14px;
}
```

---

## CSS Rules: Types of Selectors

### Basic Selectors:
1. **Element Selector**: Targets all elements of a specific type.
   ```css
   h1 {
       color: red;
   }
   ```
2. **Class Selector**: Targets elements with a specific class.
   ```css
   .highlight {
       background-color: yellow;
   }
   ```
3. **ID Selector**: Targets a single element with a specific ID.
   ```css
   #unique {
       font-weight: bold;
   }
   ```

### Advanced Selectors:
1. **Group Selector**: Styles multiple elements.
   ```css
   h1, h2, p {
       margin: 10px;
   }
   ```
2. **Descendant Selector**: Targets elements inside a specific parent.
   ```css
   div p {
       font-style: italic;
   }
   ```
3. **Pseudo-classes**: Styles elements based on their state.
   ```css
   a:hover {
       color: green;
   }
   ```
4. **Attribute Selector**: Targets elements with specific attributes.
   ```css
   input[type="text"] {
       border: 1px solid black;
   }
   ```

---

## Inline Styles

### What are Inline Styles?
Inline styles are written directly within an HTML element using the `style` attribute. These styles apply only to the specific element.

#### Syntax:
```html
<element style="property: value;">
```

#### Example:
```html
<p style="color: red; font-size: 16px;">This is a paragraph with inline styles.</p>
```

#### Pros of Inline Styles:
1. **Quick application**: Apply styles directly to an element without creating a CSS file.
2. **Overrides external styles**: Inline styles take precedence over internal and external styles.

#### Cons of Inline Styles:
1. **Harder to maintain**: Difficult to manage when applied extensively.
2. **Limited functionality**: Lacks features like media queries, animations, etc.
3. **Poor separation of concerns**: Mixing content and presentation.


### Practical Examples

#### Inline vs Internal vs External Styles

1. **Inline Style Example**:
   ```html
   <h1 style="color: blue; text-align: center;">Hello, World!</h1>
   ```

2. **Internal Style Example** (inside `<style>` tag):
   ```html
   <style>
       h1 {
           color: green;
           text-align: center;
       }
   </style>
   <h1>Hello, World!</h1>
   ```

3. **External Style Example** (linked via an external file):
   ```html
   <!-- HTML -->
   <link rel="stylesheet" href="styles.css">
   <h1>Hello, World!</h1>

   /* CSS (styles.css) */
   h1 {
       color: red;
       text-align: center;
   }
   ```

---

## Cascading and Specificity

CSS follows cascading rules to resolve conflicts when multiple styles apply to an element:
1. **Inline styles** have the highest priority.
2. **ID selectors** take precedence over classes.
3. **Classes, attributes, and pseudo-classes** take precedence over element selectors.

### Specificity Calculation:
- Inline styles: **1000**
- ID selector: **100**
- Class, attributes, pseudo-classes: **10**
- Element: **1**

### Example:
```css
/* Element selector */
p {
    color: blue;
}

/* Class selector (overrides element styles) */
.special {
    color: green;
}

/* ID selector (overrides class styles) */
#unique {
    color: red;
}
```

```html
<p>This text is blue.</p>
<p class="special">This text is green.</p>
<p id="unique">This text is red.</p>
```
---
## Embedded Style Sheets and Linking External Style Sheets

CSS can be applied to web pages using various methods. Two commonly used methods are **embedded style sheets** and **linking external style sheets**. These approaches help organize and manage styles efficiently for web development.

### Embedded Style Sheets

An **embedded style sheet** is written directly within the `<style>` tag in the `<head>` section of an HTML document. It applies styles to the current HTML document only.

#### Syntax:
```html
<style>
    selector {
        property: value;
    }
</style>
```

#### Example:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Embedded Style Example</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            margin: 0;
            padding: 0;
        }
        h1 {
            color: #333;
            text-align: center;
        }
        p {
            color: #666;
            line-height: 1.6;
            padding: 10px;
        }
    </style>
</head>
<body>
    <h1>Welcome to Embedded Styles</h1>
    <p>This is an example of an embedded style sheet.</p>
</body>
</html>
```

#### Key Features:
- **Location**: Styles are defined within the `<style>` tag inside the `<head>` section.
- **Scope**: The styles apply only to the document in which they are embedded.

#### Pros of Embedded Style Sheets:
1. Easy to test and modify styles for a single page.
2. No need for an external file, making it quick to implement.

#### Cons of Embedded Style Sheets:
1. Styles are not reusable across multiple pages.
2. Increases the size of the HTML file, potentially slowing down load times.

---

## Linking External Style Sheets

An **external style sheet** is a separate `.css` file linked to an HTML document using the `<link>` tag. This approach is ideal for applying consistent styles across multiple web pages.

#### Syntax:
1. **In the HTML file**:
   ```html
   <link rel="stylesheet" href="styles.css">
   ```
2. **In the external CSS file** (`styles.css`):
   ```css
   selector {
       property: value;
   }
   ```

#### Example:

**HTML File (index.html):**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>External Style Example</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1>Welcome to External Styles</h1>
    <p>This is an example of linking to an external style sheet.</p>
</body>
</html>
```

**CSS File (styles.css):**
```css
body {
    font-family: Verdana, sans-serif;
    background-color: #e0f7fa;
    margin: 0;
    padding: 0;
}

h1 {
    color: #00796b;
    text-align: center;
}

p {
    color: #004d40;
    font-size: 16px;
    line-height: 1.8;
    padding: 10px;
}
```

#### Key Features:
- **Location**: Styles are stored in a separate `.css` file.
- **Linking**: The HTML document references the external file using the `<link>` tag.

#### Pros of External Style Sheets:
1. **Reusability**: Use the same stylesheet for multiple web pages.
2. **Maintainability**: Update styles in one place to reflect changes across all linked pages.
3. **Optimized Performance**: External stylesheets can be cached by browsers, reducing load times for subsequent visits.

#### Cons of External Style Sheets:
1. **Dependency**: Requires an additional HTTP request to fetch the CSS file.
2. **No inline preview**: Changes in the CSS file require saving and reloading the browser to view updates.


### Comparing Embedded and External Style Sheets

| Feature                | Embedded Style Sheets                | External Style Sheets                  |
|------------------------|---------------------------------------|----------------------------------------|
| **Location**           | Inside the HTML document (`<style>`).| In a separate `.css` file.             |
| **Scope**              | Applies to the current document only.| Can be reused across multiple pages.   |
| **Performance**        | Increases HTML file size.            | Requires additional HTTP requests.     |
| **Reusability**        | Not reusable.                        | Highly reusable.                       |
| **Maintenance**        | Harder to maintain for multiple pages.| Easier to update styles globally.      |

---

## Combining Embedded and External Style Sheets

It is possible to use both embedded and external style sheets in the same document. However, **cascading rules** determine which styles are applied. Inline styles have the highest priority, followed by embedded styles, and then external styles.

#### Example:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Combining Styles</title>
    <link rel="stylesheet" href="external.css"> <!-- External styles -->
    <style>
        /* Embedded styles */
        h1 {
            color: green;
        }
    </style>
</head>
<body>
    <h1 style="color: red;">This is an inline styled heading</h1> <!-- Inline style -->
    <p>This paragraph is styled using an external stylesheet.</p>
</body>
</html>
```

---

### When to Use Which Method?

| Use Case                                   | Recommended Method            |
|-------------------------------------------|-------------------------------|
| For a small, single-page project.         | Inline or embedded styles.    |
| For a large website with multiple pages.  | External style sheets.        |
| For rapid prototyping or debugging.       | Embedded styles.              |
| To ensure consistency across pages.       | External style sheets.        |

By understanding and applying these methods effectively, you can achieve both flexibility and maintainability in your web designs.
