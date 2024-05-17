## Chapter 11. Bash Shell Scripting

# Lesson 1. Bash Aliases

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868794

- alias are shortcuts for commands.
- Create an alias, eg:
  alias update="sudo apt update && sudo apt dist-update && sudo apt clean"

- To preserve the alias:

1. Open the .bashrc file in home directory
   vim ~/.bashrc

2. write the new alias and save the file.

# Lesson 2. Intro to Bash Shell Scripting

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868797

- shell script is a executable shell command that contains very specific structure and components like variable, options, functions, loops and so on

1. Create a file (firts_script.sh)
   vim firts_script.sh
2. write the commands inside this file
   mkdir -p dir1
   echo "some text" > dir1/file.txt
   ls -l
   cat dir1/file.txt

3. Make the file an executable:
   chmod 700 firts_script.sh

4. Run the commands (if the file is contain in this directory):
   ./firts_script.sh

# Lesson 3. Running Scripts

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868799

- We can run a file by calling the program (bash, python, etc). In this case I don't need the permission to execute
  bash firts_script.sh

# Lesson 4. Variables in Bash

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868800

- Variable can not start with a number and special characters are not allowed (.,@)

- Create a variable, eg:
  myAge=44
  os=Linux

- Check a variable, eg:
  echo $myAge

