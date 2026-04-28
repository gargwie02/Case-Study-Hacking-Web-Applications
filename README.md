# Case-Study-Hacking-Web-Applications
# 🔐 Web Application Security Assessment – Detailed Case Study

---

## 🚀 Introduction

This repository documents a **comprehensive web application penetration testing case study** performed in a controlled and authorized lab environment.

The objective of this assessment was to simulate a **real-world security evaluation workflow**, identify vulnerabilities, understand their impact, and demonstrate how multiple vulnerabilities can be **chained together to achieve full system compromise**.

---

## 🎯 Objectives

- Perform **network reconnaissance**
- Identify **technologies and application stack**
- Intercept and analyze HTTP traffic
- Detect and exploit common vulnerabilities:
  - SQL Injection
  - Cross-Site Scripting (XSS)
  - Insecure Direct Object Reference (IDOR)
  - Server-Side Request Forgery (SSRF)
- Understand **attack chaining**
- Document findings professionally

---

## 🌐 Target Environment

> ⚠️ All testing was conducted on **authorized and safe environments only**

Targets used:
- http://testfire.net
- http://testphp.vulnweb.com

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|--------|
| Nmap | Network scanning & service detection |
| WhatWeb | Technology fingerprinting |
| Burp Suite | HTTP interception & manipulation |
| Web Browser | Interaction with application |

---

## 🧭 Methodology Overview

The assessment followed a structured approach:

```text
Reconnaissance → Technology Detection → Traffic Analysis → Exploitation → Impact Analysis → Reporting# 🔐 Web Application Security Assessment – Case Study

This repository presents a complete web application security assessment carried out in a controlled and authorized environment, designed to simulate a real-world penetration testing scenario. The goal of this case study was not only to use tools, but to understand how an attacker thinks, how vulnerabilities are discovered step by step, and how seemingly independent weaknesses can be chained together to achieve full system compromise.

The assessment began with network reconnaissance to understand the attack surface of the target application. Using Nmap with service detection enabled, the scan revealed that the application was accessible over standard web ports such as HTTP (port 80) and HTTPS (port 443). This confirmed that the primary interaction point would be through a browser-based interface, and that the focus of testing would shift toward web application vulnerabilities. The corresponding evidence for this phase is captured in `01_nmap_scan.png`, which demonstrates the discovery of active services and validates that the target is a web-based system.

Following the initial discovery phase, technology fingerprinting was performed using WhatWeb to identify the underlying stack used by the application. The results indicated the presence of an Apache web server, along with backend technologies such as Java or PHP, and session management through cookies like JSESSIONID. This information is critical because different technologies introduce different classes of vulnerabilities, and knowing the stack allows an attacker to choose more targeted and effective techniques. The findings from this phase are documented in `02_whatweb_output.png`, where the detected technologies and session mechanisms are visible.

With a clear understanding of the application environment, the next step involved intercepting and analyzing live HTTP traffic using Burp Suite. By configuring the browser to route traffic through a proxy (127.0.0.1:8080) and enabling interception, it became possible to observe the exact requests being sent from the client to the server. This step marks a crucial transition from passive observation to active control, as requests can now be modified before reaching the server. In `03_burp_intercept.png`, an example request is shown, including headers and session cookies such as JSESSIONID, which represent the identity of the user within the application. Controlling or manipulating such values can directly impact authentication and authorization behavior.

Once traffic interception was established, vulnerability testing began. The first vulnerability explored was SQL Injection, where user input fields were manipulated using payloads such as `' OR '1'='1`. This payload alters the logic of backend database queries, forcing conditions to evaluate as true regardless of actual credentials. As a result, authentication mechanisms can be bypassed entirely, allowing unauthorized access to the application. This behavior is demonstrated in `04_sqli.png`, where login is successfully achieved without valid credentials. The impact of this vulnerability is severe, as it compromises the integrity of the authentication system and may expose sensitive data.

The assessment then proceeded to Cross-Site Scripting (XSS), where malicious JavaScript code was injected into input fields using payloads like `<script>alert(1)</script>`. Because the application failed to properly sanitize user input, the script executed within the browser context, confirming the presence of an XSS vulnerability. This is shown in `05_xss.png`, where a JavaScript alert is triggered. While this example demonstrates a simple alert, in real scenarios this could be used to steal session cookies, redirect users, or perform actions on behalf of the victim, potentially leading to account takeover.

Next, Insecure Direct Object Reference (IDOR) was tested by modifying parameters in requests, such as changing `?id=100` to `?id=101`. This simple manipulation resulted in access to another user’s data, indicating that the application failed to enforce proper authorization checks. The evidence is shown in `06_idor.png`, where unauthorized data access is visible. This vulnerability highlights a critical flaw in access control, where users can retrieve or manipulate resources that should be restricted.

The final vulnerability explored was Server-Side Request Forgery (SSRF), which involves tricking the server into making requests to internal or otherwise restricted resources. By supplying inputs such as `http://127.0.0.1`, the server was observed attempting to access internal services, as shown in `07_ssrf.png`. This type of vulnerability is particularly dangerous because it allows attackers to bypass network boundaries, interact with internal systems, and potentially access sensitive configurations or metadata.

While each vulnerability is impactful on its own, the most critical insight from this case study is how these vulnerabilities can be chained together. An attacker could use SQL Injection to gain initial access, leverage IDOR to expand that access across user accounts, exploit XSS to hijack sessions, and finally use SSRF to interact with internal infrastructure. This chain transforms isolated weaknesses into a full compromise scenario, demonstrating the importance of holistic security rather than isolated fixes.

Through this assessment, it becomes clear that web application security is not about individual tools, but about understanding system behavior, identifying trust boundaries, and thinking critically about how data flows through an application. Each step in this process builds upon the previous one, forming a structured methodology that reflects real-world penetration testing practices.

This project serves as a practical demonstration of that methodology, combining reconnaissance, analysis, exploitation, and impact assessment into a single coherent workflow. All testing was conducted on authorized environments for educational purposes, and the goal of this work is to strengthen understanding of web security concepts and responsible ethical hacking practices.

If you find this project insightful, feel free to explore the screenshots, review the methodology, and connect to discuss further improvements and learning opportunities.**
