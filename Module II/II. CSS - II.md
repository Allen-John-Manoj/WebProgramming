## **CSS Selectors**

A **selector** is the part of a CSS rule that specifies the HTML elements to style.

### **Types of Selectors**

#### **1. Universal Selector (`*`)**
Targets all elements on the page.
```css
* {
    margin: 0;
    padding: 0;
}
```

#### **2. Element (Type) Selector**
Targets all instances of a specific HTML element.
```css
h1 {
    color: blue;
}
```

#### **3. Class Selector (`.`)**
Targets elements with a specific class attribute.
```css
.box {
    border: 1px solid black;
}
```

#### **4. ID Selector (`#`)**
Targets a single element with a specific ID attribute.
```css
#main-header {
    font-size: 24px;
}
```

#### **5. Group Selector (`,`)**
Applies the same style to multiple elements.
```css
h1, h2, p {
    font-family: Arial, sans-serif;
}
```

#### **6. Descendant Selector (Space)**
Targets elements that are descendants of a specified parent.
```css
div p {
    color: gray;
}
```

#### **7. Child Selector (`>`)**
Targets direct children of a specified parent.
```css
ul > li {
    list-style: none;
}
```

#### **8. Sibling Selectors**
- **Adjacent Sibling (`+`)**: Selects the immediate sibling.
  ```css
  h1 + p {
      color: red;
  }
  ```
- **General Sibling (`~`)**: Selects all siblings.
  ```css
  h1 ~ p {
      color: blue;
  }
  ```

#### **9. Attribute Selectors**
Target elements based on attributes.
- Elements with a specific attribute:
  ```css
  input[type] {
      border: 1px solid black;
  }
  ```
- Attribute equals a value:
  ```css
  input[type="text"] {
      background-color: lightgray;
  }
  ```
- Attribute contains a value:
  ```css
  [class*="btn"] {
      padding: 10px;
  }
  ```

#### **10. Pseudo-classes**
Target elements based on their state.
```css
a:hover {
    text-decoration: underline;
}
```

#### **11. Pseudo-elements**
Style specific parts of an element.
```css
p::first-line {
    font-weight: bold;
}
```

---

## **CSS Properties and Values**

### **What is a Property?**
A **property** defines the specific style attribute you want to change (e.g., `color`, `margin`, `font-size`).

### **What is a Value?**
A **value** specifies the setting for the property (e.g., `red`, `20px`, `bold`).

#### **General Syntax**
```css
selector {
    property: value;
}
```

#### **Example:**
```css
h1 {
    color: blue;         /* Property: color, Value: blue */
    font-size: 24px;     /* Property: font-size, Value: 24px */
}
```

---

## **Commonly Used CSS Properties and Their Values**

#### **1. Text and Font Properties**
- `color`: Sets the text color.
  ```css
  p {
      color: red;
  }
  ```
- `font-size`: Sets the size of the font.
  ```css
  h1 {
      font-size: 2em;
  }
  ```
- `font-family`: Specifies the font.
  ```css
  body {
      font-family: Arial, sans-serif;
  }
  ```
- `font-weight`: Defines the thickness of the text.
  ```css
  strong {
      font-weight: bold;
  }
  ```
- `text-align`: Aligns text horizontally.
  ```css
  h1 {
      text-align: center;
  }
  ```
- `line-height`: Sets the height of a line of text.
  ```css
  p {
      line-height: 1.5;
  }
  ```

#### **2. Box Model Properties**
- `margin`: Sets the outer spacing.
  ```css
  div {
      margin: 10px;
  }
  ```
- `padding`: Sets the inner spacing.
  ```css
  section {
      padding: 20px;
  }
  ```
- `border`: Sets the border style, width, and color.
  ```css
  div {
      border: 2px solid black;
  }
  ```
- `width` and `height`: Define the dimensions.
  ```css
  img {
      width: 100px;
      height: auto;
  }
  ```

#### **3. Background Properties**
- `background-color`: Sets the background color.
  ```css
  body {
      background-color: #f0f0f0;
  }
  ```
