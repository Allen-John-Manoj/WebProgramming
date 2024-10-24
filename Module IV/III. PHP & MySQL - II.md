# **1. Introduction to SQL**

**SQL** (Structured Query Language) is the standard language used to interact with databases like MySQL. It allows you to **create**, **read**, **update**, and **delete** data (commonly referred to as **CRUD** operations). SQL commands are divided into different categories based on their functionality:

## **1.1 SQL Categories: DDL and DML**

1. **Data Definition Language (DDL)**:
   - **Purpose**: DDL commands are used to define the structure of a database, including creating and modifying tables.
   - **Common DDL Commands**:
     - **`CREATE`**: Creates a new database or table.
     - **`ALTER`**: Modifies an existing database or table.
     - **`DROP`**: Deletes a database or table.
     - **`TRUNCATE`**: Removes all records from a table without deleting the table structure.

2. **Data Manipulation Language (DML)**:
   - **Purpose**: DML commands are used for managing data within tables, including inserting, updating, and deleting records.
   - **Common DML Commands**:
     - **`INSERT`**: Adds new records to a table.
     - **`UPDATE`**: Modifies existing records.
     - **`DELETE`**: Removes records from a table.
     - **`SELECT`**: Retrieves data from a database (not covered in depth here as per your request).

---

# **2. Data Definition Language (DDL) with PHP**

## **2.1 Creating a MySQL Database**

**SQL Command for Creating a Database**:
```sql
CREATE DATABASE my_database;
```

**Example: Creating a Database with PHP**:
```php
<?php
$servername = "localhost";
$username = "root";
$password = "";

// Establish connection
$conn = mysql_connect($servername, $username, $password);
if (!$conn) {
    die("Connection failed: " . mysql_error());
}

// SQL to create a database
$sql = "CREATE DATABASE my_database";
if (mysql_query($sql, $conn)) {
    echo "Database created successfully!";
} else {
    echo "Error creating database: " . mysql_error();
}

// Close connection
mysql_close($conn);
?>
```

## **2.2 Creating a Table in MySQL**

After creating a database, you need to create tables to store data. Tables consist of rows and columns, where each column represents a field and each row represents a record.

**SQL Command for Creating a Table**:
```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL,
    password VARCHAR(255) NOT NULL
);
```

**Example: Creating a Table with PHP**:
```php
<?php
$conn = mysql_connect("localhost", "root", "");
mysql_select_db("my_database", $conn);

// SQL to create a 'users' table
$sql = "CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL,
    password VARCHAR(255) NOT NULL
)";

if (mysql_query($sql, $conn)) {
    echo "Table 'users' created successfully!";
} else {
    echo "Error creating table: " . mysql_error();
}

mysql_close($conn);
?>
```

### **Explanation**:
- **`mysql_connect()`**: Connects to the MySQL server.
- **`mysql_select_db()`**: Selects the database where the table will be created.
- **`CREATE TABLE`**: Creates a new table with specified columns and data types.
- **`AUTO_INCREMENT`**: Automatically increments the `id` field for each new record.

---

# **3. Data Manipulation Language (DML) with PHP**
Continuing from the previous discussion on working with MySQL data in PHP, let's delve into **performing `SELECT` and `UPDATE` operations** on a MySQL table using PHP. These operations are fundamental for interacting with database records: **`SELECT`** for retrieving data, and **`UPDATE`** for modifying existing data.

---

## **3.1. Performing SELECT Operations on MySQL Table**

The `SELECT` statement is used to retrieve data from one or more tables in a MySQL database. It is part of **Data Manipulation Language (DML)** and allows you to read data stored in the database. With `SELECT`, you can retrieve all or specific rows based on conditions.

### **3.1.1 Basic SELECT Query**

**SQL Command for Selecting All Records**:
```sql
SELECT * FROM users;
```

**Example: Fetching All Records with PHP**:
```php
<?php
// Database connection
$conn = mysql_connect("localhost", "root", "");
mysql_select_db("my_database", $conn);

// SQL query to select all records from the 'users' table
$sql = "SELECT * FROM users";
$result = mysql_query($sql, $conn);

// Check if any records were found
if (mysql_num_rows($result) > 0) {
    // Loop through the results and display each record
    while ($row = mysql_fetch_assoc($result)) {
        echo "User ID: " . $row['id'] . "<br>";
        echo "Username: " . $row['username'] . "<br>";
        echo "Email: " . $row['email'] . "<br><br>";
    }
} else {
    echo "No records found.";
}

// Close the database connection
mysql_close($conn);
?>
```

