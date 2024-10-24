## **Cookies and Sessions**

When building dynamic web applications, it is often necessary to store user-specific data across multiple pages. This is where **cookies** and **sessions** come into play. They both serve the purpose of **maintaining state** (keeping data between different page requests), but they do so in different ways.

### **What are Cookies?**
- **Definition**: Cookies are small pieces of data that are stored on the client's computer (browser).
- **Purpose**: They are used to remember information about the user, like login details, preferences, or tracking information.
- **Storage**: Cookies are stored as text files on the client’s machine and are sent back to the server with each HTTP request.

### **What are Sessions?**
- **Definition**: Sessions store data on the server, rather than on the client.
- **Purpose**: They are used to store temporary data that should persist across multiple page requests during a user session (e.g., logged-in status).
- **Storage**: Sessions are identified by a unique **session ID** that is stored as a cookie on the client’s browser, linking the client to their session data on the server.

---

## **1. Understanding Cookies in PHP**

### **1.1 Setting a Cookie**
To set a cookie in PHP, use the `setcookie()` function.

**Syntax**:
```php
setcookie(name, value, expire, path, domain, secure, httponly);
```

- **`name`**: Name of the cookie.
- **`value`**: Value to be stored in the cookie.
- **`expire`**: Expiration time in seconds (use `time()` function for current time).
- **`path`**: Directory where the cookie is available.
- **`domain`**: The domain that the cookie is available to.
- **`secure`**: If true, the cookie is sent over HTTPS only.
- **`httponly`**: If true, the cookie is only accessible through HTTP, not JavaScript.

**Example: Setting a Cookie**:
```php
<?php
// Setting a cookie named "user" with a value of "John Doe" that expires in 1 hour
setcookie("user", "John Doe", time() + 3600, "/");
?>
```

### **1.2 Retrieving a Cookie**
To retrieve the value of a cookie, use the `$_COOKIE` superglobal array.

**Example: Retrieving a Cookie**:
```php
<?php
if (isset($_COOKIE['user'])) {
    echo "Welcome back, " . $_COOKIE['user'] . "!";
} else {
    echo "Hello, new visitor!";
}
?>
```

### **1.3 Deleting a Cookie**
To delete a cookie, set its expiration time to a past time.

**Example: Deleting a Cookie**:
```php
<?php
// Delete the "user" cookie by setting its expiration time to the past
setcookie("user", "", time() - 3600, "/");
?>
```

### **1.4 Common Use Cases for Cookies**:
- **Remembering user preferences** (e.g., theme selection).
- **Tracking user activity** for analytics.
- **Storing login tokens** for automatic logins.

---

## **2. Understanding Sessions in PHP**

### **2.1 Starting a Session**
To use sessions, the `session_start()` function must be called at the beginning of a PHP script before any HTML output.

**Example: Starting a Session**:
```php
<?php
session_start(); // Start the session

// Store session data
$_SESSION["username"] = "JohnDoe";
$_SESSION["role"] = "admin";
?>
```

### **2.2 Accessing Session Data**
Once a session is started, the stored data can be accessed using the `$_SESSION` superglobal.

**Example: Accessing Session Data**:
```php
<?php
session_start(); // Start the session

if (isset($_SESSION["username"])) {
    echo "Welcome, " . $_SESSION["username"] . "!";
} else {
    echo "Please log in.";
}
?>
```

### **2.3 Modifying and Unsetting Session Variables**
You can modify session variables by assigning a new value or unset them using `unset()`.

**Example: Modifying and Unsetting Session Data**:
```php
<?php
session_start(); // Start the session

// Change the username
$_SESSION["username"] = "JaneDoe";

// Remove the role data from the session
unset($_SESSION["role"]);

// Destroy all session data
session_destroy();
?>
```

### **2.4 Storing Complex Data in Sessions**
PHP sessions can store arrays and even objects.

**Example: Storing an Array in a Session**:
```php
<?php
session_start(); // Start the session

// Store an array in a session variable
$_SESSION["cart"] = array("item1" => 2, "item2" => 5); // 2 of item1, 5 of item2

// Access and modify the array
$_SESSION["cart"]["item3"] = 1; // Add 1 of item3 to the cart
?>
```