- Use a variable inside a string. The name of the variable is not substitue if we use single quotes ('):
  echo "I'm learning $os at $myAge years old"

* In this case the variable will be included, it is just like using "`" in javascript, the result of the string above will be:

I'm learning Linux at 44 years old

- If we want to cancel a special character, we use (\)

- Run the list of variables. There are many so it is better to pipe (less, grep) the response:
  set | grep myAge

- erase a variable:
  unset myAge

- Variables by the OS or Shell itself, are usually in capital letters, eg:
  echo $PATH
  echo $USER
  echo $HOME
  echo $HISTFILE

- Declare a variable that can not be changed (read only), EG:
  declare -r logdir="/var/log"

- Run a file with scrips and variables:

1. Create the file:
   vim file_stat.sh

2. Give execute rights:
   chmod +x file_stat.sh

3. Write the script into file_stat.sh and save it:
   #!/bin/bash
   filename="/etc/passwd"
   echo "number of lines"
   wc -l $file_stat.sh

echo "############"
echo "First 5 lines:"
head -n 5 $file_stat.sh

echo "############"
echo "Last 7 lines:"
tail -n 7 $file_stat.sh

4. Run the script:
   ./file_stat.sh

# Lesson 5. Environment Variables

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868801

- There are 2 types of variables:

1. _environment variables_: Defined by the current shell or inherit by any child shell or process. Displayed with: env
2. _shell variables_ are contained in the shell they are defined or set

- There are many variables so it is better to pipe it (less. grep)

- Add an environmet variable permanently:

1. Open the file that contains the variables:
   vim ~/.bashrc
2. Write the variable at the end of the file, eg:
   export PATH=$PATH:~/script
3. Save the file
4. Load it in the current shell:
   source ~/.bashrc

# Lesson 6. Getting User Input

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868804

# Lesson 7. Special Variables and Positional Arguments

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868807

# Lesson 8. If, Elif and Else Statements

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868808

Example:

1. Create a folder for the scripts projects (projects_script) and move to this folder
2. Create a file for the scripts (display.sh)
3. Open a second terminal so we can edit the file and runnit without exit the file
4. Write the code:
   #!/bin/bash
   if [ -f "$1" ]
   then
   echo "The argument is a file, displaying its contents ..."
   sleep 1
   cat $1
   elif [ -d "$1" ]
   then
   echo "The argument is a directory, running ls -l ..."
   sleep 1
   ls -l $1
   else
   echo "The argument ($1) is neither a file nor a directory."
   fi

# Lesson 9. Testing Conditions For Numbers

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868810

Example:

#!/bin/bash
read -p "Enter your age: " age

if [[$age -lt 18]]
then
echo "You are minor!"
elif [[$age -eq 18]]
then
echo "Congratulations, you've just become major!"
else
echo "You are major!"
fi

- read -p "Enter your age: " age will promp a cuestion while execute age.sh

- To check available test: man test

INTEGER1 -eg INTEGER2
INTEGER1 is equal to INTEGER2

INTEGER1 -ge INTEGER2
INTEGER1 is greater or equal than INTEGER2

INTEGER1 -gt INTEGER2
INTEGER1 is greater than INTEGER2

INTEGER1 -le INTEGER2
INTEGER1 is less or equal than INTEGER2

INTEGER1 -lt INTEGER2
INTEGER1 is less than INTEGER2

# Lesson 10. Multiple Conditions and Nested If Statements

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868811

Example 1. Multiple Conditions:

- We add some condictions: Check that the person is a menor and that the major age is a real one (age > 18 && age < 100 ):

#!/bin/bash
read -p "Enter your age: " age

if [[$age -lt 18]] && [[$age -ge 0]]
then
echo "You are minor!"
elif [[$age -eq 18]]
then
echo "Congratulations, you've just become major!"
elif [[$age -gt 18]] && [[$age -le 100]]
then
echo "You are major!"
else
echo "Invalid age!"
fi

Example 2. Nested If Statements:

#!/bin/bash
if [[$# -eg 1]]
then

if [ -f "$1" ]
then
echo "The argument is a file, displaying its contents ..."
sleep 1
cat $1
elif [ -d "$1" ]
then
echo "The argument is a directory, running ls -l ..."
sleep 1
ls -l $1
else
echo "The argument ($1) is neither a file nor a directory."
fi

else
echo "The script should be run with an argument"
fi

1. Select Shift + v
2. Define selection with arrow keys
3. Index: >

# Lesson 11. Command Substitution

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868812

There are 2 ways to do it:
now=`date`
now="$(date)"

# Lesson 12. Comparing Strings in If Statements

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868815

Example 1:

#!/bin/bash
read -p "String1: " str1
read -p "String2: " str2

- if with single square brackets and single =

if [ "$str1" = "$str2" ]

then
echo "The strings are equal."
else
echo "The strings are NOT equal."
fi

- if with double square brackets and ==

if [[$str1 == $str2]]
then
echo "The strings are equal."
else
echo "The strings are not equal."
fi

if [["$str1" != "$str2"]];then  
 echo "The strings are not equal."
fi

Example 2. Check substring:

#!/bin/bash

str1="Nowadays, Linux powers the servers of the Internet."
if [[“$str1” == *"Linux"*]]
then
echo "The substring Linux is there."
else
echo "The substring Linux IS NOT there"
fi

Example 3. Check strings length
my_str="abc"
if [[-z "$my_str"]]
then
echo "String is zero length."
else
echo "String IS NOT zero length."
fi

if [[-n "$my_str"]]
then
echo "String IS NOT zero length"
else
echo "String is zero length"
fi

# Lesson 13. Lab: Testing Network Connections

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868816

Example:
#!/bin/bash
output="$(ping -c 3 $1)" 
#echo "$output"

if [[$output == *"100% packet loss"*]]
then
echo "The network connection to $1 is not working."
else
echo "The network connection to $1 is working"
fi

ping -c 3 => command to check connection

100% packet loss => substring showed when there is not connection

# Lesson 14. For Loops

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868817

#!/bin/bash

- iterating over a list of strings
  for os in Ubuntu CentOs Slackware "Kali Linux"
  do
  echo "os is $os"
  done

- iterating over a list of numbers

for num in {3..7}
do  
 echo "num is $num"
done

- interating over a list of numbers in increments
  for x in {10..100..5}
  do
  echo $x
  done

- iterating over a list of files
  for item in ./\*
  do
  if [[-f $item]]
  then
  echo "Displaying the contents of $item"
  sleep 1
  cat $item
  echo "#######################"
  fi
  done

- ./\* # files in the current dir

- C/Java style. It not very common
  for ((i = 0 ; i <= 50 ; i++))
  do
  echo "i = $i"
  done

# Lesson 15. Lab: Dropping a List of IP addresses Using a For Loop

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868819

Example 1:
#!/bin/bash

DROPPED_IPS="8.8.8.8 1.1.1.1 10.10.11.1"

for ip in $DROPPED_IPS
do
echo "Dropping packets from $ip"
iptables -I INPUT -s $ip -j DROP
done

- IPs to drop (whitespace separated list)
- iterating over the list dropping ip after ip

Example 2:

1. Create file with ip address and write the ip address in separate lines:
   vim ips.txt
2. Create the execute file (lab.dropping_ips.sh):
   vim lab.dropping_ips.sh
3. made executable
   chmod +x lab.dropping_ips.sh

4. Write the code

for ip in $(cat ips.txt)
do
echo "Dropping packets from $ip"
iptables -I INPUT -s $ip -j DROP
done

# Lesson 16. While Loops

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868821

Example:
i=0
while [[$i -lt 10]]
do
echo "i: $i"
((i++)) # same as: let i=i+1
done

# Lesson 17. Case Statement

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868822

- Case is like using <switch> in javascript

- Example 1. Checking favorite pet. Code source in bash_case:

  #!/bin/bash
  echo -n "Enter your favorite pet:"
  read PET

case "$PET" in
dog)
echo "Your favorite pet is the dog."
;;
cat | Cat)
echo "You like cats."
;;  
 fish | "African Turtle")