### **Explanation**:
- **Connection and Database Selection**: Uses `mysql_connect()` to establish a connection and `mysql_select_db()` to choose the database.
- **Executing SELECT Query**: `mysql_query()` runs the `SELECT` query.
- **Fetching Results**: Uses `mysql_fetch_assoc()` to retrieve each row as an associative array, making it easy to access columns by name.
- **Looping Through Results**: `while` loop is used to display each user’s details.
- **Counting Records**: `mysql_num_rows()` checks if any rows were returned by the query.

### **3.1.2 Selecting Specific Columns**

You can optimize your `SELECT` queries by specifying the columns you want to retrieve.

**SQL Command for Selecting Specific Columns**:
```sql
SELECT username, email FROM users;
```

**Example: Fetching Specific Columns with PHP**:
```php
<?php
$conn = mysql_connect("localhost", "root", "");
mysql_select_db("my_database", $conn);

// SQL query to select only 'username' and 'email' columns
$sql = "SELECT username, email FROM users";
$result = mysql_query($sql, $conn);

if (mysql_num_rows($result) > 0) {
    while ($row = mysql_fetch_assoc($result)) {
        echo "Username: " . $row['username'] . "<br>";
        echo "Email: " . $row['email'] . "<br><br>";
    }
} else {
    echo "No records found.";
}

mysql_close($conn);
?>
```

### **Explanation**:
- **Efficiency**: Selecting only the necessary columns (`username`, `email`) reduces the amount of data retrieved, making the query more efficient.
- **Output**: Displays only the username and email of each user.

### **3.1.3 Using WHERE Clause in SELECT**

The `WHERE` clause is used to filter records based on a specified condition.

**SQL Command with WHERE Clause**:
```sql
SELECT * FROM users WHERE username = 'john_doe';
```

**Example: Fetching Records with a WHERE Clause in PHP**:
```php
<?php
$conn = mysql_connect("localhost", "root", "");
mysql_select_db("my_database", $conn);

// SQL query to fetch records where 'username' is 'john_doe'
$sql = "SELECT * FROM users WHERE username = 'john_doe'";
$result = mysql_query($sql, $conn);

if (mysql_num_rows($result) > 0) {
    while ($row = mysql_fetch_assoc($result)) {
        echo "User ID: " . $row['id'] . "<br>";
        echo "Username: " . $row['username'] . "<br>";
        echo "Email: " . $row['email'] . "<br>";
    }
} else {
    echo "User not found.";
}

mysql_close($conn);
?>
```

### **Explanation**:
- **Filtering Results**: Uses `WHERE` to select only those rows where `username` matches `'john_doe'`.
- **Output**: Displays the details of the user with the specified username.

---

## **3.2. Performing UPDATE Operations on MySQL Table**

The `UPDATE` statement is used to modify existing records in a table. This allows you to change one or more columns for rows that meet a specified condition. Like `SELECT`, `UPDATE` is also part of **DML**.

#### **3.2.1 Basic UPDATE Query**

**SQL Command for Updating Data**:
```sql
UPDATE users SET email = 'new_email@example.com' WHERE username = 'john_doe';
```

**Example: Updating Data with PHP**:
```php
<?php
$conn = mysql_connect("localhost", "root", "");
mysql_select_db("my_database", $conn);

// SQL query to update the email of a specific user
$sql = "UPDATE users SET email = 'new_email@example.com' WHERE username = 'john_doe'";

if (mysql_query($sql, $conn)) {
    echo "Record updated successfully!";
} else {
    echo "Error updating record: " . mysql_error();
}

mysql_close($conn);
?>
```

### **Explanation**:
- **Modifying Data**: Uses `UPDATE` to change the `email` of the user where `username` is `'john_doe'`.
- **Conditional Update**: The `WHERE` clause ensures that only the intended user’s email is updated.
- **Error Handling**: Displays any errors encountered during the update operation using `mysql_error()`.

