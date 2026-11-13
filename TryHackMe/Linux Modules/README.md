# TryHackMe - Linux Modules

A repository documenting my progress, hands-on labs, and command-line reference notes from completing the Linux learning paths on [TryHackMe](https://tryhackme.com).

## 🛠️ Key Topics Covered
- **Navigation & File Management:** Navigating the directory tree (`cd`, `ls`, `pwd`), creating and manipulating files/directories (`mkdir`, `touch`, `cp`, `mv`, `rm`).
- **Permissions & Access Control:** Managing user/group permissions using `chmod`, `chown`, and understanding SUID/SGID bits.
- **Text Manipulation & Filtering:** Searching and parsing logs using `grep`, `awk`, `sed`, `head`, `tail`, and redirection (`>`, `>>`, `|`).
- **Process & Service Management:** Monitoring system processes (`ps`, `top`, `htop`, `kill`) and managing systemd services (`systemctl`).
- **Networking Basics:** Checking network interfaces, open ports, and connectivity (`ip`, `ss`, `netstat`, `ping`, `curl`).

## 📑 Quick Command Reference
A quick look at some of the most useful commands practiced during these labs:
```bash
# Find files modified in the last 2 days
find /var/log -type f -mtime -2

# Search recursively for a specific string in configuration files
grep -rnw '/etc/' -e 'password'

# View active listening ports and their associated processes
ss -tulpn
