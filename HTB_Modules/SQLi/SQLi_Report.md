# SQL Injection (SQLi) – Case Study

**Author:** Jordan Davis  
**Platform:** Hack The Box Academy (Sanitized Case Study)  
**Category:** Web Exploitation / SQL Injection  

---

## 🧠 Overview

This case study demonstrates the exploitation of a **SQL Injection (SQLi)** vulnerability in a simulated grey-box environment.  
The engagement covered authentication bypass, data extraction, privilege escalation, and eventually writing a file to achieve **remote code execution (RCE)**.

---

## 🎯 Objectives

- Identify and exploit SQL injection vulnerabilities  
- Perform database enumeration (tables, columns, data)  
- Escalate privileges based on discovered misconfigurations  
- Attempt file access and RCE  
- Propose security best practices to defend against SQLi  

---

## 🛠️ Tools & Environment

- SQL injection testing techniques (manual payloads, UNION-based injection)  
- Linux command-line tools (base64 encoding)  
- Burp Suite for request interception  
- Hack The Box Academy assessment environment  

---

## 🔍 Methodology (Sanitized)

### 1. Authentication Bypass
- Identified SQL injection in a login form.  
- Successfully bypassed authentication using crafted SQL input, confirming vulnerability.  

### 2. Database Enumeration
- Determined column count through UNION queries.  
- Extracted database version and confirmed backend as **MariaDB on Linux**.  
- Enumerated databases and tables using **INFORMATION_SCHEMA**.  

### 3. Sensitive Data Extraction
- Queried user tables to retrieve usernames and password hashes.  
- Confirmed risk of sensitive data exposure.  

### 4. Privilege Escalation
- Identified the database user was running with **root privileges**, a major misconfiguration.  
- Enumerated excessive privileges including file read/write access.  

### 5. Remote Code Execution
- Attempted direct file write for a PHP shell but encountered permission issues.  
- Successfully used **base64 encoding/decoding** to write a functional web shell into the application directory.  
- Demonstrated RCE by executing system commands in the lab environment.  

---

## 🧱 Remediation & Defense

- Always use **prepared statements** / parameterized queries.  
- Enforce **least privilege**: applications must never connect as root/admin.  
- Disable dangerous privileges (`FILE`, `EXECUTE`, `SUPER`) for DB users.  
- Validate and sanitize **all** user input.  
- Restrict file system permissions to prevent DB from writing into web roots.  
- Enable MySQL/MariaDB `secure_file_priv` to restrict file export locations.  
- Deploy a Web Application Firewall (WAF) to detect injection attempts.  

---

## ✅ Conclusion

This case study highlights the severe risk of SQL Injection when combined with poor database configurations.  
The vulnerability chain escalated from **authentication bypass → data exfiltration → RCE**, demonstrating the critical need for secure coding practices and proper privilege management.  

---

**Assessment Completed:** August 26, 2025  
**Analyst:** Jordan Davis  

---
