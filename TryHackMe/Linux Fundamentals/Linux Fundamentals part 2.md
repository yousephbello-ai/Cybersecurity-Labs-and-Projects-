# TryHackMe: Linux Fundamentals Part 2 — Write-up

Welcome to my write-up for **Linux Fundamentals Part 2** on [TryHackMe](https://tryhackme.com). Building upon basic terminal navigation, this room covers administrative tasks, user permissions, process management, and package installation.

---

## 📌 Room Overview
* **Platform:** TryHackMe
* **Module:** Linux Fundamentals Part 2
* **Difficulty:** Beginner / Intermediate
* **Objective:** Understand Linux permissions, user privilege escalation, package management, system logging, and process handling.

---

## 🛠️ Key Commands & Concepts Learned

### 1. Privilege Escalation & User Switching
* `su`: Switch user account (e.g., `su root` to log in as superuser).
* `sudo`: Execute commands with administrative/root privileges (e.g., `sudo apt update`).

### 2. File Ownership & Permissions
* `chmod`: Modifies read (`r`), write (`w`), and execute (`x`) permissions for Owner, Group, and Others.
* `chown`: Changes the owner and group of a file or directory.

### 3. Package Management
* `apt`: Command-line tool for managing Debian/Ubuntu packages.
  * `apt update` & `apt upgrade`: Refresh repositories and update installed software.
  * `apt install <package>` & `apt remove <package>`: Install or uninstall software packages.

### 4. Process Management
* `ps`: Displays active running processes in the current session (`ps aux` lists all system processes).
* `top` / `htop`: Real-time system monitoring tool for viewing CPU, memory usage, and running tasks.
* `kill` / `killall`: Terminate processes using their Process ID (PID) or process name.

### 5. System Logs & Services
* `systemctl`: Manage system services (e.g., `systemctl start apache2`, `systemctl status SSH`).
* `/var/log`: Key directory containing system, authentication (`auth.log`), and service logs essential for forensic analysis.

---

## 🚀 Next Steps
All tasks and interactive flag challenges completed! Ready to tackle **Linux Fundamentals Part 3**!
