# **Introduction to JavaScript**

JavaScript is a **high-level, interpreted programming language** commonly used in web development to create dynamic and interactive user experiences. It is a core technology of the web alongside HTML and CSS.

---

## **Why Learn JavaScript?**

- **Client-Side Behavior**: Runs directly in the browser, enabling dynamic content updates without server interaction.
- **Cross-Platform**: Works on all modern web browsers.
- **Event-Driven**: Allows interaction through events like clicks, key presses, or form submissions.
- **Wide Usage**: Used for front-end frameworks (React, Angular, Vue) and back-end (Node.js).

---

## **Introduction to Scripting**

### **What is Scripting?**
Scripting refers to writing small programs (scripts) to automate tasks or add interactivity. JavaScript scripts are embedded into web pages to manipulate HTML and CSS dynamically.

#### **Example of a Script in HTML**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>JavaScript Example</title>
</head>
<body>
    <h1 id="greeting">Hello, World!</h1>
    <button onclick="changeGreeting()">Click Me</button>

    <script>
        function changeGreeting() {
            document.getElementById("greeting").innerText = "You clicked the button!";
        }
    </script>
</body>
</html>
```

#### **Explanation**
- JavaScript is written inside `<script>` tags or in external files linked with `<script src="file.js"></script>`.
- The `onclick` attribute calls the `changeGreeting` function when the button is clicked.

---

## **Programming Fundamentals of JavaScript**

### **1. Variables**
Variables are containers for storing data values.

#### **Declaration**
- `var`: Function-scoped (older syntax).
- `let`: Block-scoped.
- `const`: Block-scoped and immutable.

#### Example:
```javascript
let name = "Alice"; // String
const age = 25; // Number
var isStudent = true; // Boolean
```

---

### **2. Data Types**
JavaScript supports several data types:
- **Primitive**: String, Number, Boolean, Null, Undefined, Symbol.
- **Non-Primitive**: Object (includes arrays and functions).

#### Example:
```javascript
let stringType = "Hello";
let numberType = 42;
let booleanType = true;
let nullType = null;
let undefinedType; // Declared but not assigned
let arrayType = [1, 2, 3];
let objectType = { name: "Alice", age: 25 };
```

---

### **3. Operators**
- **Arithmetic**: `+`, `-`, `*`, `/`, `%`
- **Comparison**: `==`, `===`, `!=`, `!==`, `<`, `>`, `<=`, `>=`
- **Logical**: `&&`, `||`, `!`

#### Example:
```javascript
let a = 10, b = 20;
let sum = a + b; // 30
let isEqual = a === b; // false
let logical = (a < b) && (b > 15); // true
```

---

### **4. Conditional Statements**
Control the flow of execution based on conditions.

#### **If-Else Example**
```javascript
let age = 18;
if (age >= 18) {
    console.log("You are an adult.");
} else {
    console.log("You are a minor.");
}
```

#### **Switch Example**
```javascript
let day = 3;
switch (day) {
    case 1:
        console.log("Monday");
        break;
    case 2:
        console.log("Tuesday");
        break;
    default:
        console.log("Other day");
}
```

---

### **5. Loops**
Execute code repeatedly based on conditions.

#### **For Loop**
```javascript
for (let i = 0; i < 5; i++) {
    console.log("Count:", i);
}
```

#### **While Loop**
```javascript
let count = 0;
while (count < 5) {
    console.log("Count:", count);
    count++;
}
```

---

### **6. Functions**
Reusable blocks of code that perform specific tasks.

#### **Declaration**
```javascript
function greet(name) {
    return `Hello, ${name}!`;
}
console.log(greet("Alice"));
```

#### **Arrow Function (ES6)**
```javascript
const greet = (name) => `Hello, ${name}!`;
console.log(greet("Bob"));
```

---

## **Obtaining User Input with `prompt` Dialogs**

### **What is `prompt`?**
The `prompt()` function is used to obtain input from the user. It opens a dialog box where the user can type a response.

### **Syntax**
```javascript
let userInput = prompt("Enter your name:");
```

- The `prompt()` function takes one argument:
  - A string displayed as the message in the dialog.
- The return value is the user's input as a string. If the user cancels, it returns `null`.

### **Example: Greeting the User**
```javascript
let name = prompt("What is your name?");
if (name) {
    alert(`Hello, ${name}! Welcome to our site.`);
} else {
    alert("You didn't enter a name.");
}
```

---

### **Example: Simple Calculator**
```javascript
let num1 = parseFloat(prompt("Enter the first number:"));
let num2 = parseFloat(prompt("Enter the second number:"));
let operation = prompt("Enter the operation (+, -, *, /):");

let result;
switch (operation) {
    case "+":
        result = num1 + num2;
        break;
    case "-":
        result = num1 - num2;
        break;
    case "*":
        result = num1 * num2;
        break;
    case "/":
        result = num1 / num2;
        break;
    default:
        alert("Invalid operation!");
}

if (result !== undefined) {
    alert(`The result is: ${result}`);
}
```
---

## **Arithmetic in JavaScript**

Arithmetic operations allow you to perform basic mathematical calculations. JavaScript provides operators to handle numbers and perform operations such as addition, subtraction, multiplication, division, and more.

### **Arithmetic Operators**

- **Addition (`+`)**: Adds two operands.
- **Subtraction (`-`)**: Subtracts the second operand from the first.
- **Multiplication (`*`)**: Multiplies two operands.
- **Division (`/`)**: Divides the first operand by the second.
- **Modulus (`%`)**: Returns the remainder of the division.
- **Exponentiation (`**`)**: Raises the first operand to the power of the second operand (ES6).
- **Increment (`++`)**: Increases a number by one.
- **Decrement (`--`)**: Decreases a number by one.

### **Examples of Arithmetic Operations**

```javascript
let a = 10, b = 5;

