### Day 2: Security Frameworks (NIST CSF) & Basic Linux Privilege Escalation

**Date:** August 4, 2026  
**Focus:** Risk Management, System Auditing, and SUID Privilege Escalation  

#### Key Learnings
- **NIST CSF 5 Core Functions:** Explored Identify, Protect, Detect, Respond, and Recover; aligned functions with real-world incident handling scenarios (e.g., host isolation under *Respond*).
- **Linux Security Controls:** Audited file permissions via octal notation (`chmod 600` for owner-only read/write access) and network socket monitoring via `ss -tulpn`.

#### Practical Lab Exercise: Linux Privilege Escalation via SUID
- **Scenario:** Initial access as `www-data` on a simulated target host.
- **Reconnaissance:** Located misconfigured binaries using `find / -perm -4000 -type f 2>/dev/null`.
- **Exploitation:** Identified an abnormally permitted SUID binary (`/usr/bin/env`) and leveraged it to execute `/usr/bin/env /bin/sh -p`, escalating privileges to `root` (`euid=0`).
- **Remediation:** Revoked the unnecessary SUID bit using `chmod u-s /usr/bin/env`.