- `background-image`: Adds a background image.
  ```css
  div {
      background-image: url('background.jpg');
  }
  ```
- `background-repeat`: Defines how the image repeats.
  ```css
  div {
      background-repeat: no-repeat;
  }
  ```

#### **4. Positioning Properties**
- `position`: Specifies how an element is positioned.
  ```css
  div {
      position: absolute;
      top: 50px;
      left: 100px;
  }
  ```
- `z-index`: Sets the stack order.
  ```css
  img {
      z-index: 10;
  }
  ```

#### **5. Display and Visibility**
- `display`: Controls the layout behavior.
  ```css
  span {
      display: inline-block;
  }
  ```
- `visibility`: Toggles visibility without affecting layout.
  ```css
  div {
      visibility: hidden;
  }
  ```

#### **6. Flexbox and Grid Properties**
- Flexbox:
  ```css
  .container {
      display: flex;
      justify-content: center;
      align-items: center;
  }
  ```
- Grid:
  ```css
  .grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
  }
  ```

---

### **Combining Selectors, Properties, and Values**

```css
/* Example: Styling a button */
button {
    background-color: #007BFF; /* Property: background-color, Value: #007BFF */
    color: white;
    font-size: 16px;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}
```

---

### **Understanding Specificity**
When multiple selectors apply to the same element, specificity determines which styles are applied.

#### **Specificity Rules:**
1. Inline styles: `1000`
2. ID selectors: `100`
3. Class and pseudo-class selectors: `10`
4. Element selectors: `1`

#### **Example:**
```css
/* Specificity hierarchy */
div { color: black; }          /* Element selector (Specificity: 1) */
#unique { color: red; }        /* ID selector (Specificity: 100) */
```
---

## **Positioning Modes**

### **1. Static Positioning (Default)**

- This is the default behavior for all elements.
- Elements appear in the natural flow of the document.
- No special positioning is applied.

#### Example:
```css
p {
    position: static; /* Default */
}
```

---

### **2. Relative Positioning**

- Positions the element **relative to its normal position** in the document flow.
- It retains its original space but moves visually.

#### Properties:
- `top`: Moves the element down.
- `bottom`: Moves the element up.
- `left`: Moves the element right.
- `right`: Moves the element left.

#### Example:
```css
div {
    position: relative;
    top: 10px; /* Moves down by 10px */
    left: 20px; /* Moves right by 20px */
    background-color: lightblue;
}
```

---

### **3. Absolute Positioning**

- Positions the element **relative to its nearest positioned ancestor** (an ancestor with `position: relative`, `absolute`, or `fixed`).
- If no such ancestor exists, it positions itself relative to the `<html>` element.

#### Properties:
- Same as relative positioning: `top`, `bottom`, `left`, `right`.

#### Example:
```css
.container {
    position: relative;
    background-color: lightgray;
    height: 200px;
}

.child {
    position: absolute;
    top: 50px;
    left: 30px;
    background-color: pink;
    width: 100px;
    height: 50px;
}
```

#### HTML:
```html
<div class="container">
    <div class="child">I’m absolutely positioned!</div>
</div>
```

---

### **4. Fixed Positioning**

- Positions the element **relative to the viewport** (browser window).
- It does not move when the page is scrolled.

#### Example:
```css
header {
    position: fixed;
    top: 0;
    width: 100%;
    background-color: black;
    color: white;
    text-align: center;
}
```

---

### **5. Sticky Positioning**

- Combines features of `relative` and `fixed`.
- The element toggles between `relative` and `fixed` based on the scroll position.

#### Example:
```css
h1 {
    position: sticky;
    top: 0;
    background-color: yellow;
}
```

---

## **Backgrounds in CSS**

The background of an element includes options like color, image, and positioning.

### **Background Properties**

#### **1. Background Color**
Sets the background color of an element.
```css
div {
    background-color: lightblue;
}
```

#### **2. Background Image**
Adds an image to the background.
```css
div {
    background-image: url('background.jpg');
}
```

#### **3. Background Repeat**
Defines how the background image repeats.
- `repeat` (default): Repeats both horizontally and vertically.
- `repeat-x`: Repeats horizontally.
- `repeat-y`: Repeats vertically.
- `no-repeat`: Does not repeat.

