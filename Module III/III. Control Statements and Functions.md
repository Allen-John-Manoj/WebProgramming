## **Control Statements in PHP**

Control statements allow you to dictate the flow of your PHP script based on conditions and loops. They enable your program to make decisions and repeat certain tasks.

### **1. Conditional Statements**
Conditional statements are used to execute different blocks of code based on certain conditions.

#### **if Statement**
The `if` statement executes a block of code if a condition is `true`.

Example:
```php
<?php
$age = 18;

if ($age >= 18) {
    echo "You are eligible to vote.";
}
?>
```
In this example, if `$age` is `18` or greater, it outputs: `You are eligible to vote.`

#### **if-else Statement**
The `if-else` statement provides an alternative block of code to execute when the condition is `false`.

Example:
```php
<?php
$age = 16;

if ($age >= 18) {
    echo "You are eligible to vote.";
} else {
    echo "You are not eligible to vote.";
}
?>
```
In this example, if `$age` is less than `18`, it outputs: `You are not eligible to vote.`

#### **elseif Statement**
The `elseif` statement allows you to check multiple conditions.

Example:
```php
<?php
$score = 75;

if ($score >= 90) {
    echo "Grade: A";
} elseif ($score >= 75) {
    echo "Grade: B";
} elseif ($score >= 60) {
    echo "Grade: C";
} else {
    echo "Grade: D";
}
?>
```
This code checks the value of `$score` and assigns a grade based on ranges.

#### **Switch Statement**
The `switch` statement is used to perform different actions based on multiple conditions. It’s an alternative to `if-elseif-else` chains when checking a single variable against multiple values.

Example:
```php
<?php
$day = "Tuesday";

switch ($day) {
    case "Monday":
        echo "Today is Monday.";
        break;
    case "Tuesday":
        echo "Today is Tuesday.";
        break;
    case "Wednesday":
        echo "Today is Wednesday.";
        break;
    default:
        echo "It’s another day.";
}
?>
```
The `switch` statement compares the value of `$day` against the cases and executes the matching block. If no cases match, it executes the `default` block.

---

### **2. Looping Statements**
Loops allow you to repeat a block of code as long as a specified condition is `true`.

#### **while Loop**
The `while` loop repeats a block of code as long as the condition is `true`.

Example:
```php
<?php
$i = 1;
while ($i <= 5) {
    echo "Number: $i <br>";
    $i++;
}
?>
```
In this example, the loop prints numbers from `1` to `5` and then stops.

#### **do-while Loop**
The `do-while` loop is similar to `while`, but it guarantees that the block of code runs at least once, even if the condition is `false`.

Example:
```php
<?php
$i = 6;
do {
    echo "Number: $i <br>";
    $i++;
} while ($i <= 5);
?>
```
Here, even though `$i` starts at `6`, the loop runs once before checking the condition, so it outputs: `Number: 6`.

#### **for Loop**
The `for` loop is ideal for executing a block of code a specific number of times.

Example:
```php
<?php
for ($i = 1; $i <= 5; $i++) {
    echo "The number is: $i <br>";
}
?>
```
This loop prints numbers from `1` to `5` and then stops.

#### **foreach Loop**
The `foreach` loop is specifically designed for iterating over arrays.

Example:
```php
<?php
$colors = ["Red", "Green", "Blue"];
foreach ($colors as $color) {
    echo "Color: $color <br>";
}
?>
```
This loop iterates through each element in the `$colors` array and outputs each color.

#### **break and continue**
- **`break`**: Exits the loop immediately.
- **`continue`**: Skips the current iteration and continues with the next.

Example with `break`:
```php
<?php
for ($i = 1; $i <= 10; $i++) {
    if ($i == 5) {
        break;  // Exit loop when $i is 5
    }
    echo "Number: $i <br>";
}
?>
```
This code stops the loop when `$i` reaches `5`.