---

## **3. Comparison of Cookies and Sessions**

| Feature                | Cookies                                      | Sessions                                     |
|------------------------|-----------------------------------------------|----------------------------------------------|
| **Storage Location**   | Stored on the client’s browser as text files | Stored on the server                         |
| **Lifetime**           | Can persist beyond the browser session       | Lasts until the browser is closed or `session_destroy()` is called |
| **Security**           | Less secure, as data is stored on the client | More secure, data is stored on the server    |
| **Data Capacity**      | Limited (4KB max)                            | Larger capacity (depends on server storage)  |
| **Use Cases**          | Remember user preferences, tracking          | User authentication, shopping carts         |

---

## **4. Using Sessions with MySQL**

Sessions are often used with MySQL databases to maintain user authentication and manage user-specific data. Here’s how you can use PHP sessions with a MySQL database to create a simple user login system.

### **Example: User Login with Sessions and MySQL**

1. **HTML Form** (login.html):
    ```html
    <form action="login.php" method="post">
        Username: <input type="text" name="username" required><br>
        Password: <input type="password" name="password" required><br>
        <input type="submit" value="Login">
    </form>
    ```

2. **PHP Script for Login (login.php)**:
    ```php
    <?php
    session_start(); // Start the session
    $servername = "localhost";
    $username = "root";
    $password = "";
    $database = "users_db";
    
    // Create MySQL connection
    $conn = mysql_connect($servername, $username, $password);
    if (!$conn) {
        die("Connection failed: " . mysql_error());
    }
    
    // Select the database
    mysql_select_db($database, $conn);
    
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        $username = $_POST['username'];
        $password = $_POST['password'];

    // Query to check if the username and password match
    $sql = "SELECT * FROM users WHERE username = '$username' AND password = '$password'";
    $result = mysql_query($sql, $conn);

    if (mysql_num_rows($result) == 1) {
        // Set session variables upon successful login
        $_SESSION["username"] = $username;
        $_SESSION["loggedin"] = true;
        header("Location: welcome.php"); // Redirect to welcome page
    } else {
        echo "Invalid username or password.";
    }
    }
    
    // Close the connection
    mysql_close($conn);
    ?>

    ```

3. **PHP Script for Welcome Page (welcome.php)**:
    ```php
    <?php
    session_start(); // Start the session

    if (!isset($_SESSION["loggedin"]) || $_SESSION["loggedin"] !== true) {
        header("Location: login.html"); // Redirect to login if not logged in
        exit;
    }

    echo "Welcome, " . $_SESSION["username"] . "! <a href='logout.php'>Logout</a>";
    ?>
    ```

4. **PHP Script for Logging Out (logout.php)**:
    ```php
    <?php
    session_start();
    session_unset(); // Unset all session variables
    session_destroy(); // Destroy the session
    header("Location: login.html");
    ?>
    ```

### **Explanation**:
- **User Authentication**:
  - The `login.php` script checks if the provided username and password match a record in the `users` table.
  - If a match is found, the user's session is initialized, and they are redirected to `welcome.php`.
- **Session Management**:
  - The `welcome.php` script ensures that only logged-in users can access the page.
  - The `logout.php` script clears the session and redirects users back to the login page.

---

## **5. Summary and Best Practices**

### **When to Use Cookies**:
- **Remember User Preferences**: Store theme selection or language preferences.
- **Non-Sensitive Data**: Use cookies for data that is not sensitive, like a visitor's last viewed page.

### **When to Use Sessions**:
- **User Authentication**:

 Manage login sessions securely.
- **Temporary Data**: Store data like shopping cart contents during a user session.

### **Best Practices**:
- **Secure Cookies**: Set the `secure` and `httponly` flags to ensure cookies are only sent over HTTPS and are not accessible via JavaScript.
- **Session Timeout**: Implement session timeouts for enhanced security.
- **Use Prepared Statements**: Always use prepared statements with MySQL to prevent SQL injection.
