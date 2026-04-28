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
Reconnaissance → Technology Detection → Traffic Analysis → Exploitation → Impact Analysis → Reporting
