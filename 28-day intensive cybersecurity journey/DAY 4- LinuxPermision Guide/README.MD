
# Day 4: Linux File Permissions, Text Manipulation & Control 

## Overview 
This documentation covers the core concepts and practical exercises for **Day 4** of the Cybersecurity Learning Path. Today's focus centers on Linux access control, file permission management, text manipulation using filtering tools, and basic execution workflow security. 

## 1. Linux Permission Architecture 
In Linux, security and access control are built around file ownership and permission bits. Every file and directory is assigned to a specific **User (Owner)** and a **Group**, while defining access for **Others**. 

# Permission Tiers
 * **User (`u`):** The individual account that owns the file. * **Group (`g`):** A set of users sharing common access rights. 
* **Others (`o`):** Every other user account on the system. 

### Permission Types & Octal Values 
| Permission | Symbol | Binary Representation | Octal Value | Description | 
| :--- | :---: | :---: | :---: | :--- | 
| **Read** | `r` | `100` | **4** | Allows viewing file contents or listing directory contents. | 
| **Write** | `w` | `010` | **2** | Allows modifying file contents or adding/deleting files in a directory. | 
| **Execute** | `x` | `001` | **1** | Allows running a file as a program/script or traversing a directory. | 
| **None** | `-` | `000` | **0** | Grants no permissions. | 

## 2. Permission Notation Guide 
### Octal Matrix Calculation Permissions are expressed as a 3-digit octal number derived from adding values for User, Group, and Others: 
$$ \text{Octal Value} = \text{Read (4)} + \text{Write (2)} + \text{Execute (1)} $$ 
* **`7`** ($4+2+1$) = Full access (`rwx`) 
* **`6`** ($4+2+0$) = Read & Write (`rw-`) 
* **`5`** ($4+0+1$) = Read & Execute (`r-x`) 
* **`4`** ($4+0+0$) = Read-only (`r--`) 
* **`0`** ($0+0+0$) = No access (`---`) 

### Common Octal Configurations 
```text 
644 (-rw-r--r--) -> Owner: Read/Write | Group: Read-only | Others: Read-only (Standard files) 

755 (-rwxr-xr-x) -> Owner: Read/Write/Exec | Group: Read/Exec | Others: Read/Exec (Scripts/Binaries) 

600 (-rw-------) -> Owner: Read/Write | Group: None | Others: None (Sensitive files/Keys) 

700 (-rwx------) -> Owner: Read/Write/Exec | Group: None | Others: None (Private scripts) ``` 

## 3. Practical Lab Walkthrough & Verification 
### Lab 1: Permission Audit Matrix Created three target files and applied differential access privileges applying the 

**Principle of Least Privilege**: 

```bash 
# 1. Create target lab files touch public.txt team.txt secret.txt 

# 2. Assign octal permission levels chmod 644 public.txt # Owner: rw-, Group: r--, Others: r-- chmod 640 team.txt # Owner: rw-, Group: r--, Others: --- chmod 600 secret.txt # Owner: rw-, Group: ---, Others: --- 

# 3. Verify file permissions ls -l public.txt team.txt secret.txt 

``` **Verified Terminal Output:**
b
```text 
-rw-r--r-- 1 user user 0 Aug 7 06:30 public.txt 
-rw-r----- 1 user user 0 Aug 7 06:30 team.txt 
-rw------- 1 user user 0 Aug 7 06:30 secret.txt ``` 

### Lab 2: Log Analysis & Text Filtering with `grep` 
Simulated web server log filtering to isolate error responses (`404 Not Found` and `500 Internal Server Error`). 

```bash 
# 1. Create test log file : cat << 'EOF' > access.log 

192.168.1.10 - - [06/Aug/2026:10:00:01] "GET /index.html HTTP/1.1" 200 1024 

192.168.1.12 - - [06/Aug/2026:10:00:05] "GET /admin.php HTTP/1.1" 404 512 192.168.1.15 - - [06/Aug/2026:10:00:10] "POST /login HTTP/1.1" 500 256 

192.168.1.10 - - [06/Aug/2026:10:00:15] "GET /style.css HTTP/1.1" 200 2048 192.168.1.20 - - [06/Aug/2026:10:00:20] "GET /config.bak HTTP/1.1" 404 128 EOF 

# 2. Isolate client error and server error codes using Extended Regex (-E) grep -E "404|500" access.log ``` 

**Verified Output:** ```text
192.168.1.12 - - [06/Aug/2026:10:00:05] "GET /admin.php HTTP/1.1" 404 512 

192.168.1.15 - - [06/Aug/2026:10:00:10] "POST /login HTTP/1.1" 500 256 192.168.1.20 - - [06/Aug/2026:10:00:20] "GET /config.bak HTTP/1.1" 404 128 ```  

### Lab 3: Script Execution Permission Control 
Demonstrated system security enforcement when executing binary files or shell scripts. 

```bash 
# 1. Write simple bash script cat << 'EOF' > hello.sh #!/bin/bash echo "Permission Granted! Day 4 Practical Complete." EOF 

# 2. Execution attempt prior to permission modification ./hello.sh # Result -> bash: ./hello.sh: Permission denied 

# 3. Add execute bit for user owner chmod +x hello.sh 

# 4. Verify permission string updated (-rwxr-xr-x) ls -l hello.sh 

# 5. Execute script ./hello.sh # Result -> Permission Granted! Day 4 Practical Complete. ``` 

## 4. Key Command Reference 
| Command | Usage / Purpose | Example | 
| :--- | :--- | :--- | 
| `chmod` | Change file access permissions | `chmod 755 script.sh` | 
| `chown` | Change file owner and group | `sudo chown root:root file.txt` | 
| `grep` | Filter text using pattern matching | `grep -i "error" /var/log/syslog` | 
| `cat` | Concatenate and print file contents | `cat file.txt` | 
| `head` | Output top $N$ lines of a file | `head -n 20 access.log` | | `tail` | Output bottom $N$ lines of a file 
| `tail -n 20 access.log` | 
| `>` | Redirection operator (Overwrite) | `echo "data" > log.txt` | 
| `>>` | Redirection operator (Append) | `echo "data" >> log.txt` | 

## 5. Security Takeaways 

1. **Principle of Least Privilege (PoLP):** Files should only be assigned the absolute minimum permissions required to perform their intended function. 

2. **Execution Boundary:** In Unix-like environments, file extension (`.sh`, `.exe`) does not dictate execution capabilityâ€”the execute mode bit (`x`) enforced by the kernel dictates file execution. 

3. **Log Filtering:** Command-line text utilities (`grep`, `tail`, `head`) form the foundation of command-line Security Information and Event Management (SIEM) analysis and incident