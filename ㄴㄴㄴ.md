# 📚 Week 3 - Web Security Basics

## ✏️ Extracting Student Names and Scores

```php
<?php
    echo $name;
?>
```

---

## 🧩 Membership Registration Feature

// (Registration logic is implied, not provided explicitly.)

---

## 🔐 Login Section

// (Login UI/logic implied, no specific code provided.)

```php
mysqli_close($conn);
```

---

## 🚪 Understanding the Login Process

**Login:** Authentication process.

- OTP bypass vulnerabilities exist in some authentication implementations.

**Login definition:**
- Verifying if the user is the correct person.

### 🔍 Identification vs Authentication

| Identification (Exposure OK) | Authentication (Must be Protected) |
|:---|:---|
| Identifying specific data among many (e.g., shining a flashlight to find one). | Verifying if the person is who they claim to be. |
| Examples: ID, Email, Phone number (Public or Unique Identifiers) | Examples: Passwords, OTPs (Sensitive authentication information) |
| ID must be unique (Primary Key, no duplicates). | Authentication information must be secret. |
| Leakage of SSN, Passport, Driver License is dangerous. | |

### 📄 SQL Query Example

```sql
SELECT * FROM member
WHERE id = 'nomaltic';
```

---

## 🛠️ Identification and Authentication Logic

### (1) Simultaneous Identification and Authentication
Perform both in a single SQL query.

```php
$sql = "SELECT * FROM member WHERE id = '$user_id' AND pass = '$user_pass';";

$ret = $sql->execute();

if ($ret) {
    // ✅ Login successful
} else {
    // ❌ Login failed
}
```

### (2) Separate Identification and Authentication
First identify, then authenticate separately.

```php
$sql = "SELECT * FROM member WHERE id = 'user_id';";

$db_pass = $sql->ret['pass'];

if ($db_pass == $user_pass) {
    // ✅ Login successful
} else {
    // ❌ Login failed
}
```

---

## 🔒 Hashing Passwords (One-Way Encryption)

Used during:
- Login
- Session maintenance

### ⚡ Cookie vs Session

**Cookies**
- Stored on the client side.
- Vulnerable to tampering.

**Sessions**
- Stored on the server side.
- Safer and server-controlled.

```php
<?php
session_start();

$_SESSION['id'] = 'nomaltic';
?>
```

**Session IDs**
- Randomly generated each login.
- Stored in cookies (e.g., `PHPSESSID`).
- Can be stolen if sniffed (e.g., via Wireshark).

**Session Storage**
- Saved as files or in databases on the server.
- Functions like a key-value table.

**Best Practice:**
- Always regenerate session ID after login.
- Force auto logout after inactivity (e.g., banks enforce 3-minute timeouts).

---

# 📝 Summary

- Login = Authentication 🔐
- Identification ≠ Authentication
- Cookies are vulnerable 🍪, sessions are safer 🛡️.
- Always use session security practices to prevent hijacking.
- Hash passwords to protect authentication data.

Stay safe and code securely! 🚀
