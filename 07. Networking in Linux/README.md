## Chapter 07. Networking in Linux

# Lesson 1. Getting Information about the Network Interfaces (ip, ifconfig)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/49979117

- It can be used by 2 commands:
  ifconfig
  ip address show

- Check internet connection:
  if config enp0s3
  ip s a dev enp0s3

- Check DNS servers:
  resolvectl status

# Lesson 2. Configuring the Network On The Fly (ifconfig, ip, route)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32731040

- Become root:
  sudo su

* There are 2 ways to achieve this process (ifconfig, ip)

- Disconnet internet:
  ifconfig enp0s3 down
  ip link set enp0s3 down

- Reconnect internet:
  ifconfig enp0s3 up
  ip link set enp0s3 up

- Check internet status:
  ifconfig -a
  ip link show dev enp0s3

- Configure ip address:
  ifconfig enp0s3 192.168.0.111/24 up

ip address del 192.168.0.111/24 dev enp0s3
ip address add 192.168.0.222/24 dev enp0s3

- Configure Gate Away:
  route del default gw 192.168.178.1
  route add default gw 192.168.178.2

  ip route del default
  ip route del default via 192.168.178.1

- Change MAC address:
  ifconfig enp0s3 down
  ifconfig enp0s3 hw ether 08:00:27:51:05:09
  ifconfig enp0s3 up

ip link set dev enp0s3 address 08:00:27:51:05:05

- Check:
  ip link show enp0s3

# Lesson 3. Setting Up Static IP on Ubuntu (netplan)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32731041

- This is to change ip address and keep the changes. The earlier lesson shows how to do it but the changes will go away after rebooting the computer.

- Explanation of how to set up Static IP. I didn't . I just kep the automatic option

- Network interface can be managed by Network Manager or Networkd but not by both of them at the same time. So in order to do this process we need to stop Network Manager:

  sudo su
  systemctl stop NetworkManager
  systemctl disable NetworkManager
  systemctl status NetworkManager
  vim /etc/netplan/01-netconfig.yaml

* Copy some lines inside the file:
  network:
  version: 2
  rendered: networkd
  ethernets:
  enp0s3:
  dhcp4: false
  address: - 192.168.0.20/24
  gateway4: "192.168.0.1"
  nameservers:
  address: - "8.8.8.8" - "8.8.4.4"

* Check for examples:
  https://github.com/canonical/netplan/tree/main/examples

- Save the changes:
  netplan apply

# Lesson 4. Testing and Troubleshooting Network Connectivity

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/49979113

Check if a website works:
ping google.com

- Stop: control + c

- Check Troubleshooting Network Connectivity:
  route -n
  ping 192.168.178.1

* route -n shows me the default gateway (192.168.178.1).

# Lesson 5. Using SSH

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32731044

SSH => Secure Shell. Protocol used for secure Remote Management

- Install openssh in terminator (Ubuntu):
  sudo apt update && apt install openssh-server openssh-client

- Install openssh in terminal (CentOS):
  sudo apt install openssh-server openssh-client

- Check that sshd is running:
  systemctl status sshd (CentOs)
  systemctl status ssh (Ubuntu)

- Connect as a client:
  ifconfig(Ubuntu)
  ping 192.168.178.2 (that is the IP address that I get after running ifconfig)
  ssh carlosinfante@192.168.178.2
  - it prom a confirm question: type "yes"
    Voila. It is connected. To disconnect: "exit"

# Lesson 6. Troubleshooting SSH

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32731047

- Check if ssh is runnig:
  systemctl status ssh

- Check the log files for errors:
  sudo tail -f /var/log/auth.log

# Lesson 7. Securing the OpenSSH Server (sshd)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32731049

- Location of sshd
  ls -l /etc/ssh/

ssh_config => Configuration of the client
sshd_config => Configuration of the daemon

1. Open sshd_config
   sudo vim /etc/ssh/sshd_config

- Each lines that starts with "#" is a comment

To understand more about sshd_config, open the manual:
man sshd_config

- Search for something, eg: allow: /allow

2. Change the default port for a radom one.

- I need to edit the file so I press: i
- Un comment the port and change it

3. Set PermitRootLogin to "no"

