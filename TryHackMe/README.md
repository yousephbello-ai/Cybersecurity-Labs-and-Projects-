Foundational Cybersecurity & Network Defense Labs
Author:Yusuf Bello
Track:Defensive Security / SOC Analyst Preparation  
Platform:TryHackMe  



Executive Summary
This document serves as a comprehensive portfolio of foundational hands-on cybersecurity labs completed on TryHackMe. It covers Linux command-line operations, network packet analysis with Wireshark, network scanning via Nmap, and brute-force mechanism testing using Hydra.



1.Module 1: Linux CLI & Command Line Mastery

#Objective
Understand basic Linux system navigation, file management, permissions, and log processing essential for Security Operations Center (SOC) analysis.

### 🛠️ Key Commands & Syntax
* `ls -la`: List all files, including hidden dotfiles and detailed permission flags.
* `grep -i "failed" /var/log/auth.log`: Search log files for failed authentication attempts.
* `chmod 700`: Restrict file access exclusively to the file owner.
* `awk` / `sed`: Parse and extract specific columns from plain-text security logs.






2.Module 2: Network Traffic Analysis (Wireshark)

#Objective
Analyze raw packet captures (`.pcap`) to detect unencrypted credentials, inspect HTTP headers, and identify malicious network traffic.

#Key Insights & Filters
*Display Filter `ip.addr == X.X.X.X`:** Isolates all inbound and outbound traffic for a target host.
*Display Filter `http.request.method == "POST"`:** Filters for form submissions, often exposing cleartext login attempts.
*Follow TCP Stream:** Reconstructs the complete conversation between client and server to observe transmitted payloads.






#3.Module 3: Network Reconnaissance & Port Scanning (Nmap)

#Objective
Perform active network reconnaissance to identify live hosts, open ports, running service versions, and underlying operating systems.

#Scan Flags & Methodology
```bash
# Comprehensive service version detection & default script scan
nmap -sV -sC -p- <target-ip>



#TryHackMe Room Completed: Hydra

-Status:Completed ✅
-Category:** Password Attacks & Network Brute-Forcing
*Key Concepts Mastered:**
  -Target enumeration for authentication endpoints (SSH, FTP, HTTP POST Forms).
  -Crafting syntax for user/password list attacks using `rockyou.txt`.
  -Capturing HTTP POST form parameters and specifying failure strings (`F=...`).
  -Analyzing defense mechanisms (Rate limiting, MFA, Account Lockout policies).

#Proof of Completion / Reflection:
Successfully enumerated and cracked target credentials across multiple protocol modules in the Hydra lab. Reinforced proper thread management (`-t`) and performance optimization during dictionary attacks.
