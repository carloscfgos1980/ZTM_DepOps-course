## Chapter 03. The Linux File System

# Lesson 1. Intro to The Linux Files System

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683153

- check <file system> diagram

In Linuex there is ONLY one file system tree

# Lesson 2. The Filesystem Hierarchy Standard ( FHS)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683175

# Lesson 3. Absolute vs. Relative Paths. Walking through the File System (pwd, cd, tree)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683176

Absolute path starts with: /
command to show the root
ls /

- Go to profile folder:
  cd Home/carlosinfante

or
cd ~

- Print current directory:
  pwd

- To access a file inside the directroy: ./

- To check content of parent directory:
  ls ..

- Install tree so we can see the file system a better graphical way:
  sudo apt install tree

# Lesson 4. The LS Command In Depth (ls)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683180

# Lesson 5. Understanding File Timestamps: atime, mtime, ctime (stat, touch, date)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683182

Commands:
ls /etc/
stat /etc/passwd

- Create a file:
  touch linux.txt

* It is not recommend it to create file with white space but it could be, like this:
  touch "learn linux.txt"

# Lesson 6. Sorting Files by Timestamp

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683183

Command to sort by timestamp
ls -lt

# Lesson 7. File Types in Linux (ls -F, file)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683191

# Lesson 8. Viewing Files - Part 1 (cat)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683193

- Command to view file is "cat" then the path, eg:
  cat /var/log/auth.log

* It can be more than one file, just type the path of the file we want to have access

- To print the number of the lines, eg:
  cat -n /etc/passwd

- "cat" stands for concatenate so it is possobible to put two or more file togethers, this is the example:
  cat /etc/hosts /etc/host.conf > my_host.txt

to check the resulted file that was created:
cat my_host.txt

- While typing I made a typo (my-host) so this is the actual name of the file

# Lesson 9. Viewing Files - Part 2 (less, more)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683195

- You can also read a file with "less" command, eg:
  less /var/log/dmesg

h => help
q => exit the file
arrow key => Move line up or down
scape => forward one window
control + B => move one window backward
g => Go to the beginning of the file
G => Go to the end od the file
/root => This search for the word root in the file. First we need to go to the beginning of the file
n => to move to the next filtered word
N => to move previous filtered word
?kernel => Search for the word kernel backward. First go to the end of the file

# Lesson 10. Viewing Files - Part 3 (tail, head, watch)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683198

- command <tail> show by default the last 10 lines, eg:
  tail /etc/passwd

- we can pass an argument to tail so it will show the amount of line we want

tail -n 2 /etc/group

- Check the last line from a specific line, eg:
  tail -n +20 /var/log/syslog

- Command <head> print the start of the file

# Lesson 11. Creating Files and Directories (touch, mkdir)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683200

- touch examples are already explained in previos lessons

* Create a new directory (folder), eg:
  mkdir dirl

- This is pretty much like working with github

# Lesson 12. Copying Files and Directories (cp)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683202

- Command to copy content into a file, eg:
  cp /etc/passwd ./users.txt

# Lesson 13. Moving and Renaming Files and Directories (mv)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683203

- Command to move file is "mv", eg:
  mv dir1/dir2/b.txt dir1/

* First the command (mv), then the path where the file is (dir1/dir2/b.txt) and the the new path (dir1/)

- Move several files into one directory, ex
  mv c.txt dir1.a.txt dir1.b.txt dir1/dir2/

* The last argument is the destiny directory

- Move all the file with the same format to a different directory, eg:
  mv dir1/dir2/\*.txt dir1/

- To prevent that a file is over written, then is best to use (-i) option, eg:
  mv -i dir1/dir2/b.txt dir1/

  - To rename, "mv" is also use, eg:
    mv dir1/a.txt dir1/abc.txt

# Lesson 14. Removing Files and Directories (rm, shred)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683204

- Remove, eg:
  rm dir1/a.txt

* Remove using "-i" option, for confirmation

- Remove and print the and, we use (-v) option that stands for verbose, eg:
  rm -v dir1/c.txt

- To remove a directory we need (-r option), eg:
  rm -r dir1/dir2/

- To remove protected files, eg
  rm -rf Music/

* f stands for force

# Lesson 15. Working With Pipes in Linux (|, wc)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683205

- "|" is used as pipe, eg to get just the 10 first larges file in <etc> directory:

ls -lSh /etc/ | head

- Get the line 20. Head will get the first 20 and tail just the last on those 20, which is is fact the 20th line:

ls -lSh /etc/ | head -n 20 | tail -n 1

- Check who many times authentication fail (login to the system):

cat -n /var/log/auth.log | grep -a "authentication failure" | wc -l

cat => show the content of a file (auth.log)
-n => format the printed document in lines
grep -a "authentication failure" => criteria search in the document
wc -l => print the amount of matches

