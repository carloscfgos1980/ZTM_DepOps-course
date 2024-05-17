## Chapter 09. System Administration

# Lesson 1. Task Automation and Scheduling Using Cron (crontab)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32860187

# Lesson 2. Scheduling Tasks Using Anacron (anacron)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32860188

- <Anacron> is just like <Cron> but it is design for system that are not running continously, like laptops

- Edit ancaron:
  vim /etc/anacrontab

# Lesson 3. Mounting and Unmounting File Systems (df, mount, umount, fdisk, gparted)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32860189

- mount means to add usb device

# Lesson 4. Working With Device Files (dd)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32860191

# Lesson 5. Getting System Hardware Information (lwhw, lscpu, lsusb, lspci, dmidecode, hdparm)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32860192

- Hardware info:
  lshw

- Hardware info in json format:
  lshw -json | less

- Hardware info in html format and redirect it to a file:
  lshw -html > hw.html

* I can open the file just by double click it.

-Info about the Central Process Unit (CPU)
lscpu

- Info about the hard disk:
  lshw -C disk

# Lesson 6. Intro to systemd

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32860193

# Lesson 7. Service Management (systemd and systemctl)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32860194