```css
div {
    background-repeat: no-repeat;
}
```

#### **4. Background Position**
Specifies the position of the background image.
```css
div {
    background-position: center center; /* Horizontal and vertical alignment */
}
```

#### **5. Background Size**
Adjusts the size of the background image.
- `cover`: Scales the image to cover the entire element.
- `contain`: Scales the image to fit within the element.
```css
div {
    background-size: cover;
}
```

---

## **List Styles**

Lists in HTML can be styled using CSS for better aesthetics and functionality.

### **List Types**
1. **Ordered List (`<ol>`)**: Displays items in a numbered sequence.
2. **Unordered List (`<ul>`)**: Displays items with bullet points.

### **CSS Properties for Lists**

#### **1. List Style Type**
Defines the style of the bullet or numbering.
```css
ul {
    list-style-type: square; /* Options: disc, circle, square */
}
```

#### **2. List Style Image**
Replaces bullets with an image.
```css
ul {
    list-style-image: url('bullet.png');
}
```

#### **3. List Style Position**
Defines the position of bullets (inside or outside the content box).
```css
ul {
    list-style-position: inside;
}
```

#### Example:
```css
ul {
    list-style-type: circle;
    margin: 10px;
    padding: 0;
}
```

---

## **Table Layouts**

Tables organize data in rows and columns. CSS enhances their appearance and layout.

### **CSS Properties for Tables**

#### **1. Border**
Defines the border around the table, rows, or cells.
```css
table, th, td {
    border: 1px solid black;
    border-collapse: collapse; /* Avoids double borders */
}
```

#### **2. Padding**
Adds spacing within cells.
```css
td {
    padding: 10px;
}
```

#### **3. Width and Height**
Controls the size of the table or cells.
```css
table {
    width: 100%;
}
```

#### **4. Text Alignment**
Aligns content within cells.
```css
th, td {
    text-align: center;
}
```

#### **5. Background and Borders**
Customizes cell colors and borders.
```css
tr:nth-child(even) {
    background-color: #f2f2f2;
}
```

### **Table Example**

#### HTML:
```html
<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Age</th>
            <th>City</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>John</td>
            <td>25</td>
            <td>New York</td>
        </tr>
        <tr>
            <td>Jane</td>
            <td>30</td>
            <td>London</td>
        </tr>
    </tbody>
</table>
```

#### CSS:
```css
table {
    border-collapse: collapse;
    width: 100%;
}

th, td {
    border: 1px solid black;
    padding: 8px;
    text-align: left;
}

tr:nth-child(even) {
    background-color: #f9f9f9;
}
```

---


## **CSS Box Model**

The **CSS Box Model** defines how elements are structured and spaced on a web page. Every element is a rectangular box composed of the following layers:

### **Components of the Box Model**

1. **Content**:
   - The inner part where the text or image appears.
   - Example:
     ```css
     div {
         width: 200px;
         height: 100px;
     }
     ```

2. **Padding**:
   - Space between the content and the border.
   - Example:
     ```css
     div {
         padding: 20px; /* Adds space inside the element around content */
     }
     ```

3. **Border**:
   - A line surrounding the padding and content.
   - Example:
     ```css
     div {
         border: 2px solid black; /* Border width, style, and color */
     }
     ```

4. **Margin**:
   - Space between the border of an element and adjacent elements.
   - Example:
     ```css
     div {
         margin: 10px; /* Adds space outside the element */
     }
     ```

### **Box Model Example**

```html
<div class="box">Hello, World!</div>
```

```css
.box {
    width: 150px;
    height: 100px;
    padding: 10px;
    border: 5px solid blue;
    margin: 20px;
}
```

### **Diagram of Box Model**
| Component | Example Value | Description                          |
|-----------|---------------|--------------------------------------|
| Content   | `150px`       | Actual area of the box.              |
| Padding   | `10px`        | Space around the content.            |
| Border    | `5px solid`   | Encircles padding and content.       |
| Margin    | `20px`        | Space outside the border.            |