- "wc" is command useed to count. It has several options:
  -l => count lines
  -w => count words
  -c => count characteres

* if not option is passed as argument, it will return the 3 elements

# Lesson 16. Command Redirection (>, >>, 2> &>, cut, tee)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683206

- Create a file to save content. the used command is ">". The file is create or overwritten, eg:
  ls -l > l.txt

- If we want to save contant and preserve the previous one, then we use ">>", eg

ls -l ifconfig >> l.txt

- check <piping and comand redirection> diagram

- To redirect an error and print in a file, eg:
  tail -n 3 /etc/shadow/ 2> error.txt
  tail -n 3 /etc/shadow/ 2>> error.txt

* tail -n 3 /etc/shadow/ => is the command that I got the error so I run the command again and redirect to a file in order to save the printed error.

- "tee" command is used to write a file and print it in the terminal, eg:
  ifconfig | grep ether | tee m.txt

- By default "tee" will over write the content, in order to append it, then we need to use [-a] option, eg:
  who | tee -a m.txt

# Lesson 17. Finding Files and Directories - Part 1 (locate, which)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683208

- Install locate:
  sudo apt install mlocate
  sudo updatedb

* I can't find mlocate inside /var/lib/ as the tutorial shows. locate command is working thoug

Usage
locate eahorse

- This will return all the matches, for example all seahorse strings

locate -b 'seahorse'

- This will return only when match the exact word

* Search without case sensitive:
  locate -i Rainshadow

- "which" is used to search for executables, eg:
  which ls

- By default it returns the first match, if we want to check all then we add [-a] option:
  wich -a find

- Search for more than one executable:
  which find pwd ifconfig grep firefox

# Lesson 18. Finding Files and Directories - Part 2 (find)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683219

locate is very useful but it has a several set backs, it does not search in real time but in the database.

USAGE:
find . -name todo.txt

- (.) represents current directory
  [-name] option to look for certain file

[-iname] makes the search case insensitive:
find . -iname todO.txt

- This will match everything that starts with todo:
  find . -name todo\*

- This will find all the matches with this combination of characters:

find . -name \*rep\*

- Find and delete:
  find . -name todo.txt -delete

- Find file based on size:
  sudo find /var/ -type f -size +5M -size -10M

- Find files modified in the last 24 hours
  find /var/ -type f -mtime 0 -ls

- Find files modified between one and two days ago:
  find /var/ -type f -mtime 1 -ls

- Find files were accessed at least 2 days ago:
  find /var/ -type f -atime +1 -ls

- Find files were modified in the last hour:
  find /var/ -type f -mmin -60 -ls

- Find files by user:
  find /var/ -type f -user gdm -ls
- Find the files that does not belong to a group
  sudo find /etc/ -type f -not -group root -ls

# Lesson 19. Find and Exec

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683216

- Find files in the last 24 hours and execute them:
  sudo find /etc/ -type f -mtime 0 -exec cat {} \;

- Find files modified in the last 7 days in directory /etc/ and copy into a backup directory in /root/
  sudo find /etc/ -type f -mtime -7 -exec cp {} /root/backup/ \;

- If I want to run the previos command but first asking if I want to copy a file, one by one, I sustitute [-exec] for [-ok]:
  sudo find /etc/ -type f -mtime -7 -ok cp {} /root/backup/ \;

# Lesson 20. Searching for String Patterns in Text Files (grep)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/49979119

USAGE:
grep user /etc/ssh/ssh_config

- If the string search containg white space:
  grep "command line" /etc/ssh/ssh_config

- Find it without matter lower or upper case:
  grep -i "SSH" /etc/ssh/ssh_config

- Find it without matter lower or upper case [-i] and print the lines[-n]:
  grep -i -n "SSH" /etc/ssh/ssh_config

# Lesson 21. Searching for Strings in Binary Files (strings)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683261

- Check the path:
  which ls

- Check the command. I pipe to [less] so it show less:
  string /usr/bin/ls | less

- Check directly in the machine inside memory:
  ls -l /dev/mem
  strings /dev/mem | less

* There are other options that can be found in man strings

# Lesson 22. Comparing Files (cmp, diff, sha256)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683262

USAGE:

- Here I check the path og the executable ls, then I copy to the current directory and I compare the original executable with the copied one:
  which ls
  cp /usr/bin/ls .
  cmp /usr/bin/ls ./ls

* If nothing return, then they are identical

- Another way yo compare:
  sha256sum /usr/bin/ls ./ls

- Using "diff" command to check how differ two text files
  Fist I create a file (a) from ifconfig, then I run ping command to create some network traffic, then I create another file (b) from ifconfig. finally I compare:
  ifconfig > a
  ping 8.8.8.8
  control + c to abort
  ifconfig > b
  diff a b

- Another example:

Install ssh
sudo apt install ssh

