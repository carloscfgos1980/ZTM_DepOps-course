## Chapter 04. User Accounts Management

# Lesson 1. Understanding /etc/passwd and /etc/shadow files

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32715342

USAGE

- List the files:
  ls -l /etc/passwd /etc/shadow
- Check the content in passwd:
  less /etc/passwd

<passwd> shows the user that has logged in, eg:
carlosinfante:x:1000:1000: CarlosInfante,,,:/home/carlosinfante:/bin/bash

- Explanation of above string. the elements are separated by ":" :
  carlosinfante => users's login name
  x => means that the password was assigned but in other file: shadow. If this field is blank, the used does not need to enter a password in order to log in
  1000 => user id. A possitive integer number
  1000 => group id
  CarlosInfante,,, => it is a comment, sometimes it is left blank
  /home/carlosinfante => user's home directory
  /bin/bash => defult shell, usually set to

<shadow> contains the passwords:
sudo less /etc/shadow

- Find full description of each field in <shadow>
  man shadow

* password string contains two fields:

  - user's loging name
  - encrypcted passwrod: $y is the encrypted method, it could be others.

* This password are using a has method and a salt, that make every encypted password unique, even when they could be potianlly the same raw password

# Lesson 2. Understanding Linux Groups (groups, id)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32715343

USAGE
groups

- It will print out all the groups that the current user belogs to

* To check user group's ids:
  id

# Lesson 3. Creating User Accounts (useradd)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32715344

- Create aa user (u1):
  sudo useradd u1

create a password for u1:
sudo passwd u1

- then type the selected password twice

# Lesson 4. Changing and Removing User Accounts (usermod, userdel)

- Change the user comment:
  sudo usermod -c "C++ DEveloper" james

- Change primary group:
  sudo usermod -g daemon james

- Delete user:
  sudo userdel u1

# Lesson 5. Creating Admin Users

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32715348

USAGE:

- Create a new user (toor)
  sudo useradd -m -s toor

- Give admon permission
  sudo usermod -aG sudo toor

# Lesson 6. Group Management (groupadd, groupdel, groupmod)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32715349

- Creating a group (engineering)
  sudo groupadd engineering

- Create a user
  sudo useradd u1

- Create another user (u2) attached to "engineering" group:
  sudo useradd -aG engineering u2
  [-a] is to anex the existing groups of this user, otherwise they will be deleted
  [-G] assign a group

- Assign a user (u1) to a group
  sudo usermod -aG engineering u1

- Change group's name:
  sudo groupmod -aG engineers engineering

* first option is the new name (engineers) and second one is the current name (engineering). If the group does not exist, we get an error message

# Lesson 7. User Account Monitoring (whoami, who am i, who, id, w, uptime, last)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32715351

Create link between two shells
terminator:
sudo apt install openssh-server

- Check if it is correctly installed:
  sudo systemctl status ssh

- Check connection:
  ifconfig

- Connection setting: bridge adapter

Stablish connection. terminal:
ssh carlosinfante@127.0.0.1

- terminator:
  who -H

* This will show two connections and the details
