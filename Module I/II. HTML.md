## **1. HTML5 Document Structure**

An HTML5 document has a simple structure, but each part plays a key role. Here's how to build and structure a basic HTML5 document:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document Title</title>
    <link rel="stylesheet" href="styles.css">
  </head>
  <body>
    <h1>Main Heading</h1>
    <p>Welcome to the page!</p>
  </body>
</html>
```

- **`<!DOCTYPE html>`**: Declares the document type and version of HTML (HTML5 here).
- **`<html>`**: The root element of the HTML document.
- **`<head>`**: Contains meta-information about the document (e.g., character set, viewport settings, title, external files).
- **`<body>`**: Contains all visible content that users see (text, images, links, etc.).



## **2. Fundamentals of HTML**

HTML (Hypertext Markup Language) is used to structure content on the web. It uses **elements**, defined by **tags**, to create content and format it.

- **Tags**: HTML elements are enclosed in angle brackets (`< >`), e.g., `<h1>`, `<p>`.
- **Attributes**: Additional information within tags that customize the behavior or presentation of elements. Attributes are defined with `name="value"`, e.g., `<img src="image.jpg" alt="description">`.



## **3. Headings in HTML**

Headings are essential for organizing content into sections, helping with both user experience and SEO (Search Engine Optimization). HTML has six levels of headings, from `<h1>` to `<h6>`. `<h1>` is the most important, while `<h6>` is the least.

### Example:
```html
<h1>Main Heading (Highest Importance)</h1>
<h2>Subheading Level 1</h2>
<h3>Subheading Level 2</h3>
<h4>Subheading Level 3</h4>
<h5>Subheading Level 4</h5>
<h6>Subheading Level 5 (Lowest Importance)</h6>
```

- **`<h1>`**: Usually represents the main title or theme of the page (important for SEO).
- **`<h2>` to `<h6>`**: Used for subsections or detailed organization. 
- **Best Practice**: Use headings in descending order for logical content hierarchy. **Avoid skipping levels** (e.g., don’t use `<h3>` directly after `<h1>`).


## **4. Working with Images in HTML**

Images are an essential part of modern websites. The **`<img>`** tag in HTML allows you to embed images in your webpage. It requires the `src` attribute (specifying the image source) and the `alt` attribute (providing a text description of the image for accessibility).

### Basic Image Embedding:
```html
<img src="path/to/image.jpg" alt="Description of the image">
```

- **`src`**: Specifies the path to the image (could be a local path or a URL).
- **`alt`**: Provides a description for the image. Important for accessibility (e.g., screen readers) and in cases where the image is not loaded.

### Example of an Image with a Link:
```html
<a href="https://example.com">
  <img src="image.jpg" alt="Description of the image">
</a>
```
- This example embeds an image that, when clicked, will take the user to `https://example.com`.

### **Attributes for Images**:
- **`width` and `height`**: Specifies the dimensions of the image in pixels.
  ```html
  <img src="image.jpg" alt="Description" width="500" height="300">
  ```
- **`title`**: Provides additional information when the user hovers over the image.
  ```html
  <img src="image.jpg" alt="Description" title="This is a title">
  ```



## **5. Advanced Image Use**

1. **Responsive Images**:
   - Use the `srcset` attribute for different image sizes depending on the screen resolution or viewport width:
   ```html
   <img src="image-small.jpg" alt="Description" srcset="image-large.jpg 1024w, image-medium.jpg 640w">
   ```
   - This technique allows the browser to choose the appropriate image based on the device's screen size or resolution.

2. **Image Formats**:
   - **JPEG**: Commonly used for photographs.
   - **PNG**: Supports transparency; best for logos or images with sharp edges.
   - **GIF**: Supports animations.
   - **WebP**: Modern format offering high-quality compression with smaller file sizes (supported in most modern browsers).

3. **Lazy Loading**:
   - To improve page performance, load images only when they are in view using the `loading="lazy"` attribute:
   ```html
   <img src="image.jpg" alt="Description" loading="lazy">
   ```



## **6. Hyperlinks in HTML**

Hyperlinks allow users to navigate between pages or resources. The `<a>` (anchor) tag is used for creating hyperlinks.

```html
<a href="https://www.example.com">Visit Example</a>
```
- **`href`**: The attribute that defines the URL to link to.
- **Text** between the `<a>` tags is clickable.

### **2. Internal Linking**

Internal links allow navigation within the same website or domain.

