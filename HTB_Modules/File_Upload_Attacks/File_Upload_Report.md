# File Upload Attacks – Case Study

**Author:** Jordan Davis  
**Platform:** Hack The Box Academy (Sanitized Case Study)  
**Category:** Web Exploitation / File Upload Vulnerabilities  

---

## 🧠 Overview

This case study explores how insecure file upload functionality can be exploited to gain unauthorized access to a web server.  
The target was a contact form that accepted file uploads, and despite multiple validation layers (extension, MIME type, magic bytes), a crafted payload was able to bypass restrictions and achieve remote code execution.  

---

## 🎯 Objectives

- Assess file upload validation and filtering mechanisms  
- Identify potential bypasses through crafted extensions, headers, and payloads  
- Demonstrate exploitation with a hybrid payload in a controlled lab environment  
- Propose secure design and remediation steps  

---

## 🛠️ Tools & Environment

- Burp Suite (intercepting and manipulating requests)  
- FFUF and wordlists for fuzzing extensions and parameters  
- PHP payloads for proof-of-concept execution  
- Hack The Box Academy lab environment  

---

## 🔍 Methodology (Sanitized)

### 1. Reconnaissance
- Intercepted upload requests via Burp Suite.  
- Confirmed that file type and headers were being validated.  

### 2. Fuzzing & Discovery
- Tested multiple content types, magic bytes, and extensions.  
- Identified that certain uncommon extensions were accepted when disguised with valid image headers.  

### 3. Exploitation Approach
- Crafted a hybrid payload that combined valid image headers with executable code.  
- Uploaded the file using an accepted extension.  
- Located the uploaded file in the predictable directory structure.  
- Executed commands through the malicious upload in a controlled environment.  

### 4. Outcome
- Successfully bypassed layered filters and achieved remote command execution.  
- Demonstrated access to sensitive files.  

---

## 🧱 Remediation & Defense

- Implement strict allowlist for MIME types and extensions.  
- Block double extensions and enforce case consistency.  
- Disable execution from upload directories.  
- Use server-side content inspection (e.g., `finfo_file()` in PHP).  
- Store uploaded files outside the web root with randomized filenames.  
- Deploy a WAF to detect malicious upload attempts.  

---

## ✅ Conclusion

This case study demonstrates the risks of insecure file upload mechanisms. Even with multiple validation steps, insufficient design allowed for a bypass leading to remote code execution.  
The lesson emphasizes the need for **layered defense, proper input handling, and execution restrictions** in web applications.  

---
