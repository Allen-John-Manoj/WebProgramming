## **What is JSON Schema?**

- JSON Schema is a vocabulary that allows you to **validate**, **describe**, and **define the structure** of JSON data.
- It acts as a blueprint for your JSON objects, ensuring consistency and correctness.
- It acts smilar to forms, specifying what type of entries are allowed, it's contrainsts, and which are mandatory (to fill).


## **Purpose of JSON Schema**

1. **Validation**: Ensures JSON data adheres to a defined structure.
2. **Documentation**: Serves as documentation for APIs or data formats.
3. **Interoperability**: Promotes uniform data standards across systems.


## **Core Components of JSON Schema**

### 1. **Root Schema**
A JSON schema starts with a root object containing:
- `$schema`: The JSON Schema version used.
- `type`: The type of JSON data (`object`, `array`, `string`, etc.).

### Example:
```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "type": "object",
  "properties": {
    "name": {
      "type": "string"
    },
    "age": {
      "type": "integer",
      "minimum": 0
    }
  },
  "required": ["name"]
}
```

### 2. **Properties**
Defines the structure and constraints of fields within an object.

**Example:**
```json
{
  "properties": {
    "email": {
      "type": "string",
      "format": "email"
    }
  }
}
```

- `format`: Validates specific formats like `email`, `date`, etc.


### 3. **Type**
Specifies the expected data type for fields.

**Valid Types:**
- `string`
- `number`
- `integer`
- `object`
- `array`
- `boolean`
- `null`

**Example:**
```json
{
  "type": "string"
}
```

### 4. **Required Fields**
Defines mandatory fields in the JSON data.

**Example:**
```json
{
  "required": ["name", "email"]
}
```

### 5. **Constraints**
Defines additional rules for fields:
- **`minLength` and `maxLength`**: For strings.
- **`minimum` and `maximum`**: For numbers.
- **`pattern`**: Regex for string validation.

**Example:**
```json
{
  "properties": {
    "password": {
      "type": "string",
      "minLength": 8
    },
    "age": {
      "type": "integer",
      "minimum": 18
    }
  }
}
```

### 6. **Nested Objects**
Schemas can validate nested objects or arrays.

**Example:**
```json
{
  "type": "object",
  "properties": {
    "address": {
      "type": "object",
      "properties": {
        "street": {
          "type": "string"
        },
        "city": {
          "type": "string"
        }
      },
      "required": ["street"]
    }
  }
}
```

