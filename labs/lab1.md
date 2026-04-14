# Lab 1 - Basic Network Scan

> Lab Type: Reconnaissance / Network Scanning

## Objective
The objective of this lab is to understand how to perform a basic network scan using Nmap and identify open ports and running services on a target system. This helps in understanding the attack surface of a system during the reconnaissance phase.

## Lab Environment
- Operating System: Kali Linux
- Tool: Nmap
- Target: Local test machine / lab environment (e.g., virtual machine)

## Tools Used
- Nmap (Network Mapper)

## Background
Network scanning is a fundamental step in cybersecurity, especially in penetration testing. It allows security professionals to discover devices, open ports, and services running on a system. These services may present potential entry points for attackers if not properly secured.

## Steps Performed

### 1. Identify Target
- Selected a target machine within a controlled lab environment.
- Obtained the IP address of the target.

### 2. Run Nmap Scan
Executed the following command to perform a TCP SYN scan:

```bash
nmap -sS <target-ip>
```

This command performs a TCP SYN scan to quickly identify open ports on the target system.

## Result
The scan revealed the following open ports:

- 22 (SSH)
- 80 (HTTP)

This indicates that the target system is running SSH and HTTP services.

## Analysis
- Port 22 (SSH): Used for secure remote access.
- Port 80 (HTTP): Indicates a running web service.
- These open ports increase the attack surface and should be reviewed.

## Key Takeaways
- Learned how to use Nmap for network scanning.
- Understood how to identify open ports and services.
- Gained insight into the reconnaissance phase in cybersecurity.

## Notes
This lab was conducted in a controlled environment for educational purposes only.
