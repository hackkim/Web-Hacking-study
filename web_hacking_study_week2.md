
# 🛠️ Web Hacking Study: Understanding Web Servers and Parameter Transmission in PHP

> In this post, we’ll explore how web servers work, how users interact with them using web browsers, and how to use PHP to receive parameters via GET and POST methods. This content is ideal for beginners who are starting to learn web development or web hacking.

---

## 🌐 What is a Web Server?

A **Web Server** is a system that delivers content or services to end users over the web. It responds to HTTP requests from clients (usually browsers) and provides the corresponding files such as HTML, CSS, JS, or dynamically generated PHP pages.

### Web Root Example:
```
/var/www/html/
```

Files placed inside this directory are accessible through a browser if the server is running.

---

## 🧭 URL Structure and HTTP Request Basics

A typical HTTP request URL looks like:

```
[Protocol]://[Domain or IP address]:[Port]/[File path]
```

### Example:
```
http://192.168.50.177:80/index.html
```

- **Protocol**: `http` or `https`
- **Domain/IP**: IP address or website name
- **Port**: Optional (80 for HTTP, 443 for HTTPS)
- **File path**: Path to the file on the server (relative to web root)

> 🔸 Browsers automatically assume port 80 for HTTP and 443 for HTTPS if not specified.

---

## 💡 Web Application Architecture

Modern web applications often follow this structure:

```
Client (Browser)
    ↓
Web Server (Apache, Nginx)
    ↓
Web Application Server (WAS - PHP, JSP, ASP)
    ↓
Database (MySQL, MariaDB, etc.)
```

This layered design separates static file serving (web server) from dynamic processing (WAS).

---

## ⚙️ PHP and HTTP Methods: GET vs POST

In PHP, data from a user can be retrieved through either `$_GET` or `$_POST`, depending on the HTTP method used in the form submission.

---

## 📮 GET Method

### Description:
- Sends form data through the **URL**
- Parameters are appended as query strings
- Visible to the user
- Used for non-sensitive data and linkable resources

### Example HTML Form:

```html
<form method="GET" action="login_proc.php">
    <input type="text" name="id" placeholder="Enter your ID">
    <input type="password" name="pass" placeholder="Enter your password">
    <input type="submit" value="Login">
</form>
```

### Example PHP Handler (`login_proc.php`):

```php
<?php
    echo "ID: " . $_GET['id'] . "<br>";
    echo "Password: " . $_GET['pass'];
?>
```

### URL will look like:
```
login_proc.php?id=student&pass=student1234
```

---

## 🕶️ POST Method

### Description:
- Sends form data through the **request body**
- Not visible in the URL
- More secure than GET (but still needs HTTPS for full security)
- Commonly used for login forms and data modification

### Example HTML Form:

```html
<form method="POST" action="login_proc.php">
    <input type="text" name="id" placeholder="Enter your ID">
    <input type="password" name="pass" placeholder="Enter your password">
    <input type="submit" value="Login">
</form>
```

### Example PHP Handler:

```php
<?php
    echo "ID: " . $_POST['id'] . "<br>";
    echo "Password: " . $_POST['pass'];
?>
```

---

## 🔍 Key Differences Between GET and POST

| Feature           | GET                                  | POST                                 |
|------------------|---------------------------------------|--------------------------------------|
| Data Location     | URL (query string)                   | HTTP Request Body                    |
| Visibility        | Visible in address bar               | Hidden from user view                |
| Use Case          | Search queries, filters, navigation  | Logins, form submissions, updates    |
| Max Data Length   | Limited (about 2048 characters)       | Much larger                          |
| Security          | Less secure (use only for public data)| More secure (use with HTTPS)         |

---

## 🧪 Practice Exercise: Basic Login Page Using GET

### login.html

```html
<form method="GET" action="login_proc.php">
    <input type="text" name="id" placeholder="User ID">
    <input type="password" name="pass" placeholder="User Password">
    <input type="submit" value="Login">
</form>
```

### login_proc.php

```php
<?php
    echo "<h2>Login Information Received</h2>";
    echo "ID: " . htmlspecialchars($_GET['id']) . "<br>";
    echo "Password: " . htmlspecialchars($_GET['pass']);
?>
```

---

## 💬 Summary: What You Learned

1. How to use a web browser to send requests to a web server
2. How URLs are structured and how ports work (80, 443)
3. The difference between GET and POST methods in PHP
4. How to send and receive parameters using forms
5. How to make your own login page and parameter receiver in PHP

---

## 📝 Developer Notes

- Use `htmlspecialchars()` to prevent XSS when printing user inputs.
- Use POST for all login and sensitive data.
- You can test these pages by placing them in `/var/www/html` if using Apache, or in a public folder if using XAMPP/MAMP.
- Use the **SFTP extension in VSCode** to upload files to a remote web server.

---

## 🧪 Example Login Credentials

```
ID: student
Password: student1234
```

---

Happy hacking! 🎯
