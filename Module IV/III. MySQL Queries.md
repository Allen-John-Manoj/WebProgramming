## **1. Introduction to SQL**

**SQL** (Structured Query Language) is the standard language used to interact with databases like MySQL. It allows you to **create**, **read**, **update**, and **delete** data (commonly referred to as **CRUD** operations). SQL commands are divided into different categories based on their functionality:

### **1.1 SQL Categories: DDL and DML**

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

## **2. Data Definition Language (DDL) with PHP**

### **2.1 Creating a MySQL Database**

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

### **2.2 Creating a Table in MySQL**

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

## **3. Data Manipulation Language (DML) with PHP**

### **3.1 Inserting Data into a MySQL Table**

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

### **3.2 Inserting Multiple Records**

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

### **3.3 Deleting Records from a MySQL Table**

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

## **4. Dropping Tables and Databases**

### **4.1 Dropping a Table**

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

### **4.2 Dropping a Database**

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

## **5. Summary of MySQL Operations in PHP**

### **CRUD Operations Summary**
| Operation  | SQL Command                  | Description                                | PHP Function Example                                  |
|------------|------------------------------|--------------------------------------------|------------------------------------------------------|
| **Create** | `CREATE TABLE`               | Defines a new table structure.             | `mysql_query("CREATE TABLE ...")`                    |
| **Insert** | `INSERT INTO`                | Adds new records to a table.               | `mysql_query("INSERT INTO ...")`                     |
| **Read**   | `SELECT`                     | Retrieves records from a table.            | `mysql_query("SELECT ...")`                          |
| **Update** | `UPDATE`                     | Modifies existing records in a table.      | `mysql_query("UPDATE ...")`                          |
| **Delete** | `DELETE FROM`                | Removes specific records from a table.     | `mysql_query("DELETE FROM ...")`                     |
| **Drop**   | `DROP TABLE` / `DROP DATABASE`| Deletes tables or databases permanently.   | `mysql_query("DROP TABLE ...")`                      |

### **Best Practices**:
- **Always Backup Data**: Before performing `DELETE` or `DROP` operations, always back up your database.
- **Use Conditions**: When using `DELETE`, always specify a `WHERE` clause to avoid deleting all records unintentionally.
- **Close Connections**: Use `mysql_close()` after your operations to free up resources.
