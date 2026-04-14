# Lab 2 - Web Vulnerability Scan

> Lab Type: Reconnaissance / Vulnerability Scanning

## Objective
The objective of this lab is to perform a basic web vulnerability scan using Nmap scripts (NSE) to identify potential weaknesses in a target web server.

## Lab Environment
- Operating System: Kali Linux
- Tool: Nmap (with NSE scripts)
- Target: Local test machine / vulnerable web application (e.g., DVWA)

## Tools Used
- Nmap (Network Mapper)
- Nmap Scripting Engine (NSE)

## Background
After identifying open ports in the previous lab, the next step is to analyze services running on those ports. Web servers, especially on port 80, may contain vulnerabilities that can be detected using automated scripts such as Nmap NSE.

## Steps Performed

### 1. Identify Web Service
- From the previous scan, port 80 (HTTP) was found open.
- This indicates a running web server.

### 2. Run Nmap Vulnerability Scan
Executed the following command to scan for common web vulnerabilities:

```bash
nmap -sV --script=vuln <target-ip>
```

- `-sV`: Detect service version  
- `--script=vuln`: Run vulnerability detection scripts  

## Scan Output (Example)

```bash
PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.49

| http-vuln-cve2021-41773:
|   VULNERABLE:
|   Path Traversal vulnerability
|_  State: VULNERABLE
```

## Result
- Detected running web server on port 80  
- Identified potential vulnerability using NSE scripts  

## Analysis
- Web servers are common attack targets  
- The detected vulnerability could allow unauthorized access to files  
- This highlights the importance of regularly updating and securing services  

## Key Takeaways
- Learned how to use Nmap NSE for vulnerability scanning  
- Understood how to analyze services beyond open ports  
- Gained deeper insight into the reconnaissance and scanning phase  

## Notes
This lab was conducted in a controlled environment for educational purposes only.
