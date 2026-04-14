# Lab 4 - Directory Brute Force

> Lab Type: Web Enumeration / Reconnaissance

## Objective
The objective of this lab is to discover hidden directories and files on a web server using brute force techniques. This helps uncover unlinked or sensitive resources that may not be visible through normal browsing.

## Lab Environment
- Operating System: Kali Linux
- Tool: Gobuster
- Target: Local test web server / vulnerable application (e.g., DVWA)

## Tools Used
- Gobuster
- Wordlist (e.g., dirb/common.txt)

## Background
Web servers often contain hidden directories such as admin panels, backups, or configuration files. These are not always linked in the main application and can be discovered using directory brute forcing tools like Gobuster.

## Steps Performed

### 1. Prepare Wordlist
- Used a common wordlist for directory enumeration:
```
/usr/share/wordlists/dirb/common.txt
```

### 2. Run Gobuster Scan
Executed the following command:

```bash
gobuster dir -u http://<target-ip> -w /usr/share/wordlists/dirb/common.txt
```

- `dir`: Directory brute force mode  
- `-u`: Target URL  
- `-w`: Wordlist path  

## Scan Output (Example)

```bash
/admin          (Status: 301)
/login          (Status: 200)
/uploads        (Status: 301)
/config         (Status: 403)
```

## Result
- Discovered multiple hidden directories:
  - `/admin`
  - `/login`
  - `/uploads`
  - `/config`

## Analysis
- `/admin`: May contain administrative access panel  
- `/login`: Entry point for authentication  
- `/uploads`: Could expose user-uploaded files  
- `/config`: Restricted access, may contain sensitive configuration  

- Hidden directories increase the attack surface and may lead to further exploitation

## Impact
- Exposure of sensitive endpoints  
- Potential access to admin panels  
- Increased risk of unauthorized access  

## Key Takeaways
- Learned how to use Gobuster for directory enumeration  
- Understood the importance of hidden paths in web security  
- Recognized how attackers discover unlisted resources  

## Mitigation
- Disable directory listing  
- Restrict access to sensitive directories  
- Use authentication and proper access control  
- Regularly audit exposed endpoints  

## Notes
This lab was conducted in a controlled environment for educational purposes only.
