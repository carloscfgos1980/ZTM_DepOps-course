## 05. Linux File Permissions

# Lesson 1. Understanding File Permissions

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32727481

There are 3 file permissions:

- Read permissin (r)
- Write permissin (w)
- execute permissin (x)

USAGE:
ls -l /etc/passwd

- this show something like this:
  -rw-r--r-- 1 root root 3107 apr 29 06:28 /etc/passwd

rw- => Shows owner permission
r-- => Shows owner permission
r-- => Everybody else permissions

# Lesson 2. Octal (Numeric) Notation of File Permissions

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32727484

write = 4
read = 2
execute = 1

Example
-rw- => 4 + 2 + 0 = 6
-rwx => 4 +2 + 1 = 7
-r-- => 4 + 0 + 0

-rw-rw-r-- => 4+2+0, 4+2+0, 4+0+0 = 664

# Lesson 3. Changing File Permissions (chmod)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32727485

USAGE

- Create a txt frpm who command
  who > user.txt
- Show file's permissions:
  ls -l user.txt
- Remove user write privilige:
  chmod u-w user.txt
- Give the user all rights:
  chmod u+rwx user.txt
- Editing permission for the user, add write permission to the group and removing all the permission for others:
  chmod u-w,g+w,o-rwx user.txt

- Edit permission using "=". Setting user and owner to write and read and others no permissions:
  chmod ug=wr,o= user.txt

- Editing using numbers. User = write and read, group = read, other = read
  chmod 644 user.txt

# Lesson 4. The Effect of Permissions on Directories

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32727486

- The directory needs the execute (x) permission so we can have full access ot it!
- The permission of the parent directory has more importance that the permission of the file

# Lesson 5. Combining Find and Chmod Commands Together

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32727488

- Change all the files in Home directory to user= write and read, group = read, others = no write
  find ~ -type f -exec chmod 640 {} \;

- Change all the directories in Home directory to user= write, read and execute, group = read and execute, others = no write
  find ~ -type d -exec chmod 750 {} \;

# Lesson 6. Changing File Ownership (chown, chgrp)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32727489

lscpu => Shows all the metadata from my cpu

- Copy this data to a file:
  lscpu > cpu.txt
- Change the owner of the file:
  sudo chown toor cpu.txt

* toor is a user I created in previous lesson

- Change the group of the file:
  sudo chgrp sudo cpu.txt

# Lesson 7. Understanding SUID (Set User ID)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32727490

SUID gives priviliges to commands to run as root, for example passwd which allows to have access to /etc/shadow where the passwords are storage

# Lesson 8. Understanding SGID (Set Group ID)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32727491

- It is very similar like the previous one, in this case for directories

# Lesson 9. Understanding the Sticky Bit

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32727492

- Applied to a folder so the files in a shared directory can not be deleted by other users

# Lesson 10. Umask

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32727493

Default umask is 0002. This number is rested from the default file and directory and that is why they are always created with the same set of privilages. Not really usefull, just a deep dive

# Lesson 11. Understanding Files Attributes (lsattr, chattr)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32727494

This features are not very common to be used. It is to set directories with certain attributes in order to protect them from changes