### **3.2.2 Updating Multiple Columns**

You can update more than one column at a time by separating the columns with commas.

**SQL Command for Updating Multiple Columns**:
```sql
UPDATE users SET email = 'updated_email@example.com', password = 'new_password123' WHERE username = 'john_doe';
```

**Example: Updating Multiple Columns with PHP**:
```php
<?php
$conn = mysql_connect("localhost", "root", "");
mysql_select_db("my_database", $conn);

// SQL query to update both email and password for 'john_doe'
$sql = "UPDATE users SET email = 'updated_email@example.com', password = 'new_password123' WHERE username = 'john_doe'";

if (mysql_query($sql, $conn)) {
    echo "User details updated successfully!";
} else {
    echo "Error updating user details: " . mysql_error();
}

mysql_close($conn);
?>
```

### **Explanation**:
- **Updating Multiple Fields**: Updates both `email` and `password` fields for the specified user.
- **Efficient Querying**: Instead of multiple queries, this example demonstrates how to modify multiple fields in a single query.

### **3.2.3 Updating Without a WHERE Clause (Use with Caution)**

If you run an `UPDATE` without a `WHERE` clause, it will modify **all rows** in the table.

**Example: Updating All Records (Not Recommended)**:
```php
<?php
$conn = mysql_connect("localhost", "root", "");
mysql_select_db("my_database", $conn);

// SQL query to update the email of all users (use with caution)
$sql = "UPDATE users SET email = 'same_email@example.com'";

if (mysql_query($sql, $conn)) {
    echo "All records updated!";
} else {
    echo "Error updating records: " . mysql_error();
}

mysql_close($conn);
?>
```

### **Explanation**:
- **No Filtering**: Omitting the `WHERE` clause means the change applies to all rows in the `users` table.
- **Potential Risk**: Use this approach only when you intend to modify every row, as it can lead to accidental data changes.

---

## **3.3 Inserting Data into a MySQL Table**

**SQL Command for Inserting Data**:
```sql
INSERT INTO users (username, email, password) VALUES ('john_doe', 'john@example.com', 'password123');
```

**Example: Inserting Data with PHP**:
```php
<?php
$conn = mysql_connect("localhost", "root", "");
mysql_select_db("my_database", $conn);

// SQL to insert a record into 'users' table
$sql = "INSERT INTO users (username, email, password) 
        VALUES ('john_doe', 'john@example.com', 'password123')";

if (mysql_query($sql, $conn)) {
    echo "New record created successfully!";
} else {
    echo "Error: " . mysql_error();
}

mysql_close($conn);
?>
```

### **Explanation**:
- **`INSERT INTO`**: Adds a new record to the `users` table with specified values for each column.
- **Error Handling**: Uses `mysql_error()` to show any errors during the insertion process.

### **3.3.1 Inserting Multiple Records**

You can also insert multiple records using a single query.

**SQL Command for Inserting Multiple Records**:
```sql
INSERT INTO users (username, email, password) VALUES 
('jane_doe', 'jane@example.com', 'password123'),
('mark_smith', 'mark@example.com', 'password456');
```

**Example: Inserting Multiple Records with PHP**:
```php
<?php
$conn = mysql_connect("localhost", "root", "");
mysql_select_db("my_database", $conn);

// SQL to insert multiple records
$sql = "INSERT INTO users (username, email, password) VALUES 
        ('jane_doe', 'jane@example.com', 'password123'),
        ('mark_smith', 'mark@example.com', 'password456')";

if (mysql_query($sql, $conn)) {
    echo "Records inserted successfully!";
} else {
    echo "Error: " . mysql_error();
}

mysql_close($conn);
?>
```

---

## **3.4 Deleting Records from a MySQL Table**

**SQL Command for Deleting Data**:
```sql
DELETE FROM users WHERE username = 'john_doe';
```

**Example: Deleting a Record with PHP**:
```php
<?php
$conn = mysql_connect("localhost", "root", "");
mysql_select_db("my_database", $conn);

// SQL to delete a record from 'users' table
$sql = "DELETE FROM users WHERE username = 'john_doe'";

if (mysql_query($sql, $conn)) {
    echo "Record deleted successfully!";
} else {
    echo "Error deleting record: " . mysql_error();
}

mysql_close($conn);
?>
```