echo "Fishes or turtles are great!"
;;  
 \*)
echo "Your favorite pet is unknown!"
esac

- This will promp the question in the same line:
  echo -n "Enter your favorite pet:"
  read PET

Example 2. Sending a signal( kill a process). Codde source: bash_case_signal:

#!/bin/bash
if [ $# -ne 2 ]  
then
echo "Run the script with 2 arguments: SIGNAL and PID."
exit
fi

case "$1" in

1.  echo "Sending the SIGHUP signal to $2"
    kill -SIGHUP $2
    ;;
2.  echo "Sending the SIGINT signal to $2"
    kill -SIGINT $2
    ;;
3.  echo "Sending the SIGTERM signal to $2"
    kill -15 $2
    ;;
    \*) echo "Signal number $1 will not be delivered."
    ;;
    esac

- In a different termial run this commands:
  sleep 1001 &
  pgrep sleep

Then run the script(case_signal) with the <case> optionn as first argument and the PID(process Id) as second argument. pgrep sleep is used to get the PID. EX:

./case_signal 1 5064

# Lesson 18. Functions in Bash

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868823

Example 1. Simple function. Code source: bash_functions:

#!/bin/bash

- defining a function: method 1
  function print_something () { .
  echo "I'm a simple function!"
  }

- defining a function: method 2
  display_something () {
  echo "Hello functions!"
  }
- either of the above methods of specifying a function is valid.

- calling the functions
  print_something
  display_something

- To call the function, just ruun the script:
  ./functions.sh

Example 2. Functions with arguments. Source code: bash_function_arguments.sh

#!/bin/bash
create_files () {
echo "Creating $1"
touch $1
chmod 400 $1

    echo "Creating $2"
    touch $2
    chmod 600 $2

}

- calling the function with 2 args

create_files aa.txt bb.txt

- function that returns a valus (output of a command)

function lines_in_file() {
grep -c "$1" "$2"
}

n=$(lines_in_file "usb" "/var/log/dmesg")
echo $n

- This function will check hoy many times is the word "usb" in "/var/log/dmesg"

# Lesson 19. Variable Scope in Functions

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868826

- It is good practice to declare local variable inside the function to contain the value. Variables in bash are global, eg:
  local var = "YY"

# Lesson 20. Menus in Bash. The Select Statement

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868827

- Example. Combination of <if statement> and <case statement>. This script loop thru a list of countries and depending the country, display a message with the local language, option 5 is to quite the loop.

#!/bin/bash

PS3="Choose your country:"
select COUNTRY in Germany France USA "United Kingdom" Quit
do
case $REPLY in 1)
echo "You speak German."
;; 2)
echo "You speak French."
;; 3)
echo "You speak American English."
;; 4)
echo "You speak British English."
;; 5)
echo "Quitting ..."
sleep 1
break
;;
\*)
echo "Invalid option $REPLY"
;;
esac
done

PS3="Choose your country:" => is used to personalise the promp question, other wise it will be shown as #?

# Lesson 21. Lab: System Administration Script using Menus

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32868856

- Loop thru a list of system adminitration tasks. The fist one is the most complicated one coz is a <indexed if statement> to check if the user already exist and to check if the process was successful. Source code: bash_lab_menus.sh

#!/bin/bash
PS3="Your choice: "
select ITEM in "Add User" "List All Processes" "Kill Process" "Install Program" "Quit"
do
if [[$REPLY -eq 1]]
then
read -p "Enter the username:" username
output="$(grep -w $username /etc/passwd)" 
                if [[ -n "$output" ]]
then
echo "The username already exists."
else  
 sudo useradd -m -s /bin/bash "$username"
if [[$? -eq 0]]
then
echo "The user $username was added successfully."
tail -n 1 /etc/passwd
else
echo "There was an error adding the user."
fi
fi
elif [[$REPLY -eq 2]]
then
echo "Listing all processes..."
sleep 1
ps -ef
elif [[$REPLY -eq 3]]
then
read -p "Enter the process to kill: " process
pkill $process
elif [[$REPLY -eq 4]]
then
read -p "Enter the program to install: " app
sudo apt update && sudo apt install $app
elif [[$REPLY -eq 5]]
then
echo "Quitting ..."
sleep 1
exit
else
echo "Invalid Menu selection."
fi
done

- This check is the user already exist:

                output="$(grep -w $username /etc/passwd)"
                if [[ -n "$output" ]]

- This check if the user was added successfully:
  sudo useradd -m -s /bin/bash "$username"
  if [[$? -eq 0]]
  then
  echo "The user $username was added successfully."
  tail -n 1 /etc/passwd
  else
  echo "There was an error adding the user."
  fi
