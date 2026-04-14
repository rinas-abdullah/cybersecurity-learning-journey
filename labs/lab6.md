# Lab 6 - Burp Suite Request Interception

> Lab Type: Web Application Security / Traffic Analysis

## Objective
The objective of this lab is to understand how to intercept, analyze, and modify HTTP requests using Burp Suite. This helps in identifying vulnerabilities and manipulating web application behavior.

## Lab Environment
- Operating System: Kali Linux
- Tool: Burp Suite
- Target: Vulnerable web application (e.g., DVWA)

## Tools Used
- Burp Suite Community Edition
- Web Browser (configured with proxy)

## Background
Burp Suite is one of the most powerful tools used in web application security testing. It allows security testers to intercept HTTP/HTTPS traffic between the browser and the server, analyze requests, and modify them before reaching the target.

## Steps Performed

### 1. Configure Browser Proxy
- Set browser proxy to:
  - IP: `127.0.0.1`
  - Port: `8080`
- Enabled Burp Suite proxy listener

### 2. Enable Interception
- Opened Burp Suite
- Navigated to **Proxy → Intercept**
- Turned interception **ON**

### 3. Capture HTTP Request
- Accessed the target web application (e.g., login page)
- Entered login credentials
- Captured the HTTP request in Burp Suite

## Captured Request (Example)

```http
POST /login HTTP/1.1
Host: <target-ip>
Content-Type: application/x-www-form-urlencoded

username=admin&password=1234
```

### 4. Modify Request
- Changed parameters in the request:
  - Example:
```
username=admin' OR 1=1 -- &password=anything
```

- Forwarded the modified request

## Result
- Successfully modified HTTP request before reaching the server
- Observed different application behavior based on modified input

## Analysis
- Intercepting requests allows deeper control over application interaction
- Input manipulation can reveal hidden vulnerabilities (e.g., SQL Injection)
- Useful for bypassing client-side validation

## Impact
- Ability to test authentication bypass
- Identify input validation flaws
- Discover hidden parameters and logic flaws

## Key Takeaways
- Learned how to intercept and modify HTTP traffic
- Understood how web applications process user input
- Gained hands-on experience with Burp Suite

## Mitigation
- Validate input on the server-side
- Implement proper authentication mechanisms
- Use secure coding practices
- Monitor and log suspicious activity

## Notes
This lab was conducted in a controlled environment for educational purposes only.
