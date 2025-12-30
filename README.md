# Damn Vulnerable Flask Shop App

A deliberately vulnerable web application built with **Python (Flask)** and **SQLite** for **educational, CTF, and penetration-testing purposes**.  
This application demonstrates common web security vulnerabilities in a realistic business-style portal, allowing learners to practice exploitation and understand insecure design patterns.

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
- Contributing
- License

---

## Features

- **Intentionally Insecure Design**: Built to be broken, not protected
- **Role-Based Accounts**: Customer, Staff, and Admin users
- **Authentication System**: Login using raw SQL queries
- **Shop Interface**: Products, orders, profiles, and admin dashboard
- **Multiple Vulnerabilities**: SQL Injection, IDOR, Broken Access Control, Insecure Deserialization
- **CTF-Friendly**: Clear exploit paths and vulnerability chaining
- **Minimal Stack**: Flask + SQLite with no security middleware

---

## Vulnerabilities Demonstrated

- **SQL Injection**
  - Authentication bypass
  - Data extraction via UNION-based attacks
  - Injection in search, profile, and order endpoints

- **Broken Authentication**
  - Plaintext password storage
  - No hashing or salting
  - No rate limiting
  - User-controlled role selection

- **Broken Access Control**
  - Any authenticated user can access admin routes
  - No role verification on sensitive endpoints

- **Insecure Direct Object References (IDOR)**
  - Access other users’ profiles and orders
  - Enumerate objects via predictable IDs

- **Insecure Deserialization**
  - Unsafe use of Python `pickle`
  - Remote Code Execution via crafted payloads

- **Security Misconfiguration**
  - Hardcoded Flask secret key
  - Debug mode enabled
  - Verbose SQL query logging
  - No CSRF protection

- **Sensitive Data Exposure**
  - Plaintext credentials
  - Session data trusted blindly
  - User roles exposed to templates

---

## Prerequisites

- Python **3.9 or higher**
- pip (Python Package Manager)
- A local or lab environment (DO NOT expose publicly)

---

## Installation

Clone the repository:

```bash
git clone https://github.com/yourusername/damn-vulnerable-flask-shop.git
Navigate to the project directory:

bash
Copy code
cd damn-vulnerable-flask-shop
(Optional but recommended) Create a virtual environment:

bash
Copy code
python -m venv venv
source venv/bin/activate   # Linux / macOS
venv\Scripts\activate      # Windows
Install dependencies:

bash
Copy code
pip install flask
Usage
Start the application:

bash
Copy code
python app.py
Open your browser and navigate to:

Login Page: http://127.0.0.1:5000/login

Dashboard: http://127.0.0.1:5000/dashboard

Admin Panel: http://127.0.0.1:5000/admin

Default Test Credentials
Role	Username	Password
Customer	user1	user123
Staff	staff1	staff123
Admin	admin	admin123

Security Characteristics
Vulnerable Implementation (Intentional)
Raw SQL queries with string concatenation

No input validation or sanitization

Plaintext password storage

No authorization checks

Unsafe deserialization using pickle

Predictable object identifiers

Hardcoded session secret

What a Secure Version Would Use (Not Implemented)
Parameterized SQL queries

Password hashing (bcrypt/argon2)

Proper role-based access control

Ownership checks for resources

Safe serialization formats (JSON)

CSRF protection

Secure session handling

Project Structure
pgsql
Copy code
.
├── app.py               # Main Flask application (vulnerable)
├── database.py          # SQLite database initialization
├── exploit.py           # Example RCE exploit using pickle
├── templates/           # HTML templates (trust user input)
│   ├── login.html
│   ├── dashboard.html
│   ├── profile.html
│   ├── orders.html
│   └── admin.html
├── static/
│   └── style.css
└── shop.db              # SQLite database (generated at runtime)
Educational Goals
This application is designed to help:

Students understand real-world web vulnerabilities

Developers recognize insecure coding patterns

Security professionals practice exploitation techniques

CTF players learn vulnerability chaining

Educators demonstrate OWASP Top 10 issues in action

The emphasis is on understanding root causes, not just exploiting bugs.

Important Security Notes
⚠️ WARNING

This application contains intentional and severe security vulnerabilities.

NEVER deploy this application in production

NEVER expose it to the public internet

Use only in controlled, local, or lab environments

You are responsible for how you use this software.

Contributing
Contributions that improve the educational value of the project are welcome.

Suggested contributions:

New vulnerable endpoints

Write-ups for exploitation paths

Secure vs insecure comparisons

Documentation improvements

Steps:

Fork the repository

Create a feature branch

Make your changes

Document any new vulnerabilities

Submit a pull request

License
This project is intended strictly for educational purposes.

No warranty is provided.
Use responsibly and ethically.

yaml
Copy code

---

If you want next, I can:

- Split this into **Introduction.md / Architecture.md / Vulnerabilities.md**
- Create a **secure vs vulnerable comparison guide**
- Add **exploit walkthroughs** per vulnerability
- Align each section explicitly to **OWASP Top 10 (2021/2023)**