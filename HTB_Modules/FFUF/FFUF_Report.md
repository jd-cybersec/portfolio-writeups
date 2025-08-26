# Reconnaissance and Fuzzing with FFUF – Case Study

**Author:** Jordan Davis  
**Platform:** Hack The Box Academy (Sanitized Case Study)  
**Category:** Web Reconnaissance / Fuzzing  

---

## 🧠 Overview

This case study demonstrates real-world reconnaissance and fuzzing techniques using **FFUF (Fuzz Faster U Fool)** in a controlled lab environment.  
The workflow mirrors common steps used in penetration testing and bug bounty reconnaissance: subdomain enumeration, extension fuzzing, hidden page discovery, parameter identification, and value fuzzing.

---

## 🎯 Objectives

- Enumerate subdomains
- Discover accepted file extensions
- Identify hidden pages and directories
- Fuzz parameters and values
- Assess potential data exposure

---

## 🛠️ Tools & Environment

- **FFUF** (`Fuzz Faster U Fool`)
- **Wordlists:** SecLists (DNS, extensions, directories, parameter names, usernames)
- **Environment:** Linux-based penetration testing VM

---

## 🔍 Methodology (Sanitized)

### 1. Subdomain Discovery
- Used FFUF with DNS wordlists to brute-force potential subdomains.  
- Multiple valid subdomains were identified, showing a multi-tenant structure.

### 2. Extension Fuzzing
- Fuzzed common file extensions to determine valid backend technologies.  
- Discovered different subsystems accepting `.php`, `.php7`, and related extensions.

### 3. Hidden Page Discovery
- Fuzzed directories and pages with FFUF.  
- Found sensitive application pages not directly linked in navigation.

### 4. Parameter Discovery
- Brute-forced parameter names using HTTP GET/POST.  
- Identified multiple input parameters, including ones processing user-controlled values.

### 5. Parameter Value Fuzzing
- Tested common usernames and values against discovered parameters.  
- Confirmed that weak validation exposed sensitive data when certain values were supplied.

---

## ✅ Conclusion

This exercise demonstrates how **automation and fuzzing** reveal hidden application surfaces and weak input handling.  
Techniques like these are foundational in both penetration testing and bug bounty hunting, where efficient recon directly translates into higher-impact findings.

---