```html
<a href="#section1">Go to Section 1</a>
```
- **`#section1`**: Refers to an ID within the same document.

## **7. Lists in HTML**

HTML supports ordered and unordered lists.

- **Unordered List**: Uses `<ul>` with `<li>` for list items.
```html
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
</ul>
```
- **Ordered List**: Uses `<ol>` for numbered items.
```html
<ol>
  <li>First item</li>
  <li>Second item</li>
</ol>
```

## **8. Special Characters in HTML**

Special characters, such as symbols and characters that have special meanings in HTML, can be displayed using **HTML entities**. For example:

- **`&lt;`**: Less than symbol (`<`)
- **`&gt;`**: Greater than symbol (`>`)
- **`&amp;`**: Ampersand (`&`)
- **`&quot;`**: Double quotation mark (`"`)
- **`&copy;`**: Copyright symbol (`©`)

These characters must be encoded to avoid conflicts with HTML tags.



## **9. Horizontal Rules in HTML**

A horizontal rule (line) is used to separate sections of content visually:

```html
<hr>
```

- The `<hr>` tag creates a thematic break, often displayed as a horizontal line.



## **10. Meta Elements in HTML**

Meta elements are placed in the `<head>` section of an HTML document and provide metadata like the document's character encoding, author, and description for SEO.

```html
<meta charset="UTF-8"> <!-- Character encoding -->
<meta name="author" content="John Doe">
<meta name="description" content="This is a sample page">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

- **`<meta charset="UTF-8">`**: Defines the character encoding.
- **`<meta name="description">`**: Gives a description for SEO.
- **`<meta name="viewport">`**: Controls the layout on mobile devices.



## **11. `<div>` and `<span>` Elements**

- **`<div>`**: A block-level element used to group other elements. It is often used for styling and layout purposes.
```html
<div>
  <p>This is a paragraph inside a div element.</p>
</div>
```

- **`<span>`**: An inline element used to style or group small sections of text or other inline elements.
```html
<p>This is a <span style="color:red;">red</span> word in a sentence.</p>
```



## **12. Tables in HTML**

Tables are used to organize data in rows and columns.

```html
<table>
  <tr>
    <th>Heading 1</th>
    <th>Heading 2</th>
  </tr>
  <tr>
    <td>Data 1</td>
    <td>Data 2</td>
  </tr>
</table>
```

- **`<table>`**: Creates the table.
- **`<tr>`**: Defines a table row.
- **`<th>`**: Defines a table header.
- **`<td>`**: Defines a table data cell.



## **13. Forms in HTML**

Forms are used to collect user input. The `<form>` tag contains various input fields like text boxes, checkboxes, and buttons.

```html
<form action="/submit" method="POST">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name">
  <input type="submit" value="Submit">
</form>
```

- **`action`**: Specifies where to send the form data.
- **`method`**: Defines the HTTP method (e.g., GET or POST).
- **`<input>`**: Defines an input field.



## **14. HTML5 Input Types**

HTML5 introduces new input types to enhance forms with validation and usability. Some key types:

1. **Textual Inputs**:
   - `text`: Standard text box.
   - `password`: Obscures user input.
   - `email`: Validates email format.
   - `url`: Validates URL format.
   ```html
   <input type="email" placeholder="Enter your email">
   ```

2. **Number-Based Inputs**:
   - `number`: Allows numeric input with optional `min` and `max`.
   - `range`: Slider for selecting numeric values.
   ```html
   <input type="number" min="0" max="100">
   <input type="range" min="0" max="100">
   ```

3. **Date and Time Inputs**:
   - `date`: Calendar-based date picker.
   - `datetime-local`: Combines date and time picker.
   ```html
   <input type="date">
   <input type="datetime-local">
   ```

4. **Specialized Inputs**:
   - `color`: Color picker.
   - `file`: File upload control.
   ```html
   <input type="color">
   <input type="file">
   ```

5. **Interactive Inputs**:
   - `search`: Optimized for search boxes.
   - `tel`: For telephone numbers.
   - `checkbox` and `radio`: Selection controls.
   ```html
   <input type="search" placeholder="Search here">
   ```



## **15. Input and Datalist**

The `<datalist>` element enhances input fields by providing predefined suggestions.

### **Example**:
```html
<form>
  <label for="fruit">Choose a fruit:</label>
  <input list="fruits" id="fruit" name="fruit">
  <datalist id="fruits">
    <option value="Apple">
    <option value="Banana">
    <option value="Cherry">
    <option value="Date">
  </datalist>