---

## **Text Flow**

CSS controls the way text flows and wraps within elements.

### **Properties Controlling Text Flow**

1. **Text Alignment**
   - Aligns text horizontally.
   - Example:
     ```css
     p {
         text-align: justify; /* Options: left, center, right, justify */
     }
     ```

2. **Text Wrapping**
   - Specifies whether text wraps inside the container.
   - Example:
     ```css
     div {
         white-space: nowrap; /* Options: normal, nowrap, pre-wrap */
     }
     ```

3. **Text Overflow**
   - Handles overflowing text within a container.
   - Example:
     ```css
     div {
         text-overflow: ellipsis; /* Options: clip, ellipsis */
         overflow: hidden;
         white-space: nowrap;
     }
     ```

4. **Word Break**
   - Controls how words break inside a container.
   - Example:
     ```css
     p {
         word-break: break-word; /* Options: normal, break-word */
     }
     ```

---

## **Basics of Responsive CSS**

Responsive web design ensures web pages look good on all devices (desktops, tablets, phones) by adapting to different screen sizes.

### **Key Techniques in Responsive CSS**

1. **Flexible Layouts**
   - Use relative units like percentages (`%`) or `em` for dimensions.
   - Example:
     ```css
     .container {
         width: 80%; /* Adjusts width relative to the viewport */
         max-width: 1200px; /* Sets a maximum width */
     }
     ```

2. **Viewport Meta Tag**
   - Ensures the website scales correctly on mobile devices.
   - Example:
     ```html
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     ```

3. **Fluid Images**
   - Make images scale proportionally.
   - Example:
     ```css
     img {
         max-width: 100%;
         height: auto;
     }
     ```

4. **Media Queries**
   - Customize styles for different screen sizes (explained below).

---

## **Media Queries**

Media queries enable the application of CSS rules based on device characteristics like width, height, resolution, or orientation.

### **Syntax of a Media Query**
```css
@media (condition) {
    /* CSS rules here */
}
```

### **Common Media Query Conditions**

1. **Width and Height**
   - Target devices with specific viewport dimensions.
   ```css
   @media (max-width: 600px) {
       body {
           background-color: lightblue;
       }
   }
   ```

2. **Orientation**
   - Target devices in portrait or landscape mode.
   ```css
   @media (orientation: portrait) {
       img {
           width: 100%;
       }
   }
   ```

3. **Resolution**
   - Target devices based on pixel density.
   ```css
   @media (min-resolution: 2dppx) {
       img {
           content: url('high-res-image.jpg');
       }
   }
   ```

---

### **Combining Media Queries**

You can use logical operators like `and`, `or`, and `not` to combine queries.

#### Example:
```css
@media (min-width: 768px) and (max-width: 1024px) {
    body {
        font-size: 18px;
    }
}
```

---

### **Media Query Breakpoints**

Breakpoints define the screen widths where styles change. Common breakpoints are:

| Device Type | Width Range         |
|-------------|---------------------|
| Small (Mobile) | 0px to 600px       |
| Medium (Tablet) | 601px to 1024px    |
| Large (Desktop) | 1025px and above   |

---

### **Complete Responsive Example**

#### HTML:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Responsive Example</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>Responsive Header</header>
    <main>
        <p>This layout adjusts to different screen sizes!</p>
    </main>
</body>
</html>
```

#### CSS:
```css
/* Default Styles */
body {
    font-family: Arial, sans-serif;
    background-color: white;
    margin: 0;
}

header {
    background-color: blue;
    color: white;
    text-align: center;
    padding: 20px;
}

/* Mobile Styles */
@media (max-width: 600px) {
    header {
        font-size: 16px;
        padding: 10px;
    }
    main {
        padding: 5px;
    }
}

/* Tablet Styles */
@media (min-width: 601px) and (max-width: 1024px) {
    header {
        font-size: 24px;
    }
    main {
        padding: 20px;
    }
}

/* Desktop Styles */
@media (min-width: 1025px) {
    header {
        font-size: 32px;
    }
    main {
        padding: 40px;
    }
}
```
