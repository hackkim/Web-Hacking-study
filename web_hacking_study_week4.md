# 🔧 Week 4 - Burp Suite and Web Proxy Basics

## 🛠️ Burp Suite Overview

- **Burp Suite** is a professional web proxy tool used mainly for **web application penetration testing**.
- It allows you to **intercept**, **modify**, **analyze**, and **repeat** web traffic between the client (browser) and the server.

**Burp Suite Components:**
- **Proxy**: Intercept traffic between browser and server.
- **Repeater**: Resend modified HTTP requests manually.
- **Decoder**: Encode and decode data formats (e.g., Base64, URL encoding).
- **Comparer**: Compare two pieces of data to find differences (characters, bytes).

---

## 🔔 Proxy Settings

To use Burp Suite properly, you need to configure your proxy settings:

1. Open **Burp Suite**.
2. Navigate to **Proxy -> Options**.
3. Add a **Proxy Listener**:
   - **Bind Address**:
     - `127.0.0.1` (Localhost) → Only for internal machine testing.
     - `All Interfaces` → To allow external devices (e.g., mobile apps) to route traffic through your Burp proxy.

**Usage Cases:**
- **Local testing**: Keep the Bind Address as `127.0.0.1`.
- **Mobile app hacking**: Set Bind Address to **All Interfaces** and configure the mobile device to use your computer's IP as a proxy.

> **Note:** You must have a listener active to intercept traffic.

---

## 🌐 How Web Traffic Flows with Burp Suite

```
Browser → Burp Suite Proxy → Google Server (or other target server)
```

- Burp Suite sits in the middle, capturing and manipulating the traffic.

---

## 🚀 Why Use a Web Proxy Tool?

- Essential for **penetration testers** and **bug bounty hunters**.
- Analyze, tamper, and replay HTTP/HTTPS traffic.
- Identify vulnerabilities such as:
  - Broken authentication
  - Session management flaws
  - Injection points (e.g., SQLi, XSS)

---

# 🛠️ Burp Suite Key Features

| Feature | Description |
|:---|:---|
| Proxy | Intercept HTTP/HTTPS requests and responses |
| Repeater | Manually modify and resend HTTP requests repeatedly |
| Decoder | Decode or encode data (e.g., URL, Base64) |
| Comparer | Highlight differences between two HTTP messages |

---

# 🔢 HTTP Status Codes Overview

| Status Code | Meaning |
|:---|:---|
| 200 | OK - Successful request |
| 300 | Redirect - Further action needs to be taken |
| 301/302 | Moved permanently / temporarily |
| 400 | Client Error - Request cannot be processed |
| 404 | Not Found - Resource doesn't exist |
| 500 | Server Error - Server failed to fulfill request |

**Quick Tip:**
- `Location` header often appears in 300 redirects.
- **400 series** errors are client-side mistakes.
- **500 series** errors are server-side failures.

---

# 🔐 Encoding Insight

- `%3D` → `=` (URL Encoding)
- A string ending with `=` often suggests **Base64 encoding**.

> **Base64 Identification Tip:**
> - If the encoded string ends with `=`, it is highly probable that it is Base64 encoded.
> - Use Burp Suite Decoder to verify and decode Base64 data easily.

---

# 📌 Summary

- **Burp Suite** is an essential tool for web security testing.
- **Proxy Listener** must be correctly configured to capture traffic.
- **All Interfaces** binding enables mobile device traffic interception.
- Understand basic **HTTP status codes** to diagnose issues quickly.
- **Base64 detection** becomes intuitive with experience.

Keep practicing, stay curious, and master your tools! 🚀