</form>
```

- **`<datalist>`**: Holds a list of options.
- **Linked to `<input>`** using the `list` attribute.

**Benefits**:
- Provides user-friendly autocomplete suggestions without requiring JavaScript.
- Customizable for any form input.



## **16. Elements and Autocomplete Attributes**

### **Elements of HTML Forms**
1. **Input Fields**:
   - Standard user-input fields like `text`, `password`, `email`.
2. **Labels**:
   - Associate text with inputs for accessibility.
   ```html
   <label for="username">Username:</label>
   <input id="username" type="text">
   ```

3. **Buttons**:
   - Submit (`submit`), Reset (`reset`), or Custom Buttons (`button`).
   ```html
   <button type="submit">Submit</button>
   ```

4. **Fieldsets and Legends**:
   - Group related form elements.
   ```html
   <fieldset>
     <legend>Personal Info</legend>
     <input type="text" placeholder="First Name">
   </fieldset>
   ```


### **Autocomplete Attribute**
The `autocomplete` attribute allows forms to store and autofill data.

- **Values**:
  - `on`: Enables autocomplete.
  - `off`: Disables autocomplete.

### Example:
```html
<form autocomplete="on">
  <label for="email">Email:</label>
  <input type="email" id="email" name="email">
</form>
```

**Autocomplete Field Values**:
- `name`, `email`, `username`, `new-password`, `tel`, `address-line1`, etc.



## **17. Page Structure Elements**

HTML5 introduces semantic elements for improved readability and SEO.

### **Common Structural Elements**:
1. **`<header>`**: Represents introductory content.
2. **`<nav>`**: Defines navigation links.
3. **`<main>`**: Main content area.
4. **`<section>`**: Groups related content.
5. **`<footer>`**: Footer for the page or a section.
6. **`<article>`**: Self-contained content (e.g., blog posts).
7. **`<aside>`**: Sidebar or complementary content.

### **Example of Page Structure**:
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>HTML5 Page</title>
</head>
<body>
  <header>
    <h1>Welcome to My Website</h1>
  </header>
  <nav>
    <a href="#home">Home</a>
    <a href="#about">About</a>
  </nav>
  <main>
    <section>
      <h2>About Us</h2>
      <p>We build websites!</p>
    </section>
    <aside>
      <p>Related Links</p>
    </aside>
  </main>
  <footer>
    <p>&copy; 2024 My Website</p>
  </footer>
</body>
</html>
```

## **18. Audio Element**

The `<audio>` element allows embedding sound files, with built-in controls for playback.

#### Basic Example:
```html
<audio controls>
  <source src="audiofile.mp3" type="audio/mpeg">
  Your browser does not support the audio element.
</audio>
```
- **Attributes**:
  - `controls`: Adds play, pause, and volume controls.
  - `autoplay`: Starts playback automatically.
  - `loop`: Repeats the audio.
  - `muted`: Starts muted.

#### Supported Formats:
- **MP3 (`audio/mpeg`)**: Widely supported.
- **OGG (`audio/ogg`)**: Open-source.
- **WAV (`audio/wav`)**: Uncompressed, high quality.



## **19. Video Element**

The `<video>` element embeds videos directly into web pages.

#### Basic Example:
```html
<video controls width="640" height="360">
  <source src="videofile.mp4" type="video/mp4">
  Your browser does not support the video element.
</video>
```
- **Attributes**:
  - `controls`: Adds playback options.
  - `autoplay`: Starts playing automatically.
  - `loop`: Repeats the video.
  - `poster`: Specifies an image to display before playback starts.
  - `muted`: Starts muted.

#### Supported Formats:
- **MP4 (`video/mp4`)**: Most commonly used.
- **WebM (`video/webm`)**: Open-source.
- **OGG (`video/ogg`)**: Older format.



## **20. Accessibility**
- Always provide fallback text for unsupported browsers.
- Include captions/subtitles using `<track>` within the `<video>` element.

#### Example:
```html
<video controls>
  <source src="movie.mp4" type="video/mp4">
  <track src="captions.vtt" kind="subtitles" srclang="en" label="English">
</video>
```



## **21. Styling and Customization**

Customize audio/video elements using CSS:
```css
audio, video {
  border: 2px solid #333;
  border-radius: 8px;
}
```

