## **1. Arrays in PHP**

An **array** in PHP is a special variable that allows you to store multiple values under a single name. PHP supports three primary types of arrays: **Indexed arrays**, **Associative arrays**, and **Multidimensional arrays**.

### **1.1 Indexed Arrays**
Indexed arrays use numeric indices, starting from `0` by default, to access their elements.

#### **Creating an Indexed Array**
- **Example**:
    ```php
    <?php
    // Using the array() function
    $cars = array("Volvo", "BMW", "Toyota");

    // Using the short array syntax (preferred)
    $colors = ["Red", "Green", "Blue"];

    // Displaying the array
    var_dump($cars);
    ?>
    ```

#### **Accessing Indexed Array Elements**
- **Example**:
    ```php
    <?php
    $cars = array("Volvo", "BMW", "Toyota");

    // Access the first element
    echo $cars[0];  // Output: Volvo

    // Access the third element
    echo $cars[2];  // Output: Toyota
    ?>
    ```

#### **Modifying Indexed Array Elements**
- **Example**:
    ```php
    <?php
    $cars = array("Volvo", "BMW", "Toyota");

    // Change the second element
    $cars[1] = "Ford";

    // Display updated array
    var_dump($cars);
    ?>
    ```

#### **Adding Items to Indexed Arrays**
- **Example**:
    ```php
    <?php
    $cars = ["Volvo", "BMW"];
    $cars[] = "Toyota";  // Adds "Toyota" at the next index

    // Using array_push() to add multiple items
    array_push($cars, "Honda", "Chevrolet");

    var_dump($cars);
    ?>
    ```

#### **Looping Through an Indexed Array**
- **Example**:
    ```php
    <?php
    $cars = ["Volvo", "BMW", "Toyota"];

    // Using foreach loop to print each car
    foreach ($cars as $car) {
        echo "$car <br>";
    }
    ?>
    ```

#### **Removing Items from Indexed Arrays**
- **Example**:
    ```php
    <?php
    $cars = ["Volvo", "BMW", "Toyota"];
    
    // Remove the last item
    array_pop($cars);  // Removes "Toyota"

    // Remove the first item
    array_shift($cars);  // Removes "Volvo"

    var_dump($cars);  // Output: array(1) { [0]=> string(3) "BMW" }
    ?>
    ```

---

### **1.2 Associative Arrays**
Associative arrays use named keys instead of numeric indices. They are ideal for storing data in key-value pairs.

#### **Creating an Associative Array**
- **Example**:
    ```php
    <?php
    $person = array(
        "name" => "John",
        "age" => 30,
        "city" => "New York"
    );

    // Using short syntax
    $car = [
        "brand" => "Ford",
        "model" => "Mustang",
        "year" => 1964
    ];

    var_dump($person);
    ?>
    ```

#### **Accessing Associative Array Elements**
- **Example**:
    ```php
    <?php
    echo $car["brand"];  // Output: Ford
    echo $car["year"];   // Output: 1964
    ?>
    ```

#### **Modifying Associative Arrays**
- **Example**:
    ```php
    <?php
    $car = [
        "brand" => "Ford",
        "model" => "Mustang",
        "year" => 1964
    ];

    // Change the year
    $car["year"] = 2024;

    var_dump($car);
    ?>
    ```

#### **Adding Items to Associative Arrays**
- **Example**:
    ```php
    <?php
    $car = [
        "brand" => "Ford",
        "model" => "Mustang"
    ];

    // Add a new key-value pair
    $car["color"] = "Red";

    // Adding multiple items using +=
    $car += ["engine" => "V8", "doors" => 2];

    var_dump($car);
    ?>
    ```

#### **Looping Through an Associative Array**
- **Example**:
    ```php
    <?php
    $car = [
        "brand" => "Ford",
        "model" => "Mustang",
        "year" => 2024
    ];

    // Using foreach loop to display keys and values
    foreach ($car as $key => $value) {
        echo "$key: $value <br>";
    }
    ?>
    ```

