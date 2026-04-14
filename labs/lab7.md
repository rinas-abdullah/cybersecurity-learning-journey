# Lab 7 - Basic Log Analysis

> Lab Type: Blue Team / Security Monitoring

## Objective
The objective of this lab is to analyze system and web server logs to identify suspicious activities and understand how attacks can be detected.

## Lab Environment
- Operating System: Kali Linux / Ubuntu
- Tool: Terminal / Log files
- Target: Local system logs (e.g., Apache logs)

## Tools Used
- Linux Terminal
- `cat`, `grep`, `less`

## Background
Log analysis is a critical part of cybersecurity operations. Security analysts monitor logs to detect unusual behavior, unauthorized access, and potential attacks such as brute force attempts or SQL injection.

## Steps Performed

### 1. Locate Log Files
- Navigated to log directory:

```bash
cd /var/log/
```

- Common log files:
  - `auth.log`
  - `syslog`
  - `apache2/access.log`

### 2. View Logs
Displayed log contents:

```bash
cat apache2/access.log
```

Or used:

```bash
less apache2/access.log
```

### 3. Search for Suspicious Activity
Searched for unusual patterns:

```bash
grep "login" apache2/access.log
```

```bash
grep "admin" apache2/access.log
```

```bash
grep "SELECT" apache2/access.log
```

### 4. Identify Potential Attacks
Observed patterns such as:
- Multiple login attempts
- SQL keywords (e.g., SELECT, OR 1=1)
- Access to restricted directories

## Example Log Entry

```bash
192.168.1.5 - - [14/Apr/2026:12:30:25] "GET /login HTTP/1.1" 200
192.168.1.5 - - [14/Apr/2026:12:31:02] "GET /admin HTTP/1.1" 403
192.168.1.5 - - [14/Apr/2026:12:31:45] "GET /login?user=admin' OR 1=1 -- HTTP/1.1" 200
```

## Result
- Detected suspicious requests in logs
- Identified possible SQL Injection attempt
- Observed access attempts to restricted pages

## Analysis
- Repeated requests may indicate brute force attempts
- SQL patterns suggest injection attacks
- Access to `/admin` shows enumeration activity

## Impact
- Early detection of attacks
- Ability to respond before damage occurs
- Improved visibility of system activity

## Key Takeaways
- Logs are essential for detecting cyber attacks
- Pattern recognition is key in security monitoring
- Even simple tools like `grep` are powerful

## Mitigation
- Monitor logs continuously
- Implement alerting systems (SIEM)
- Restrict access to sensitive endpoints
- Apply intrusion detection systems (IDS)

## Notes
This lab was conducted in a controlled environment for educational purposes only.