cp /etc/ssh/sshd_ifconfig .

- Edit the copied file (change the port from 22 to 29)

- This will show the different:
  diff /etc/ssh/sshd_ifconfig ./ sshd_ifconfig

- more detailed explanation [-c]:
  diff -c /etc/ssh/sshd_ifconfig ./ sshd_ifconfig

- Display file by file [-y]:
  diff -y /etc/ssh/sshd_ifconfig ./ sshd_ifconfig

# Lesson 23. The Basics of VIM Text Editor

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683263

Install vim in the terminal and the terminator:
sudo apt install vim

- The tutorial video use for the terminal
  sudo dnf install vim but does not work, instead I used the same command for the terminator, maybe the video is outdated

USAGE:

- Open a file:
  vi a.txt

- Exit the file:
  :q!

- Insert: i
- Insert in the beginning of the current line: I
- Append the text after the cursor: a
- Append the text at the end of the current line: A
- Write the text under the current line: o
- Write the text above the current line: O
- Remove under the cursor: r
- return to command mode: pres "esc"
- Get to the last line mode: type ":"
- leaving the file without save the changes: :q!
- Save the file with closing it: :w!
- Save the file and closing it: :wq!
- Same command as boven: shift + zz

# Lesson 24. The VIM Editor In Depth - Part 1

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683264

- Run a shell command from inside <vim>: :! + command (eg:ls)
- Search a string: / + string (eg: ssh)
- Navegate to next match: n
- Navegate to previous match: N
- Searc backward: ? + string (eg: port)
- Find a certain word: bring the cursor over the word and press (\*)
- Replace a string. In the following example all "no" will be sustitute by "XXX":
  :%s/no/XXX/g
- Unmake changes till the last save: :e!
- to undo previos operarion: control + u
- To re do previous operation: control + r
- To cut a line: dd
- To copy before the cursor: p
- To copy after the cursor: P
- to delete 10 lines: 10dd
- Select one character: control + v
- Select whole line: control + V
- Select varios line: control + V + up down arrow
- To copy selected lines: y
- Setting. Show the lines number: :set nu
- Setting. Do not show the lines number: :set nonu
- Syntax highlighting: :syntax on
- Do Syntax highlighting: :syntax off

- Save the configuration in vim:
  vim ~/.vimrc
  set nu
  syntax on
  :wq

# Lesson 25. The VIM Editor In Depth - Part 2

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683265

- To move a certain line 20, eg: :20
- Open file "a" and "b" with vim: vim a b
- To move to the other file: :n
- To move to the previous file: :N
- Open "a" and "b" file in a stack windows: vim -o a b
- Move to the next window: control + w
- Open "a" and "b" file side by side: vim -d a b

* If I leave the document not using the vim command, then I am presented with several option when I try to open it again. To avoid that, delete the .swp file, eg:
  rm .sshd_config.swp

# Lesson 26. Compressing and Archiving Files and Directories (tar, gzip)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683267

- Compressing etc folder into current directory. I must run <tar> command with sudo coz I will be compressing /etc/:
  sudo tar -czvf tar.etc.gz /etc/

[-c] create the compressed file
[-v] verbose: display the process in the terminal
[-z] compression protocol(gzip). Is the most used for Linux
tar.etc.gz => name of the created compressed file. It helps to give a name with .gz so we know what kinda of file is.

- The file can be save in different location:
  sudo tar -czvf /temp/tar.etc.gz /etc/

- Another compression algorithm (bzip2). Use the [j] instead of [z]:
  sudo tar -cjvf /temp/tar.etc.gz /etc/

- Archieve and compress 3 files:
  sudo tar -czvf archievetar.gz /etc/passwd /etc/group /var/log/dmesg

- Archieve and compress but excluding some files in the user's home directory (~):
  sudo tar --exclude='\*.mkv' --exclude='.config' --esclude='.cache' -czvf myhome.tar.gz ~

- Extract the files. Almost the same, just change [c] for [x]. Tis time sudo is not need:
  tar - xzvf etc.tar.gz

* The content is shown in a folder name <etc>. <tar.gz> is not included!

- Extract file to a folder:
  tar - xzvf etc.tar.gz -C my_backup/

- Check if a specific file is in the archive, then pipe the result to grep:
  tar -tf etc.tar.bz2 | grep sshd_config

# Lesson 27. Hard Links and the Inode Structure

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32683268

the way linuz find a file is by a number (hard links). We can visualize by type:
ls -il

- Create a hard link example:
  ln /etc/passwd ./passwd

# Lesson 28. Working With Symlinks. Symlinks vs. Hard Links

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32712364

- Check <Symlinks vs. Hard Link> diagram

- Symlinks file does not share the same number that the original and you can create a Symlinks from a folder while a Hard Links not

- Create a Symlinks example:
  ln -s /etc/passwd ./passwd
