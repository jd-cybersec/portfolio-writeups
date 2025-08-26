# Local File Inclusion (LFI) – Case Study

**Author:** Jordan Davis  
**Platform:** Hack The Box Academy (Sanitized Case Study)  
**Category:** Web Exploitation / File Inclusion  

---

## 🧠 Overview

This case study demonstrates the exploitation of a **Local File Inclusion (LFI)** vulnerability in a simulated lab environment.  
By leveraging weak input validation and unsafe file handling, it was possible to escalate the vulnerability into **Remote Code Execution (RCE)** using log poisoning techniques.  

---

## 🎯 Objectives

- Identify and exploit a Local File Inclusion vulnerability  
- Test multiple payload approaches (directory traversal, wrappers)  
- Escalate LFI to RCE using log file injection  
- Highlight secure coding practices to prevent similar issues  

---

## 🛠️ Tools & Environment

- **Burp Suite** for request inspection and parameter testing  
- **FFUF** for directory and parameter fuzzing  
- **Linux environment** for crafting payloads and encodings  
- Hack The Box Academy lab environment  

---

## 🔍 Methodology (Sanitized)

### 1. Reconnaissance
- Performed directory and subdomain enumeration.  
- Identified dynamic parameters that accepted user input.  

### 2. LFI Discovery
- Found a parameter vulnerable to file inclusion.  
- Used **directory traversal** to retrieve sensitive files (e.g., `/etc/passwd`).  
- Employed `php://filter` wrapper to extract and review source code.  

### 3. Hidden Functionality
- Discovered hidden administrative functionality during enumeration.  
- Conducted parameter fuzzing, though no additional undocumented parameters were found.  

### 4. Escalation to RCE
- Performed **log poisoning** by injecting PHP payloads into access logs.  
- Retrieved the poisoned log via LFI and executed commands.  
- Successfully demonstrated RCE with system command output in the lab environment.  

---

## 🧱 Remediation & Defense

- Strictly validate and sanitize user input for file path parameters.  
- Avoid dynamic file inclusion based on user-controlled input.  
- Use allowlists for permitted file paths.  
- Disable unnecessary PHP wrappers (e.g., `php://filter`).  
- Restrict web server permissions and isolate log files from public access.  

---

## ✅ Conclusion

This case study shows how LFI, if left unchecked, can be escalated into **remote code execution** by combining it with techniques like log poisoning.  
The scenario highlights the importance of defensive coding practices, configuration hardening, and principle of least privilege for web applications.  

---
