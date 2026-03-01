# 🔐 FUTURE_CS_01 – Vulnerability Assessment Report  
### Future Interns – Cyber Security Internship (Feb-March 2026)

---

## 👩‍💻 Intern Details

- **Name:** Sanita Salomon  
- **Track:** Cyber Security  
- **CIN ID:** FIT/FEB26/CS6325  
- **Date Reported:** 1 March 2026  

---

## 🎯 Task Objective

The objective of this task was to perform a structured vulnerability assessment on a legally permitted live test website using standard cybersecurity tools.

The goal was to:

- Identify exposed services and security weaknesses  
- Classify vulnerabilities based on risk level  
- Provide practical remediation recommendations  
- Conduct analysis using a read-only testing methodology  

---

## 🌐 Target Website

http://testphp.vulnweb.com  

> ⚠️ Note: This is an intentionally vulnerable test website used strictly for educational and security testing purposes.

---

## 🛠 Tools Used

- Nmap  
- OWASP ZAP (Passive Scan)  
- Browser Developer Tools  
- Nikto  

---

## 📊 Risk Classification Overview

| Risk Level | Count |
|------------|--------|
| High       | 0      |
| Medium     | 8      |
| Low        | 3      |

Most identified issues fall under the **Medium risk category**, primarily due to insecure configurations and missing protective controls.

---

## 🔎 Key Findings Summary

### 1️⃣ Unencrypted Communication (HTTP – Port 80)

- Website operates over HTTP  
- Data transmission is not encrypted  
- Vulnerable to Man-in-the-Middle (MITM) attacks  

**Risk Level:** Medium  

**Remediation:**
- Implement HTTPS using a valid SSL/TLS certificate  
- Redirect all HTTP traffic to HTTPS  
- Enable HSTS (Strict-Transport-Security)  

---

### 2️⃣ Server Version Disclosure (nginx 1.19.0)

- Server version revealed in HTTP headers  
- Enables attackers to search for known exploits  

**Risk Level:** Medium  

**Remediation:**
- Hide server version details  
- Keep server software updated  
- Use generic server headers  

---

### 3️⃣ Missing Security Headers

Missing headers:
- X-Frame-Options  
- Content-Security-Policy  
- X-Content-Type-Options  

**Impact:**
- Clickjacking attacks  
- Increased XSS risk  
- Weak browser protection  

**Risk Level:** Medium  

**Remediation:**
- Configure recommended HTTP security headers  
- Implement via server configuration  

---

### 4️⃣ Input Validation & CSRF Issues

- Forms do not visibly sanitize inputs  
- No visible CSRF protection  
- Potential risk of XSS and injection attacks  

**Risk Level:** Medium  

**Remediation:**
- Validate and sanitize all user inputs  
- Use prepared statements for database queries  
- Implement CSRF tokens  
- Encode output properly  

---

### 5️⃣ Cookie Security Issues

- Cookies not marked as Secure  
- HttpOnly attribute missing  

**Risk Level:** Low  

**Remediation:**
- Set cookies with:
  - HttpOnly  
  - Secure  
  - SameSite attributes  

---

### 6️⃣ Deprecated Components (Flash)

- Flash components detected  

**Risk Level:** Low  

**Remediation:**
- Remove Flash components  
- Replace with secure HTML5 alternatives  

---

### 7️⃣ Insecure Cross-Domain Configuration

- clientaccesspolicy.xml allows wildcard (*) access  
- crossdomain.xml overly permissive  

**Risk Level:** Medium  

**Remediation:**
- Restrict access to trusted domains only  
- Remove wildcard (*) configurations  

---