// Addition
let sum = a + b; // 15

// Subtraction
let difference = a - b; // 5

// Multiplication
let product = a * b; // 50

// Division
let quotient = a / b; // 2

// Modulus
let remainder = a % b; // 0 (no remainder)

// Exponentiation
let power = a ** 2; // 100 (10 squared)

// Increment
let increment = a++; // 10 (then a becomes 11)

// Decrement
let decrement = b--; // 5 (then b becomes 4)
```

---

## **Decision Making in JavaScript**

Decision-making statements allow your program to make decisions based on conditions. The primary decision-making constructs in JavaScript are **`if`**, **`else if`**, **`else`**, and **`switch`**.

### **1. `if` Statement**

The `if` statement evaluates a condition and executes a block of code if the condition is true.

#### Syntax:
```javascript
if (condition) {
    // code block if condition is true
}
```

#### Example:
```javascript
let age = 18;
if (age >= 18) {
    console.log("You are an adult.");
}
```

### **2. `else` Statement**

The `else` statement executes a block of code if the `if` condition is false.

#### Syntax:
```javascript
if (condition) {
    // code block if condition is true
} else {
    // code block if condition is false
}
```

#### Example:
```javascript
let age = 16;
if (age >= 18) {
    console.log("You are an adult.");
} else {
    console.log("You are a minor.");
}
```

### **3. `else if` Statement**

The `else if` statement allows you to test multiple conditions. If the first condition is false, it will test the next condition.

#### Syntax:
```javascript
if (condition1) {
    // code block if condition1 is true
} else if (condition2) {
    // code block if condition2 is true
} else {
    // code block if neither condition1 nor condition2 is true
}
```

#### Example:
```javascript
let day = 2;
if (day === 1) {
    console.log("Monday");
} else if (day === 2) {
    console.log("Tuesday");
} else {
    console.log("Other day");
}
```

### **4. `switch` Statement**

The `switch` statement tests a variable or expression against multiple values and executes the corresponding block of code.

#### Syntax:
```javascript
switch (expression) {
    case value1:
        // code block for value1
        break;
    case value2:
        // code block for value2
        break;
    default:
        // code block if no match
}
```

#### Example:
```javascript
let day = 3;
switch (day) {
    case 1:
        console.log("Monday");
        break;
    case 2:
        console.log("Tuesday");
        break;
    case 3:
        console.log("Wednesday");
        break;
    default:
        console.log("Invalid day");
}
```

### **5. Ternary Operator (Shortened if-else)**

The **ternary operator** is a shorthand for `if-else`. It returns one of two values based on the condition.

#### Syntax:
```javascript
condition ? valueIfTrue : valueIfFalse;
```

#### Example:
```javascript
let age = 20;
let result = (age >= 18) ? "Adult" : "Minor";
console.log(result); // "Adult"
```

---

## **Control Statements in JavaScript**

Control statements in JavaScript determine the flow of the program execution. They include looping and branching constructs that guide the flow based on conditions and repetitions.

### **1. `for` Loop**

The `for` loop is used when you know the number of iterations in advance.

#### Syntax:
```javascript
for (let i = 0; i < n; i++) {
    // code block
}
```

#### Example:
```javascript
for (let i = 1; i <= 5; i++) {
    console.log(i); // Prints numbers 1 to 5
}
```

### **2. `while` Loop**

The `while` loop repeats a block of code as long as the condition is true.

#### Syntax:
```javascript
while (condition) {
    // code block
}
```

#### Example:
```javascript
let i = 1;
while (i <= 5) {
    console.log(i); // Prints numbers 1 to 5
    i++;
}
```

### **3. `do...while` Loop**

The `do...while` loop is similar to the `while` loop, but the code block runs at least once, even if the condition is false.

#### Syntax:
```javascript
do {
    // code block
} while (condition);
```

#### Example:
```javascript
let i = 1;
do {
    console.log(i); // Prints numbers 1 to 5
    i++;
} while (i <= 5);
```

### **4. `break` Statement**

The `break` statement is used to exit a loop or a `switch` statement prematurely.

#### Example (in a loop):
```javascript
for (let i = 0; i < 10; i++) {
    if (i === 5) {
        break; // Exits the loop when i equals 5
    }
    console.log(i);
}
```

### **5. `continue` Statement**

The `continue` statement skips the current iteration of a loop and continues to the next iteration.

#### Example (in a loop):
```javascript
for (let i = 0; i < 10; i++) {
    if (i === 5) {
        continue; // Skips the iteration when i equals 5
    }
    console.log(i);
}
```

---

### **Summary of Concepts**

1. **Arithmetic**:
   - JavaScript provides basic arithmetic operators such as `+`, `-`, `*`, `/`, `%`, and `**` to perform mathematical calculations.

2. **Decision Making**:
   - JavaScript uses `if`, `else`, `else if`, and `switch` statements to make decisions based on conditions.

3. **Control Statements**:
   - **Loops**: `for`, `while`, and `do...while` loops allow repeating code.
   - **Loop Control**: Use `break` to exit a loop early and `continue` to skip an iteration.
