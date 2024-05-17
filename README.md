## DevOps Bootcamp: Learn Linux & Become a Linux Sysadmin

# Cahper 1. Setting Up the Environment

- Explanation of several Linux Distribution
- Installing Ubuntu in a VM. This took a while. I had to do it twice!

# Capter 2. The Linux Terminal in Depth

- Terminals, Consoles, Shells and Command
- Linux Command Structure
- Getting Help, Man Pages (man, type, help, apropos)
- Mastering the Terminal: The TAB Key (auto complition)
- Mastering the Terminal: Keyboard Shortcuts. Beginning line (control + a). End line (control + e)
- Mastering the Terminal: the Bash History
- Running Commands Without Leaving a Trace
- Recording the Date and Time for Each Line in History
- root vs. non-Privileged Users. Getting root Access (sudo, su, passwd)

# Chapter 3. The Linux File System

- Intro to The Linux Files System
- The Filesystem Hierarchy Standard ( FHS)
- Absolute vs. Relative Paths. Walking through the File System (pwd, cd, tree). Print current directory (pwd). Profile folder (cd ~)
- The LS Command In Depth (ls)
- Understanding File Timestamps: atime, mtime, ctime (stat, touch, date). Create file (touch). Check timestand (stat)
- Sorting Files by Timestam
- File Types in Linux (ls -F, file)
- Viewing Files - Part 1 (cat)
- Viewing Files - Part 2 (less, more)
- Viewing Files - Part 3 (tail, head, watch)
- Creating Files and Directories (touch, mkdir)
- Copying Files and Directories (cp)
- Moving and Renaming Files and Directories (mv)
- Removing Files and Directories (rm, shred)
- Working With Pipes in Linux (|, wc). example how to find a specific line in a file
- Command Redirection (>, >>, 2> &>, cut, tee). tee copy into a file and print it in the terminal
- Finding Files and Directories - Part 1 (locate, which). locate for file and which for executables
- Finding Files and Directories - Part 2 (find). locate search in system database (plocate.db) and find search in real time
- Find and Exec:
  Ex Find files in the last 24 hours and execute them.
  Ex ind files modified in the last 7 days in directory /etc/ and copy into a backup directory in /root/
  run the previos command but first asking if I want to copy a file, one by one, I sustitute [-exec] for [-ok]
- Searching for String Patterns in Text Files (grep)
- Searching for Strings in Binary Files (strings)
- Comparing Files (cmp, diff, sha256)
- The Basics of VIM Text Editor
- Compressing and Archiving Files and Directories (tar, gzip)
- Hard Links and the Inode Structure
- Working With Symlinks. Symlinks vs. Hard Links

# Chapter 4. User Accounts Management

- Understanding /etc/passwd and /etc/shadow files
- Understanding Linux Groups (groups, id)
- Creating User Accounts (useradd)
- Changing and Removing User Accounts (usermod, userdel)
- Creating Admin Users
- Group Management (groupadd, groupdel, groupmod)
- User Account Monitoring (whoami, who am i, who, id, w, uptime, last)

# Chapter 5. Linux File Permission

- Understanding File Permissions
- Octal (Numeric) Notation of File Permissions
- Changing File Permissions (chmod)
- Combining Find and Chmod Commands Together
- Changing File Ownership (chown, chgrp)
- Understanding SUID (Set User ID)
- Understanding SGID (Set Group ID)
- Understanding the Sticky Bit
- Umask
- Understanding Files Attributes (lsattr, chattr)

# Chapter 6. Linux Process Management

- Processes and The Linux Security Model
- Listing Processes (ps, pstree)
- Getting a Dynamic Real-Time View of the Running System (top, htop)
- Signals and Killing Processes (kill, pkill, killall, pidof)
- Foreground and Background Processes
- Job Control (jobs, fg, bg)

# Chapter 7. Networking in Linux

- Getting Information about the Network Interfaces (ip, ifconfig)
- Configuring the Network On The Fly (ifconfig, ip, route)
- Setting Up Static IP on Ubuntu (netplan)
- Testing and Troubleshooting Network Connectivity
- Using SSH
- Troubleshooting SSH
- Securing the OpenSSH Server (sshd)
- Copying Files Over the Network (scp)
- Synchronizing Files and Directories using rsync
- Using rsync Over the Network
- Using wget
- Checking for Listening Ports (netstat, ss, lsof, telnet, nmap)