4. ClientAliveInterval 300

5. ClientAliveCountMax 0

# Lesson 8. Copying Files Over the Network (scp)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32731051

1. Check if the sshd connection:

- terminator: ifconfig to check ip address (inet)
- Open terminal (CentOs): ssh carlosinfante@192.178.168.72

2. Create a file in CentOs:
   ip add show > ip.txt

3. Copy the file (CentOs) to the home directory in the Client (Ubuntu) with same name:
   scp -P 22 ip.txt carlosinfante@192.178.168.72:~

4. Copy the file (CentOs) to the home directory in the Client (Ubuntu) with different name:
   scp -P 22 ip.txt carlosinfante@192.178.168.72:~/ip_centos.txt

5. Check the file is copied (Ubuntu):
   ls
   cat ip.txt
   cat ip_centos.txt

6. Copy a directory

- Create a directory in CentOs and move the file ip.txt into this directory:
  mkdir mydir1
  mv ip.txt mydir1/
- Copy the directory:
  scp -r -P 22 mydir1/ carlosinfante@192.178.168.72:~

# Lesson 9. Synchronizing Files and Directories using rsync

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32731052

- <rsync> is like an improve copy (cp) command

1. Copy directory
   sudo rsync -av /etc/ ~/etc-backup/

[-a] runs in archieve mode. It will copy directories recursively, preserves symlinks, the owner and the permissions. It will copy the files as they are
[-v] verbose mode

- If I run the command again, it won't do anything since the files are the same. This is better than <cp> which it will copy the files again. If a file is change it. It will locate that file and just copy that one

2. Mirrow the directories in case that a file has been deleted:
   sudo rsync -av --delete /etc/ ~/etc-backup/

3. Copy directory and exclude files. This will copy directory "my_project" into "backup":

- Create a file (exclude_files) with the name of the files I want to exclude
- Edit the vile with "vim" and include the files, eg:
  movie1.mkv
  dir1/
  \*.png
- Write the command:
  rsync -av --exclude-from='exclude_files.txt' my_project/ backup/

4. Copy directory and exclude specific type of files. This will copy directory "my_project" into "backup":

rsync -av --exclude='\*.png' --exclude='\*.pdf' my_project/ backup/

# Lesson 10. Using rsync Over the Network

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32731053

- It is very similar to scp. Moving etc directory from CentOs to Ubuntu:
  sudo rsync -av -e ssh /etc/ carlosinfante@192.178.168.72:~/etc-centos/

# Lesson 11. Using wget

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32731054

This is used to download files. It is very simple, just wget and the website address

1. Download it in current directory
   wget https://www.google.com

2. Download it to google directory I created:
   wget -P google/ https://www.google.com

3. Download it to google directory I created and limit the rate (default is 200k)
   wget --limit-rate=100k -P google/ https://www.google.com

4. Resume the download:
   wget -c -P google/ https://www.google.com

5. Download several websites:

- Create a vim file (image.txt) with the URLs of the websites
- Download command:
  wget -i images.txt

6. Download a large file in the background, normally .iso files:
   wget -b -P google/ https://www.google.com.iso

- If I want to check the status of the download:
  tail -f wget.log

7. Continue download even if the terminal is shot down:
   nohup wget -b -P google/ https://www.google.com.iso

# Lesson 12. Checking for Listening Ports (netstat, ss, lsof, telnet, nmap)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32731055

- Listening Ports:
  sudo netstat -tupan
  [-t] TCP ports
  [-u] UDP ports
  [-p] Process Id and the name of the program that is listenning
  [-a] shows both ports, listenning and not listenning
  [-n] numerical address instead of trying symbolic hosts and ports names

- Check if 22 port is listenning:
  sudo netstat -tupan | grep :22

- <ss> is almost the same as <netstat>
  ss -tupan

- List of any open file in the system:
  lsof

- Check open file of a specific user
  lsof -u carlosinfante

- <telnet> is use to check if the port of a different user is open, eg:
  telnet 192.168.0.113 22

- Use <nmap>. It is a pro port scanner:
  sudo apt install nmap
  sudo nmap 192.168.0.113

- We can check if specific port is open:
  nmap -p 80 linux.com