## **Tools for JSON Schema Validation**
1. **Online Validators**: Tools like [JSON Schema Validator](https://www.jsonschemavalidator.net/) let you test schemas online.
2. **Programming Libraries**:
   - JavaScript: `ajv`, `joi`
   - Python: `jsonschema`
   - PHP: `justinrainbow/json-schema`

---

## **Manipulating JSON Data in PHP**

PHP provides built-in functions to handle JSON, enabling you to parse, generate, and manipulate JSON data.

## **PHP Functions for JSON**

### 1. `json_encode()`
Converts a PHP array or object to a JSON string.

**Example:**
```php
$data = [
    "name" => "Alice",
    "age" => 25,
    "skills" => ["PHP", "JavaScript"]
];

$json = json_encode($data);
echo $json;
```

**Output:**
```json
{"name":"Alice","age":25,"skills":["PHP","JavaScript"]}
```

### 2. `json_decode()`
Converts a JSON string into a PHP object or array.

**Example:**
```php
$json = '{"name":"Alice","age":25,"skills":["PHP","JavaScript"]}';
$data = json_decode($json, true); // true returns an associative array

echo $data["name"]; // Alice
```

---

## **Working with JSON Files**

### Reading JSON from a File
```php
$json = file_get_contents('data.json');
$data = json_decode($json, true);
print_r($data);
```

### Writing JSON to a File
```php
$data = [
    "name" => "Alice",
    "age" => 25
];

$json = json_encode($data, JSON_PRETTY_PRINT);
file_put_contents('data.json', $json);
```

---

## **Error Handling**

PHP provides the `json_last_error()` function to detect errors in JSON processing.

**Example:**
```php
$json = '{"name": "Alice", "age": 25'; // Invalid JSON

$data = json_decode($json);
if (json_last_error() !== JSON_ERROR_NONE) {
    echo "Error: " . json_last_error_msg();
}
```

**Common Errors:**
- **JSON_ERROR_SYNTAX**: Malformed JSON.
- **JSON_ERROR_DEPTH**: Maximum stack depth exceeded.

---

## **Advanced JSON Options**

### Pretty-Print JSON
```php
$json = json_encode($data, JSON_PRETTY_PRINT);
echo $json;
```
Without `JSON_PRETTY_PRINT`, the JSON would be output in a compact form like:

```json
{"name":"John","age":30,"city":"New York"}
```
With `JSON_PRETTY_PRINT`,
```json
{
    "name": "John",
    "age": 30,
    "city": "New York"
}
```

### Summary
- **`JSON_PRETTY_PRINT`** makes the JSON output more readable by adding newlines and indentation.
- It is typically used for debugging or when you want to present the JSON in a format that’s easier for humans to read.

### Handling Special Characters
Use `JSON_UNESCAPED_UNICODE` and `JSON_UNESCAPED_SLASHES` for symbols beyond ASCII (including non-english symbols).

**Example:**
```php
$data = ["name" => "José", "url" => "https://example.com/"];
$json = json_encode($data, JSON_UNESCAPED_UNICODE | JSON_UNESCAPED_SLASHES);
echo $json;
```

**Output:**
```json
{"name":"José","url":"https://example.com/"}
```
Without using it, the output will look like

```json
{"name":"Jos\u00e9","url":"https:\/\/example.com\/"}
```
---

## **Manipulating JSON Data**

### Adding New Data
```php
$data = json_decode($json, true);
$data["email"] = "alice@example.com";

$json = json_encode($data);
```

### Updating Data
```php
$data = json_decode($json, true);
$data["age"] = 30;

$json = json_encode($data);
```

### Deleting Data
```php
$data = json_decode($json, true);
unset($data["age"]);

$json = json_encode($data);
```

---

## **Combining PHP and JSON Schema Validation**

To validate JSON data using a schema in PHP, you can use the `justinrainbow/json-schema` library.

#### Installation (via Composer)
```bash
composer require justinrainbow/json-schema
```

### Validation Example
```php
// Include the Composer autoloader to automatically load required dependencies
require 'vendor/autoload.php';

// Import the JsonSchema Validator class to perform validation
use JsonSchema\Validator;

// Define a JSON Schema for validating data. This schema expects an object with:
// - a string property 'name'
// - an integer property 'age' (must be at least 18)
// The 'required' array specifies that both 'name' and 'age' must be present in the data.

$schema = (object)[      //Specify datatype is an object
    '$schema' => 'https://json-schema.org/draft/2020-12/schema',  // Declare the JSON Schema version being used
    'type' => 'object',  
    'properties' => (object)[  
        'name' => (object)['type' => 'string'],  
        'age' => (object)['type' => 'integer', 'minimum' => 18] 
    ],
    'required' => ['name', 'age']  
];

$data = json_decode('{"name": "Alice", "age": 25}'); // JSON data to be validated. Creates an associative array

$validator = new Validator();  //Create a Validator object instance

$validator->validate($data, $schema);

if ($validator->isValid()) {    // Check if the data is valid according to the schema
    echo "JSON is valid!";
} else {
    echo "JSON validation failed:";
    foreach ($validator->getErrors() as $error) {
        echo "- {$error['property']}: {$error['message']}\n";   // Print each error
    } 
}

```

---

## **Common Use Cases**

### API Communication
```php
header('Content-Type: application/json');

$response = [
    "status" => "success",
    "data" => [
        "id" => 1,
        "name" => "Alice"
    ]
];

echo json_encode($response);
```

### Configuration Management
```php
$config = json_decode(file_get_contents('config.json'), true);
echo $config['database']['host'];
```
