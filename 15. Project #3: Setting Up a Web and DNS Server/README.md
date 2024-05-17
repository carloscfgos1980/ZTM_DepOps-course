## Chapter 15. Project #3: Setting Up a Web and DNS Server

# Lesson 1. Project Overview: The Big Picture

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931622

# Lesson 2. Getting a Domain Name

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931623

- Check domain of websiteÑ
  host google.com

- DNS can be bought at GoDddy or Name Cheap

# Lesson 3. Diving into the DNS Protocol and Installing a DNS Server (BIND9)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931624

log in the vpn. this is a account in Digital Ocean. I didn't create. I won't pay shit.

ssh -l root - p 2666 [ip address of the vpn]

- It is a better to have an alias:
  alias vpn=ssh -l root - p 2666 [ip address of the vpn]

* Install software to connect DNS
  apt update && apt install bind9 bin9utils bin9-doc

- Setting to set IPv4:
  vim /etc/default/named

  OPTIONS="-u bind -4"

- To start bin9
  systemctl reload-or-restart bin9

- Check a Ip addrees from the vpn:
  dig -t a @localhost google.com

- Show main configuration file:
  cat /etc/bind/named.conf

- The name of the software is bin9 but the name of the process is named. To check it:
  ps -ef | grep named

- Edit something for DNS:
  vim /etc/bind/named.conf

* Before closing the semi brazers:
  forwards {
  8.8.8.8;
  8.8.4.4;
  }

- Save the file and reload the server
  systemctl reload-or-restart bin9

- Checking status:
  systemctl status bin9

- Check it is working:
  dig @localhost -t aparrotlinux.org

# Lesson 4. Setting Up the Authoritative BIND9 DNS Server

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931627

- Add a new domain to which the server is authoritative:
  vim /etc/bin/namde.conf.local

* at the end od the file:
  zone "name-of-DNS" {
  type master;
  file "/etc/bin/db.name-of-DNS";
  }

- Create a zone file. I use a empty template that already exist:
  cp /etc/bind/db.empty /etc/bin/db.name-of-DNS

- Open a file for editing:
  vim /etc/bin/db.name-of-DNS

* This configurarion is in the archive file <bin9>

- Check if everything is alright:
  named-checkzone name-of-DNS /etc/bin/db.name-of-DNS zone name-of-DNS/IN loaded serial 1

- Restart bin9
  systemctl restart bin9

- Check is everything is set:
  dig @localhost -t ns name-of-DNS

# Lesson 5. Installing a Web Server (Apache2)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931628

Install apache in the vpn
apt update && apt install apache2

- Check if the firewall is active:
  ufw status

* If it is "inactive", we don't need to do anything, if is "active", then:
  ufw allow "Apache Full"

# Lesson 6. Setting Up Virtual Hosting

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931629

# Lesson 7. Securing Apache with OpenSSL and Digital Certificates

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931636

# Lesson 8. Access Control by Source IP Address

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931644

# Lesson 9. The 'Files' Directive

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931645

# Lesson 10. The .htaccess File

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931646

# Lesson 11. HTTP Digest Authentication

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931648

# Lesson 12. The Options Directive and Indexing

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931650

# Lesson 13. HTTP Compression

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931651

# Lesson 14. SetHandler and Server Status

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931653

# Lesson 15. Installing PHP

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931654

# Lesson 16. Installing and Securing the MySql Serve

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931655

# Lesson 17. Installing phpMyAdmin

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931659

# Lesson 18. Securing phpMyAdmin

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931660

# Lesson 19. Installing a Web Application (WordPress)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931721

# Lesson 20. Securing WordPress

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32931722

# conclusion:

I don't like this system administration. Also this guy is talking about Apache and worldpress. I haven't learned any of those stuff!
