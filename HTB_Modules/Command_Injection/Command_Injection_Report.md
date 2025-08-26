# Command Injection – Case Study

**Author:** Jordan Davis  
**Platform:** Hack The Box Academy (Sanitized Case Study)  
**Category:** Web Exploitation / Command Injection  

---

## 🧠 Overview

This case study highlights the discovery and exploitation of a **command injection vulnerability** in a simulated file management web application.  
The target featured multiple functions (view, search, move), one of which was insecurely handling user-supplied input, enabling system-level command execution.

---

## 🎯 Objectives

- Identify input vectors vulnerable to command injection  
- Test and bypass filtering of special characters  
- Demonstrate Remote Code Execution (RCE) in a safe lab setting  
- Propose mitigations for securing similar applications  

---

## 🛠️ Tools & Environment

- Burp Suite (intercepting and manipulating requests)  
- Linux shell (payload crafting and encoding)  
- Base64 encoding for filter evasion  
- Hack The Box Academy assessment environment  

---

## 🔍 Methodology (Sanitized)

### 1. Reconnaissance
- Reviewed functionality of the file manager.  
- Tested parameters controlling file operations (view, move).  
- Observed blacklisting of certain operators and characters.  

### 2. Vulnerability Discovery
- The **"Move File"** feature passed user-controlled input to a backend system command.  
- Certain operators (like `&&`) were still functional despite filters, making command chaining possible.  

### 3. Exploitation Approach
- Used encoding and character substitution to bypass filters.  
- Demonstrated command execution by injecting payloads that listed files and confirmed RCE.  
- Leveraged base64 encoding/decoding to safely deliver commands without triggering filters.  

### 4. Outcome
- Successfully achieved Remote Code Execution in the lab environment.  
- Accessed sensitive files by executing system commands through the vulnerable input.  

---

## 🧱 Remediation & Defense

- Sanitize and strictly validate **all** user input.  
- Use allowlists for permitted file/directory names.  
- Avoid direct shell execution—use safe language-native functions.  
- Disable dangerous PHP functions (`exec()`, `system()`, `shell_exec()`) where not necessary.  
- Apply **least privilege** to the web server user to reduce potential damage.  

---

## ✅ Conclusion

This case study demonstrates how improper input handling in file operations can lead to **command injection and RCE**.  
It reinforces the importance of strong validation, safer design patterns, and defensive configuration for web applications.  

---
