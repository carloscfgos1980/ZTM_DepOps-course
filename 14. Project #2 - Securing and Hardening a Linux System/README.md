## Chapter 14. Project #2 - Securing and Hardening a Linux System

# Lesson 1. Project Overview

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892385

# Lesson 2. Linux Security Checklist

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892386

- Check <security_checklist1> diagram
- Check <security_checklist2> diagram
- Check <security_checklist3> diagram

# Lesson 3. Securing the OpenSSH Server (sshd)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892388

- Edit sshd_config
  sudo vim /etc/ssh/sshd_config

1. Change the default port. I need to uncomment the line and change to a ramdom port (6222).
2. Disable direct root login

- All this steps I have already done!

# Lesson 4. Securing the Boot Loader (Grub)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892389

- Check <secure boot loader> diagram

- Open the file to set tue boot encrypted password:
  sudo vim /etc/grub.d/40_custom

- Create encripted password:
  grub-mkpasswd-pbkdf2

- Edit the file:

set superusers= root
password_pbkdf2 root [encripted password]

# Lesson 5. Enforcing Password Policy

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892390

- Enforce password for new user to be at least 10 characters:

1. Opem the file:
   sudo vim /etc/login.defs
2. Edit the file( add the text):
   PASS_MIN_LEN 10

- Create a new user and provide a password with max age of 90 days:

1. Open a differente terminal;
2. Create the user:
   sudo useradd -m -d /home/tux -s bin/hash tux

3. password for tux user:
   sudo passwd tux

user: tux
pass: tuxedo2024

4. Chage the age of the password:
   sudo chage -M 90 tux

5. Check tux password setting:
   sudo chage -l tux

- Install packate to enforce pgood quality passwords:
  sudo apt install libpam-pwquality

- Edit the file tat containts password requirements:
  sudo vim /etc/pam.d/common-password:

Edti the file and save it:
pam_quality.so retry=3 minlen=8 difok=3 ucredit=-1 lcredit=-1 dcredit=-1 ocredit=-1

[retry=3] will prompt the user 3 times before exiting and returnning an error
[minlen=8] specify that the password can not be less than 8 characters
[difok=3]only 3 changes in the new password can be present in the old password
[ucredit=-1] requires at least 1 uppercase character
[lcredit=-1] requires at least 1 lowercase character
[dcredit=-1] requires at least 1 numeric character
[ocredit=-1] requires at least 1 special character

- Change the passwrod for tux user
  sudo tux
  passwd

- Introduce current password: tuxedo2024
- Check if the requirements work by typing passwords that do not match the requirements. It works!
- Type new password: BobMarley\*1981

# Lesson 6. Locking or Disabling User Accounts

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892392

- Lock user tux password
  sudo passwd -l tux

- Check that the password is locked:
  sudo cat /etc/shadow

* This will show (!) infront of that hashed passwod for user tux

- Other way to check locked password:
  sudo passwd status tux

* If it shows L, the is locked, NP means no password, P means valid password

- Unlock the password
  sudo passwd -u tux

- Complete disable an account:
  sudo usermod --expiredate 1 tux

- Re enable an account or set ton never expiration date:
  sudo usermod --expiredate "" tux

# Lesson 7. Giving Limited root Privileges (sudoers and visudo) - Part 1

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892393

# Lesson 8. Giving Limited root Privileges (sudoers and visudo) - Part 2

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892394

- Visudo command (it is a text editor but check that the lines are written correctly):
  sudo visudo

- Create a new user (dah). In a different terminal

- Inside <visudo> I add the commands (ls and cat) that I want dan to be able to run as root:
  dan ALL=(root) /ust/bin/ls,urs/bin/cat

- Add the pivilage to dan user of update with requiring the password. this is done in visudo:
  dan ALL=(root) NOPASSWD:/usr/bin/apt

- Inside <visudo> I add the commands (ls and cat) that I want dan to be able to run as root and prompt for password:
  dan ALL=(root) PASSWD:/ust/bin/ls,urs/bin/cat

- Using alis to define user and privileges:
  \# User alias specification
  User_Alias MYADMIN=dan,john

\# Cmnd alias specification
Cmnd_Alias FILE=/usr/bin/cp,/usr/bin/ls,/usr/bin/touch,/usr/bin/rm

\# User privilege specification
MYADMIN ALL=(root) /usr/bin/netstat, FILE

# Lesson 9. Setting Users’ Limits (Running a DoS Attack Without root Access)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892395

- this shows an example of that blocks ubuntu system by running a very simple script.
- To solve this issue, we should do the folllow:
  sudo vim /etc/security/limits.conf

- Add this sript at the end of the file:
  carlosinfante hard nproc 2000

# Lesson 10. Intro to Cracking Passwords

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892396

Website to check if some has try to crack your email address:
https://haveibeenpwned.com

# Lesson 11. Cracking Linux Passwords using John The Ripper

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/49979112

- Use the app john the ripper. I already installed but it didn't work. Moving forward!

# Lesson 12. Checking Files Integrity with AIDE - Part 1

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892398

This shit is not working!

# Lesson 13. Checking Files Integrity with AIDE - Part 2

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892399

# Lesson 14. Scanning for Rootkits (rkhunter and chkrootkit)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892400

- <Rootkits> are script that compromise the integrity of the system
- <rkhunter> is a app to check system for cracking

# Lesson 14. Scanning for Viruses with ClamAV

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892402

- Linus is knowly virus free. Anyway if we are running a email server, malitious softwares can be upload it from a window system and infect other window systems. ClamAV is the most used for this porpused.

# Lesson 15. Full Disk Encryption Using dm-crypt and LUKS

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892403

# Lesson 16. Unlocking LUKS Encrypted Drives With A Keyfile

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892405

# Lesson 17. Symmetric Encryption Using GnuPG

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892406

# Lesson 18. Steganography Explained

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892407

- <Steganography> is the art of hide secret info in plain site

# Lesson 19. Steganography In Depth

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892408

# Lesson 20. Hide Secret Messages Through Steganography with Steghide

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892410

# Lesson 21. Scanning Networks with Nmap

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892411

- Get ip address in mac:
  ipconfig getifaddr en0

- Use nmpa from VM ubuntu in my Mac
  nmap 192.168.178.60

# Lesson 22.Nmap Advanced

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32892416
