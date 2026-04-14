# Lab 1 - Basic Network Scan

## Objective
Understand how to scan a network and identify open ports using Nmap.

## Tools Used
- Kali Linux
- Nmap

## Steps Performed
1. Identified target IP address
2. Ran Nmap scan:
   ```bash
   
nmap -sS <target-ip>

## Result
- Open ports found:
  - 22 (SSH)
  - 80 (HTTP)
This indicates that the target system is running SSH and HTTP services.

## Key Takeaways
- Learned how to use Nmap
- Understood basic network scanning
