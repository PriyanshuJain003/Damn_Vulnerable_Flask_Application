# Damn Vulnerable Flask Shop App

A deliberately vulnerable web application built with **Python (Flask)** and **SQLite** for educational, CTF, and penetration-testing purposes.

This application intentionally demonstrates common web security vulnerabilities in a realistic business-style portal.

---

## Table of Contents

- Features
- Vulnerabilities Demonstrated
- Prerequisites
- Installation
- Usage
- Security Characteristics
- Project Structure
- Educational Goals
- Important Security Notes
- License

---

## Features

- Intentionally insecure authentication system
- Raw SQL queries using string concatenation
- Role-based accounts without enforcement
- Admin dashboard accessible to all users
- Insecure Direct Object References (IDOR)
- Insecure deserialization using pickle
- Debug mode enabled for learning

---

## Vulnerabilities Demonstrated

- SQL Injection (authentication, search, profile, orders)
- Broken Authentication
- Broken Access Control
- Insecure Direct Object References (IDOR)
- Insecure Deserialization (RCE)
- Security Misconfiguration
- Sensitive Data Exposure

---

## Prerequisites

- Python 3.9+
- pip
- Local or lab environment only

---

## Installation

```bash
git clone https://github.com/yourusername/damn-vulnerable-flask-shop.git
cd Damn_Vulnerable_Flask_Application
pip install flask
```

---

## Usage

```bash
cd vuln exp
python app.py
```

Access:
- http://127.0.0.1:5000/login
- http://127.0.0.1:5000/admin

Default credentials:
- admin / admin123
- user1 / user123

---

## Security Characteristics

### Vulnerable by Design

- Plaintext passwords
- No input validation
- No authorization checks
- Unsafe pickle deserialization
- Hardcoded secret key

---

## Project Structure

```
.
├── app.py
├── database.py
├── exploit.py
├── templates/
├── static/
└── shop.db
```

---

## Educational Goals

- Learn how real-world vulnerabilities arise
- Practice exploitation techniques
- Understand insecure design decisions
- Prepare for CTF-style challenges

---

## Important Security Notes

⚠️ WARNING

This application is intentionally vulnerable.
DO NOT deploy to production.
Use only in controlled environments.

---

## License

Educational use only.
