#  Bug Bounty Report 
**Reflected XSS • Missing CSRF Protection • Clickjacking**

This repository showcases a full bug‑bounty‑style security assessment performed for academic purposes, featuring real-world methodologies, PoCs, and validated vulnerabilities discovered during ethical testing.

---

##  Overview

The project demonstrates a full manual penetration testing workflow, including:

- **Reconnaissance**
- **Scanning & mapping**
- **Vulnerability discovery**
- **Proof-of-Concept demonstrations**
- **Exploitation**
- **Technical remediation**
- **Reflections & challenges**

---

##  Vulnerabilities Identified

The assessment confirmed **three major security issues**, each validated with non-destructive Proof-of-Concepts (PoCs).

---

###  1. Reflected Cross-Site Scripting (XSS)

User input was reflected directly into the HTML response without proper encoding, allowing attacker‑supplied JavaScript to execute.

**Impact:** Session hijacking, credential theft, phishing, UI manipulation  
**Severity:** **High**  
**OWASP Category:** **A03 – Injection**

---

###  2. Cross-Site Request Forgery (CSRF)

Sensitive actions such as profile updates lacked CSRF tokens and Origin/Referer validation.  
A malicious cross‑origin form successfully triggered state‑changing actions on behalf of an authenticated user.

**Impact:** Account takeover, unauthorized profile modification  
**Severity:** **High**  
**OWASP Category:** **A08 – CSRF**

---

###  3. Clickjacking (Missing Frame Protection)

The site did not send `X-Frame-Options` or a `frame-ancestors` CSP directive, allowing full framing from external origins.

**Impact:** Click redirection, unintended actions, UI deception  
**Severity:** **Medium**  
**OWASP Category:** **A05 – Security Misconfiguration**

---

##  Methodology

The assessment followed a **structured and repeatable penetration testing workflow**:

### **1. Reconnaissance**
- Amass  
- WhatWeb  
- WAFW00F  
- Nmap  

### **2. Scanning & Mapping**
- OWASP ZAP (spider + passive scan)  
- Burp Suite (proxy interception & sitemap)

### **3. Exploitation**
- Crafted PoCs manually  
- Used Burp Repeater for testing  
- HTML CSRF attack page  
- Browser DevTools for DOM inspection

### **4. Verification & Documentation**
Reproduced findings, captured evidence, and documented all vulnerabilities clearly.

---