# Chapeter 8. Software Management

- Lesson 1. DPKG (Debian and Ubuntu Based Distros)
- Using APT (Advanced Package Tool)
- Compiling Programs from Source Code vs. Package Manager
- Compiling C Programs
- Compiling Software from Source Code: Lab ProFTPD

# Chapter 9. System Administration

- Task Automation and Scheduling Using Cron (crontab)
- Scheduling Tasks Using Anacron (anacron)
- Mounting and Unmounting File Systems (df, mount, umount, fdisk, gparted)
- Working With Device Files (dd)
- Getting System Hardware Information (lwhw, lscpu, lsusb, lspci, dmidecode, hdparm)
- Service Management (systemd and systemctl)

# Chapter 10. Using AI and Natural Language to Administer Linux Systems (ChatGPT & ShellGPT)

- Installing and Configuring ShellGPT
- Using ShellGPT Like a Pro
- The Chat Feature of ShellGPT

# Chapter 11. Bash Shell Scripting

- Bash Aliases
- Intro to Bash Shell Scripting
- Running Scripts
- Variables in Bash
- Environment Variables
- Getting User Input
- Special Variables and Positional Arguments
- If, Elif and Else Statements
- Testing Conditions For Numbers
- Multiple Conditions and Nested If Statements
- Command Substitution
- Comparing Strings in If Statements
- Lab: Testing Network Connections
- For Loops
- Lab: Dropping a List of IP addresses Using a For Loop
- While Loops
- Case Statement (case)
- Functions in Bash
- Variable Scope in Functions
- Menus in Bash. The Select Statement (select)
- Lab: System Administration Script using Menus

# Chapter 12. Setting Up the Environment for the Hands-On Projects

- Running a Linux Server in the Cloud
- Securing SSH with Key Authentication

# Chapter 13. Project #1 - Running Containerized Applications with Docker

- What is Docker? Why use it. Install it
- The Docker Client
- Pulling Images and Running Containers
- Listing Images and Containers
- Removing Images and Containers
- Getting Shell Access to a Container
- Executing Commands in a Running Container
- Getting Information about the Running Containers
- Committing Container Changes into a New Image
- Tagging and Pushing Custom Images to Docker Hub
- Image Structure and Layers
- Creating Custom Images using Dockerfile
- Persistent Data: Volumes

# Chapter 14. 14. Project #2 - Securing and Hardening a Linux System

- Linux Security Checklist
- Securing the OpenSSH Server (sshd)
- Securing the Boot Loader (Grub)
- Enforcing Password Policy
- Locking or Disabling User Accounts
- Giving Limited root Privileges (sudoers and visudo)
- Setting Users’ Limits (Running a DoS Attack Without root Access)
- Cracking Linux Passwords using John The Ripper
- Checking Files Integrity with AIDE
- Scanning for Rootkits (rkhunter and chkrootkit)
- Scanning for Viruses with ClamAV
- Full Disk Encryption Using dm-crypt and LUKS
- Unlocking LUKS Encrypted Drives With A Keyfile
- Symmetric Encryption Using GnuPG
- Steganography (hide file in plain site)
- Hide Secret Messages Through Steganography with Steghide
- Scanning Networks with Nmap

# Chapter 15. Project #3: Setting Up a Web and DNS Server

- Getting a Domain Name
- Diving into the DNS Protocol and Installing a DNS Server (BIND9)
- Setting Up the Authoritative BIND9 DNS Server
- Installing a Web Server (Apache2)
- Setting Up Virtual Hosting
- Securing Apache with OpenSSL and Digital Certificates
- Access Control by Source IP Address
- The 'Files' Directive
- The .htaccess File
- HTTP Digest Authentication
- The Options Directive and Indexing
- HTTP Compression
- SetHandler and Server Status
- Installing PHP
- Installing and Securing the MySql Serve
- Installing phpMyAdmin
- Securing phpMyAdmin
- Installing a Web Application (WordPress)
- Securing WordPress

# Chapter 16. 16. Project #4 - Automating Linux Administrative Tasks With Ansible

- Intro to Ansible
- Prerequisites
- Ansible Inventory File
- Ansible Ad-Hoc Commands: The Shell Module
- Ansible Ad-Hoc Commands: The Script Module
- Ansible Ad-Hoc Commands: The APT Module
- Ansible Ad-Hoc Commands: The Service Module
- Ansible Ad-Hoc Commands: The User Module
