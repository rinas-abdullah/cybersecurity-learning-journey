# Lab 5 - Cross-Site Scripting (XSS)

> Lab Type: Web Application Security / Exploitation

## Objective
The objective of this lab is to understand how Cross-Site Scripting (XSS) works and how attackers can inject malicious scripts into web applications to execute code in a victim’s browser.

## Lab Environment
- Operating System: Kali Linux
- Tool: Web Browser
- Target: Vulnerable web application (e.g., DVWA)

## Tools Used
- Web Browser
- DVWA (Damn Vulnerable Web Application)

## Background
Cross-Site Scripting (XSS) is a common web vulnerability that allows attackers to inject malicious JavaScript into web pages viewed by other users. This can lead to session hijacking, data theft, or malicious redirection.

## Steps Performed

### 1. Identify Input Field
- Navigated to a page that accepts user input (e.g., comment field or search box)
- Observed that the input is reflected on the page

### 2. Test for XSS Vulnerability
Entered the following payload:

```html
<script>alert('XSS')</script>
```

### 3. Execute Payload
- Submitted the input
- Observed that a popup alert was triggered

## Result
- Successfully executed JavaScript in the browser
- Confirmed that the application is vulnerable to XSS

## Analysis
- The application does not properly sanitize user input
- The script is executed directly in the browser
- This indicates a Reflected or Stored XSS vulnerability

## Impact
- Session hijacking
- Cookie theft
- Defacement of web pages
- Redirection to malicious websites

## Key Takeaways
- XSS allows execution of malicious scripts in user browsers
- Input validation and output encoding are critical
- Even simple input fields can be dangerous if not secured

## Mitigation
- Validate and sanitize all user input
- Use output encoding (e.g., HTML entities)
- Implement Content Security Policy (CSP)
- Use secure frameworks that prevent XSS by default

## Notes
This lab was conducted in a controlled environment for educational purposes only.