Example with `continue`:
```php
<?php
for ($i = 1; $i <= 5; $i++) {
    if ($i == 3) {
        continue;  // Skip the iteration when $i is 3
    }
    echo "Number: $i <br>";
}
?>
```
This loop skips printing `3` but continues with other numbers.

---

## **Working with Functions in PHP**

Functions allow you to encapsulate a block of code that can be reused throughout your PHP script.

### **1. Defining and Calling Functions**

A function is defined using the `function` keyword, followed by the function name and parentheses `()`.

Example:
```php
<?php
function greet() {
    echo "Hello, World!";
}

greet();  // Output: Hello, World!
?>
```
In this example, the function `greet()` is defined and then called to output a greeting.

### **2. Functions with Parameters**
You can pass data to functions using parameters.

Example:
```php
<?php
function greetUser($name) {
    echo "Hello, $name!";
}

greetUser("Alice");  // Output: Hello, Alice!
greetUser("Bob");    // Output: Hello, Bob!
?>
```
The function `greetUser()` takes a parameter `$name` and uses it in the greeting.

### **3. Functions with Return Values**
A function can return a value using the `return` keyword.

Example:
```php
<?php
function add($a, $b) {
    return $a + $b;
}

$result = add(5, 7);
echo $result;  // Output: 12
?>
```
The `add()` function returns the sum of two numbers, which is then stored in the `$result` variable.

### **4. Default Parameter Values**
You can specify default values for parameters, making them optional when calling the function.

Example:
```php
<?php
function greet($name = "Guest") {
    echo "Hello, $name!";
}

greet();         // Output: Hello, Guest!
greet("Alice");  // Output: Hello, Alice!
?>
```
In this example, if no parameter is passed, `$name` defaults to `"Guest"`.

### **5. Using `return` for Multiple Values**
PHP functions can only return a single value directly, but you can return an array to get multiple values.

Example:
```php
<?php
function calculate($a, $b) {
    $sum = $a + $b;
    $difference = $a - $b;
    return [$sum, $difference];
}

list($sum, $difference) = calculate(10, 5);
echo "Sum: $sum, Difference: $difference";  // Output: Sum: 15, Difference: 5
?>
```
This function returns an array containing the sum and difference of two numbers, which can be unpacked using `list()`.

### **6. Variable Scope in Functions**
- **Local Scope**: Variables defined inside a function cannot be accessed outside.
- **Global Scope**: Variables defined outside a function cannot be accessed inside, unless specified using `global`.

Example:
```php
<?php
$globalVar = "I'm global!";

function showVar() {
    global $globalVar;
    echo $globalVar;  // Output: I'm global!
}

showVar();
?>
```
In this example, `global` allows access to the `$globalVar` inside the function.

---

### **Complete Example: Calculator with Functions and Control Statements**

```php
<?php
function calculator($a, $b, $operation) {
    switch ($operation) {
        case "add":
            return $a + $b;
        case "subtract":
            return $a - $b;
        case "multiply":
            return $a * $b;
        case "divide":
            if ($b == 0) {
                return "Cannot divide by zero.";
            }
            return $a / $b;
        default:
            return "Invalid operation.";
    }
}

echo calculator(10, 5, "add") . "<br>";       // Output: 15
echo calculator(10, 5, "subtract") . "<br>";  // Output: 5
echo calculator(10, 5, "multiply") . "<br>";  // Output: 50
echo calculator(10, 0, "divide") . "<br>";    // Output: Cannot divide by zero.
?>
```

### **Explanation:**
1. **Function Definition**: The `calculator()` function takes two numbers and an operation.
2. **Switch Statement**

: Chooses the appropriate calculation based on the operation.
3. **Error Handling**: Checks for division by zero and handles it gracefully.
4. **Function Calls**: Different operations are demonstrated using function calls.

---

This content provides a comprehensive and detailed guide to **Control Statements** and **Functions** in PHP, with numerous examples to ensure clarity. Each code snippet is wrapped in `<?php` and `?>` tags for easy copy-pasting and experimentation.
