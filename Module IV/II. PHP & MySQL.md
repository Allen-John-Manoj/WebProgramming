## **1. Introduction to PHP and MySQL Integration**

**PHP** and **MySQL** are commonly used together to create dynamic, data-driven web applications. MySQL serves as the database management system (DBMS) where data is stored, while PHP acts as the server-side scripting language to interact with MySQL, process queries, and display results to users.

### **1.1 Why Use PHP with MySQL?**
- **Open Source**: Both PHP and MySQL are open-source technologies, making them cost-effective.
- **Cross-Platform Compatibility**: PHP and MySQL can run on various operating systems like Windows, Linux, and macOS.
- **Wide Adoption**: Many popular content management systems (CMS) like WordPress, Joomla, and Drupal use PHP and MySQL.
- **Ease of Use**: PHP provides functions like `mysql_connect()` for easy integration with MySQL databases.

---

## **2. Connecting to MySQL Database with PHP**

To connect PHP to a MySQL database, we use the `mysql_connect()` function along with other functions like `mysql_select_db()` to select a database.

### **2.1 Connecting to MySQL**

**Syntax of `mysql_connect()`**:
```php
mysql_connect(servername, username, password);
```

- **`servername`**: The hostname where the MySQL server is running, usually `"localhost"` for local development.
- **`username`**: The username used to log into the MySQL server (e.g., `"root"`).
- **`password`**: The password for the specified user.

### **Example: Establishing a MySQL Connection**
```php
<?php
$servername = "localhost";
$username = "root";
$password = "";

// Establishing a connection to MySQL
$conn = mysql_connect($servername, $username, $password);

// Check if the connection is successful
if (!$conn) {
    die("Connection failed: " . mysql_error());
} else {
    echo "Connected successfully to MySQL!";
}
?>
```

### **Explanation**:
- **`mysql_connect()`**: Establishes a connection to the MySQL server using the specified credentials.
- **`mysql_error()`**: Returns a string describing the last MySQL error, useful for debugging connection issues.
- **`die()`**: Terminates the script if the connection fails, displaying the error message.

### **2.2 Selecting a MySQL Database**

After establishing a connection, you must select the database you wish to use with `mysql_select_db()`.

**Syntax of `mysql_select_db()`**:
```php
mysql_select_db(database_name, connection);
```

- **`database_name`**: The name of the database you want to select.
- **`connection`**: The connection identifier returned by `mysql_connect()`.

**Example: Selecting a Database**:
```php
<?php
$database = "my_database";

// Select the database
if (!mysql_select_db($database, $conn)) {
    die("Database selection failed: " . mysql_error());
} else {
    echo "Database selected successfully!";
}
?>
```

### **Explanation**:
- **`mysql_select_db()`**: Chooses the database where SQL queries will be executed.
- **Database Selection**: If the selection fails, the script terminates with an error message.

---

## **3. Executing SQL Queries**

Once the connection is established and a database is selected, you can perform various SQL operations such as **INSERT**, **SELECT**, **UPDATE**, and **DELETE** using the `mysql_query()` function (next chapter).

## **4. Fetching Data from MySQL**

### **4.1 Using `mysql_fetch_array()`**

`mysql_fetch_array()` fetches a row from the result set as both an associative array and a numeric array.

**Example**:
```php
<?php
$sql = "SELECT * FROM users";
$result = mysql_query($sql, $conn);

while ($row = mysql_fetch_array($result)) {
    echo "User ID: " . $row[0] . " - " . $row['id'] . "<br>";
    echo "Username: " . $row[1] . " - " . $row['username'] . "<br>";
}
?>
```

### **4.2 Using `mysql_fetch_row()`**

`mysql_fetch_row()` fetches a row as a numerical array.

**Example**:
```php
<?php
$sql = "SELECT * FROM users";
$result = mysql_query($sql, $conn);

while ($row = mysql_fetch_row($result)) {
    echo "User ID: " . $row[0] . "<br>";  // Accessing using numeric index
    echo "Username: " . $row[1] . "<br>";
}
?>
```

### **4.3 Using `mysql_fetch_assoc()`**

`mysql_fetch_assoc()` fetches a row from the result set as an associative array, commonly used..

**Example**:
```php
<?php
$sql = "SELECT * FROM users";
$result = mysql_query($sql, $conn);

while ($row = mysql_fetch_assoc($result)) {
    echo "User ID: ". $row['id'] . "<br>";
    echo "Username: ". $row['username'] . "<br>";
}
?>
```

---

## **5. Closing the MySQL Connection**

It’s important to close the MySQL connection when you are done with database operations to free up resources.

**Example: Closing the Connection**:
```php
<?php
mysql_close($conn); // Close the MySQL connection
?>
```

---

## **6. Error Handling in MySQL**

Error handling is crucial when working with databases. It helps in identifying issues during the connection, query execution, or data retrieval process.

### **6.1 Using `mysql_error()`**

`mysql_error()` returns the error message from the last MySQL operation.

**Example: Error Handling**:
```php
<?php
$sql = "SELECT * FROM non_existing_table";
$result = mysql_query($sql, $conn);

if (!$result) {
    echo "Error executing query: " . mysql_error();
}
?>
```

### **6.2 Common Errors in PHP-MySQL Integration**
- **Connection Errors**: Incorrect credentials or database server not running.
- **Query Errors**: Syntax errors in SQL or referring to a non-existent table.
- **Data Type Mismatch**: Inserting string values into integer fields.

---

## **7. Summary of PHP-MySQL Integration**

### **Overview of Functions**
| Function              | Description                                                   |
|-----------------------|---------------------------------------------------------------|
| `mysql_connect()`     | Establishes a connection to the MySQL server.                 |
| `mysql_select_db()`   | Selects the database to use.                                  |
| `mysql_query()`       | Executes an SQL query on the selected database.               |
| `mysql_fetch_assoc()` | Retrieves a result row as an associative array.               |
| `mysql_fetch_array()` | Retrieves a result row as both an associative and numeric array. |
| `mysql_fetch_row()`   | Retrieves a result row as a numeric array.                    |
| `mysql_close()`       | Closes the MySQL database connection.                         |
| `mysql_error()`       | Returns the error message for the last MySQL operation.       |

- **Always Close Connections**: Use `mysql_close()` to close connections when done.
---