### **Explanation**:
- **`DELETE FROM`**: Removes records from the specified table.
- **`WHERE`**: Specifies the condition for deleting records, ensuring only specific rows are removed.
- **Error Handling**: Uses `mysql_error()` to display any issues during deletion.

---

# **4. Dropping Tables and Databases**

## **4.1 Dropping a Table**

The `DROP` command is used to permanently delete a table from the database.

**SQL Command for Dropping a Table**:
```sql
DROP TABLE users;
```

**Example: Dropping a Table with PHP**:
```php
<?php
$conn = mysql_connect("localhost", "root", "");
mysql_select_db("my_database", $conn);

// SQL to drop the 'users' table
$sql = "DROP TABLE users";

if (mysql_query($sql, $conn)) {
    echo "Table 'users' dropped successfully!";
} else {
    echo "Error dropping table: " . mysql_error();
}

mysql_close($conn);
?>
```

## **4.2 Dropping a Database**

The `DROP DATABASE` command is used to permanently delete a database along with all its tables.

**SQL Command for Dropping a Database**:
```sql
DROP DATABASE my_database;
```

**Example: Dropping a Database with PHP**:
```php
<?php
$conn = mysql_connect("localhost", "root", "");

// SQL to drop the database
$sql = "DROP DATABASE my_database";

if (mysql_query($sql, $conn)) {
    echo "Database dropped successfully!";
} else {
    echo "Error dropping database: " . mysql_error();
}

mysql_close($conn);
?>
```

---

# **5. Summary of MySQL Operations in PHP**

## **CRUD Operations Summary**
| Operation  | SQL Command                  | Description                                | PHP Function Example                                  |
|------------|------------------------------|--------------------------------------------|------------------------------------------------------|
| **CREATE** | `CREATE TABLE`               | Defines a new table structure.             | `mysql_query("CREATE TABLE ...")`                    |
| **INSERT** | `INSERT INTO`                | Adds new records to a table.               | `mysql_query("INSERT INTO ...")`                     |
| **READ**   | `SELECT`                     | Retrieves records from a table.            | `mysql_query("SELECT ...")`                          |
| **UPDATE** | `UPDATE`                     | Modifies existing records in a table.      | `mysql_query("UPDATE ...")`                          |
| **DELETE** | `DELETE FROM`                | Removes specific records from a table.     | `mysql_query("DELETE FROM ...")`                     |
| **DROP**   | `DROP TABLE` / `DROP DATABASE`| Deletes tables or databases permanently.   | `mysql_query("DROP TABLE ...")`                      |
| **SELECT**  | `SELECT * FROM users;`                                        | Retrieves all records from the `users` table.  | `mysql_query("SELECT * FROM users", $conn);`     |
|             | `SELECT username FROM users;`                                 | Retrieves only the `username` column.          | `mysql_query("SELECT username FROM users", $conn);` |
|             | `SELECT * FROM users WHERE username = 'john_doe';`            | Retrieves records matching a condition.        | `mysql_query("SELECT * FROM users WHERE username = 'john_doe'", $conn);` |
| **UPDATE**  | `UPDATE users SET email = 'new_email' WHERE username = 'john_doe';` | Modifies a specific record in `users`.         | `mysql_query("UPDATE users SET email = 'new_email' WHERE username = 'john_doe'", $conn);` |
|             | `UPDATE users SET email = 'same_email';`                      | Updates the email for all users.               | `mysql_query("UPDATE users SET email = 'same_email'", $conn);` |

## **Best Practices**:
- **Always Backup Data**: Before performing `DELETE` or `DROP` operations, always back up your database.
- **Always Use `WHERE` Clauses**: For both `SELECT` and `UPDATE`, using `WHERE` helps target specific records, preventing unintended changes.
- **Limit Results for Efficiency**: Use `LIMIT` with `SELECT` queries to reduce the number of records returned, improving performance.
- **Backup Data Before Updates**: Before running an `UPDATE` query, especially without a `WHERE`, back up the data to avoid irreversible changes.
- **Use Conditions**: When using `DELETE`, always specify a `WHERE` clause to avoid deleting all records unintentionally.
- **Close Connections**: Use `mysql_close()` after your operations to free up resources.
