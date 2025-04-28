# 📚 Week 1 - Web Server and PHP Basics

## 🌐 What is a Web Server?

- A **Web Server** is a system that **delivers requested files** (HTML, PHP, images, etc.) to clients (browsers) over the internet.
- Commonly used in **APM stack**: Apache (Web Server) + PHP (Server-side Language) + MySQL (Database).

**Example Credentials:**
- ID: `student`
- Password: `student1234`

---

## 🖥️ How Does a Browser Request a File?

You can request a file using a **web browser** by specifying a **URL**.

### 📄 URL Structure

```
[Protocol]://[Domain or IP address]:[Port]/[File Path]
```

**Example:**

```
http://192.168.50.177:80/
```

- **Web Root Path:** `/var/www/html/`

The browser sends a request, and the web server returns the corresponding file located under the web root directory.

---

## 🚪 Standard Ports (Social Convention)

| Protocol | Default Port |
|:---|:---|
| HTTP | 80 |
| HTTPS | 443 |

- When using standard ports, specifying the port is optional.
- Non-standard ports must be specified in the URL.

---

## 🛠️ Web Application Server (WAS)

**Flow:**

```
Client (Browser) → Web Server → WAS (Web Application Server) → Database (DB)
```

- **WAS** handles dynamic content generation and business logic.
- Web Server delivers static files or passes requests to the WAS for dynamic content.

Example PHP start:

```php
<?php
    // PHP script execution begins here
?>
```

---

## 🔧 VSCode - SFTP Plugin

- Use **SFTP plugin in VSCode** to upload and synchronize files directly between your local machine and the server securely.

---

# 🖋️ PHP Basics

- `$_GET["key"]` and `$_POST["key"]` are PHP superglobals to retrieve client data.
- `echo` and `print` are used for output.

```php
<?php
echo $_GET['username'];
echo $_POST['password'];
?>
```

---

# ✉️ HTTP Request Methods: GET vs POST

| Method | Characteristics |
|:---|:---|
| GET | Data is appended to the URL, visible, limited data size, used for simple requests. |
| POST | Data is sent in the request body, hidden from URL, no size limitation, used for sensitive information like login. |

### 🖥️ Front-End vs Back-End

| Front-End | Back-End |
|:---|:---|
| Client-side code executed by browsers (HTML, CSS, JavaScript). | Server-side code executed on servers (PHP, ASP, JSP, Node.js). |

---

# ✅ Example: GET Method Form

**HTML Form:**

```html
<form method="GET">
    <input type="text" name="id">
    <input type="submit" value="Submit">
</form>
```

**PHP Script:**

```php
<?php
echo $_GET['id'];
?>
```

After submission, the URL will be:

```
http://yourdomain.com/?id=student
```

- Parameters are **exposed in the URL**.

---

# ✅ Example: POST Method Form

**HTML Form:**

```html
<form method="POST">
    <input type="text" name="id">
    <input type="submit" value="Submit">
</form>
```

**PHP Script:**

```php
<?php
echo $_POST['id'];
?>
```

- Parameters are **hidden** and sent inside the **request body**.

---

# 📋 Difference Between GET and POST

| Aspect | GET | POST |
|:---|:---|:---|
| Visibility | Visible in URL | Hidden in Request Body |
| Security | Less secure (sensitive data can be exposed) | More secure (data not shown in URL) |
| Data Size | Limited | Unlimited (depends on server settings) |
| Use Case | Simple data retrieval (e.g., search) | Secure data submission (e.g., login, payment) |

**Best Practice:** Use **POST** for login forms and sensitive information transmission.

---

# 🔐 Login Form Example (GET Method)

**login.html:**

```html
<form method="GET" action="login_proc.php">
    <input type="text" name="id" placeholder="User ID">
    <input type="password" name="pass" placeholder="User Password">
    <input type="submit" value="Login">
</form>
```

**login_proc.php:**

```php
<?php
    echo $_GET['id'];
    echo $_GET['pass'];
?>
```

After submission, the URL will look like:

```
http://yourdomain.com/login_proc.php?id=student&pass=student1234
```

- `&` is used as a **parameter separator** between multiple query parameters.

---

# 📌 Key Takeaways

1. **Web Server**: Delivers requested files (HTML, PHP, etc.).
2. **WAS (Web Application Server)**: Handles dynamic content.
3. **URL structure** and **default ports** for HTTP/HTTPS.
4. **GET vs POST** differences and security implications.
5. **Handling parameters** in PHP using `$_GET` and `$_POST`.

---

# 📈 Summary Table

| Concept | Explanation |
|:---|:---|
| Web Server | Delivers static and dynamic files |
| WAS | Processes business logic |
| GET Method | Appends data to URL, visible |
| POST Method | Sends data in body, hidden |
| PHP $_GET | Retrieves GET parameters |
| PHP $_POST | Retrieves POST parameters |

Stay focused, practice hard, and secure your web applications! 🚀
