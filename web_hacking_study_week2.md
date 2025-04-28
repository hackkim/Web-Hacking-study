# 📃 Week 2 - PHP and Database Basics

## 👉 Index.php - Basic Login Check

```php
<?php
if ($_GET['login_id'] == "") {
    header("Location: login.php");
    exit;
}
?>
```

- **header()** function: Sends a raw HTTP header.
  - Example: `header("Location: login.php");` redirects to login page.
- **exit;** is important to stop further code execution after redirection.

---

## 🔒 Header Explanation

- `header("Location: login.php");` → HTTP response will include `Location` header.
- Redirects browser to `login.php`.
- Always use `exit` after `header()` to prevent code leakage.

---

## 👍 Form Handling

```html
<form action="">
    <input type="text" name="username">
    <input type="password" name="password">
    <input type="submit" name="submit">
</form>
```

- `action=""` → Submits form to the same page.
- Check if form is submitted:

```php
if (isset($_POST['submit'])) {
    // Handle form submission
}
```

---

## 🔍 Debugging Techniques

1. **Display PHP Errors:** Configure PHP to display errors for debugging.

2. **Use echo for Debugging:**

```php
echo "Debug info: " . $login_res;
```

- Helps to trace variable values during development.

---

# 🔹 Database Concepts

- **Database (DB):** Like an Excel file.
- **Table:** Like a sheet inside Excel.
- **Column:** Represents data categories (vertical).
- **Row:** Represents each record (horizontal).

---

## 💡 Web Interaction Flow

```
Web <-> WAS (Web Application Server) <-> DB (Database)
```

- **WAS** uses **SQL** to interact with **DB**.

---

## 📊 Basic SQL Commands

### ✅ SELECT (Retrieve Data)

```sql
SELECT column_name FROM table_name;
SELECT name FROM test_table;
SELECT name, pass FROM test_table;
SELECT * FROM test_table;
```

### ✅ INSERT (Insert Data)

```sql
INSERT INTO test_table (name, score, pass) 
VALUES ('doldol', '80', '2222');

-- or inserting with auto-increment id
INSERT INTO test_table 
VALUES (NULL, 'doldol', '70', '3333');
```

### ✅ SELECT with WHERE (Conditional Query)

```sql
SELECT * FROM test_table WHERE name = 'normaltic';
SELECT * FROM test_table WHERE name = 'normaltic' OR pass = '1234';
```

---

# 🖥️ PHP - MySQL Connection

### Database Connection Example

```php
<?php
$db_conn = mysqli_connect('localhost', 'admin', 'student1234', 'test');

if ($db_conn) {
    echo "DB Connect OK";
} else {
    echo "DB Connect Fail";
}
?>
```

---

## 👀 Basic SELECT and Output

```php
$sql = "SELECT * FROM test_table";
$result = mysqli_query($db_conn, $sql);
$row = mysqli_fetch_array($result);

var_dump($row);

echo "Name: " . $row['name'];
```

### SELECT with WHERE Condition

```php
$sql = "SELECT * FROM test_table WHERE name='doldol'";
$result = mysqli_query($db_conn, $sql);
$row = mysqli_fetch_array($result);

var_dump($row);

echo "Password: " . $row['pass'];

$db_pass = $row['pass'];
if ($_POST['username'] == $db_pass) {
    // Login successful
}
```

---

# 📌 Key Points

- PHP variable starts with `$`.
- PHP string concatenation uses `.` operator.
- After a `header("Location:...")`, always use `exit;`.
- In real-world, password comparison should use **hashed passwords** not plain text.

---

# 📈 Summary

| Concept | Example |
|:---|:---|
| Database | Excel File |
| Table | Excel Sheet |
| Column | Vertical Category |
| Row | Horizontal Record |
| SQL Keywords | SELECT, INSERT, WHERE |
| PHP-MySQL Connection | mysqli_connect |
| Debugging | echo, var_dump |

Stay sharp and code securely! 🚀
