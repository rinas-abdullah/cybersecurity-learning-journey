# Lab 3 - SQL Injection

> Lab Type: Web Application Security / Exploitation

## Objective
The objective of this lab is to understand how SQL Injection attacks work and how attackers can exploit vulnerable web applications to bypass authentication and access sensitive data.

## Lab Environment
- Operating System: Kali Linux
- Tool: Web Browser / Burp Suite (optional)
- Target: Vulnerable web application (e.g., DVWA)

## Tools Used
- Web Browser
- DVWA (Damn Vulnerable Web Application)
- (Optional) Burp Suite

## Background
SQL Injection (SQLi) is one of the most common web application vulnerabilities. It occurs when user input is not properly sanitized, allowing attackers to inject malicious SQL queries into a database. This can lead to unauthorized access, data leakage, or even full system compromise.

## Steps Performed

### 1. Identify Vulnerable Input Field
- Navigated to the login page of the vulnerable web application
- Observed input fields for username and password

### 2. Test for SQL Injection
Entered the following payload into the login form:

```
' OR 1=1 --
```

- This payload attempts to bypass authentication by always evaluating the condition as true

### 3. Submit the Request
- Entered payload in the username field
- Entered any value in the password field
- Submitted the login form

## Result
- Successfully bypassed authentication without valid credentials
- Gained access to the application

## Analysis
- The application does not properly sanitize user input
- The SQL query likely becomes:

```sql
SELECT * FROM users WHERE username = '' OR 1=1 -- ' AND password = 'anything';
```

- The condition `1=1` is always true, allowing login bypass
- The `--` comments out the rest of the query

## Impact
- Unauthorized access to the system
- Potential exposure of sensitive user data
- Risk of full database compromise

## Key Takeaways
- SQL Injection is a critical vulnerability in web applications
- Input validation and parameterized queries are essential
- Never trust user input without proper sanitization

## Mitigation
- Use prepared statements (parameterized queries)
- Implement input validation and sanitization
- Use Web Application Firewalls (WAF)
- Apply least privilege to database accounts

## Notes
This lab was conducted in a controlled environment for educational purposes only.