#### **Removing Items from Associative Arrays**
- **Example**:
    ```php
    <?php
    $car = [
        "brand" => "Ford",
        "model" => "Mustang",
        "year" => 2024
    ];

    // Remove an item using unset()
    unset($car["model"]);

    var_dump($car);  // Output: array(2) { ["brand"]=> string(4) "Ford" ["year"]=> int(2024) }
    ?>
    ```

---

### **1.3 Multidimensional Arrays**
Multidimensional arrays are arrays that contain other arrays. They are useful for storing data structures like tables or matrices.

#### **Creating a Multidimensional Array**
- **Example**:
    ```php
    <?php
    $cars = [
        ["Volvo", 22, 18],
        ["BMW", 15, 13],
        ["Toyota", 17, 20]
    ];

    var_dump($cars);
    ?>
    ```

#### **Accessing Elements in a Multidimensional Array**
- **Example**:
    ```php
    <?php
    echo $cars[0][0];  // Output: Volvo
    echo $cars[1][2];  // Output: 13
    ?>
    ```

#### **Looping Through a Multidimensional Array**
- **Example**:
    ```php
    <?php
    foreach ($cars as $car) {
        echo $car[0] . " - Stock: " . $car[1] . ", Sold: " . $car[2] . "<br>";
    }
    ?>
    ```

### **1.4 Array Functions Overview**
PHP arrays come with numerous built-in functions for easy manipulation:

- `array_merge():` Combine arrays.
- `array_keys():` Get all keys of an array.
- `array_values():` Get all values of an array.
- `sort()` and `asort():` Sort arrays.
- `array_key_exists():` Check if a key exists in an array.

---

## **2. Objects in PHP**

Objects in PHP are instances of classes, providing a way to model real-world entities with properties and methods. PHP's support for **Object-Oriented Programming (OOP)** enables the creation of reusable and organized code.

### **2.1 Creating a Class and Object**

A **class** acts as a blueprint for creating **objects**. Classes can contain **properties** (variables) and **methods** (functions).

- **Defining a Class**:
    ```php
    <?php
    class Car {
        public $brand;
        public $color;

        // Constructor method
        public function __construct($brand, $color) {
            $this->brand = $brand;
            $this->color = $color;
        }

        // Method
        public function start() {
            return "The $this->color $this->brand is starting.";
        }
    }
    ?>
    ```

- **Creating an Object**:
    ```php
    <?php
    $myCar = new Car("Toyota", "Red");
    echo $myCar->start();  // Output: The Red Toyota is starting.
    ?>
    ```

### **2.2 Properties and Methods**

- **Properties** are variables defined inside a class.
- **Methods** are functions defined inside a class.

- **Example**:
    ```php
    <?php
    class Person {
        public $name;
        private $age;

        public function __construct($name, $age) {
            $this->name = $name;
            $this->age = $age;
        }

        public function greet() {
            return "Hello, my name is $this->name.";
        }

        private function getAge() {
            return $this->age;
        }
    }

    $person = new Person("Alice", 30);
    echo $person->greet();  // Output: Hello, my name is Alice.
    ?>
    ```

### **2.3 Access Modifiers**

PHP classes use **access modifiers** to define visibility:
- **`public`**: Accessible from anywhere.
- **`protected`**: Accessible within the class and by derived classes.
- **`private`**: Accessible only within the class.

### **2.4 Inheritance**

**Inheritance** allows a class to inherit properties and methods from another class using the `extends` keyword.

- **Example**:
    ```php
    <?php
    class Animal {
        public function sound() {
            return "Some generic sound";
        }
    }

    class Dog extends Animal {
        public function sound() {
            return "Woof!";
        }
    }

    $dog = new Dog();
    echo $dog->sound();  // Output: Woof!
    ?>
    ```

### **2.5 Polymorphism**

**Polymorphism** allows different classes to be treated through a common interface.

- **Example**:
    ```php
    <?php
    class Cat extends Animal {
        public function sound() {
            return "Meow!";
        }
    }

    $animals = [new Dog(), new Cat(), new Animal()];
    foreach ($animals as $animal) {
        echo $animal->sound() . "<br>";
    }
    ?>
    ```

---
