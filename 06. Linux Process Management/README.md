## Chapter 06. Linux Process Management

# Lesson 1. Processes and The Linux Security Model

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32728380

There are 2 types of commands in Linux:

- Executable commands files on the disk (eg: ls)
- Shell builtin commands (eg: cd)

* To check the type of commands, eg: type ls, type cd

- Check process and id:
  ps -ef | less

* First process is init: /sbin/init

- Several threads can be run in a same process, sharing memory and resources. This s applied to make the process more responsive. For example while using and text edit app, there could be threads for spell heck, auto complete, etc

# Lesson 2. Listing Processes (ps, pstree)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32728382

- Run ps. It shows:
  PID => process Id. It is the Id given by the kernel to identify the process
  TTY => represents the name of the controller terminal for the process
  TIME => it is the accumulated time in the process, shown in minutes and seconds
  CMD => name of the command that it was used to start the process

- Run: ps -e. It displays all process that are running
- Run: ps -f. Full status information. It displays the tail information abojt the processes
- Check how many processes are running (185 at tha moment):
  ps -ef | wc -l

- check the the first processes:

ps -ef | less

UID => user who runs the process
PID => process Id
PPID => parent process Id
TTY => represents the name of the controller terminal for the process. If the column display a question mark, it means that are process that run in the background and are not interactive. This are called "daemon"

- For extra info. Run:
  ps -aux | less
  %CPU => CPU utilization of the process
  %MEN => how much memory the process is using
  VSZ => Virtual memory side in kilobits, it includes all the memory
  RSS => size of the physical memory that the process is using
  Stat => Indicates the process state: Possible states (S- sleeping, r- running, z- zombi, T- stopped, I - idle kernel thread)

  - Show the info sorting in ascending order by memory used:
    ps -aux --sort=%mem | less

  - Show the info sorting in descending order by memory used:
    ps -aux --sort=-%mem | less

- Check the processes for a specific user:
  ps -f -u carlosinfante

- Check if a specific process is running:
  ps -ef | grep sshd

- It could be also:
  pgrep sshd

- You can search for a process by a certain user
  pgrep -u root sshd

- Another command display hierchical tree structure of all running processes
  pstree | less

# Lesson 3. Getting a Dynamic Real-Time View of the Running System (top, htop)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32728384

<top> command show 2 areas:

- Summery
- Tasks (processes list)

# Lesson 4. Signals and Killing Processes (kill, pkill, killall, pidof)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32728385

# Lesson 5. Foreground and Background Processes

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32728386

- To run a process in the background we add "&", eg:
  sleep 20 &

- Run a process in the backgroung and save it into a file
  ping -c 1 google.com > /dev/null 2>&1 &

# Lesson 6. Job Control (jobs, fg, bg)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32728387

sleep 20&
sleep 25&

- Cjeck the running process:
  jobs -l

- Bring the process in the background to the foreground, eg (1 is the job id):
  fg%1

- Suspend a process (foreground): control + z
- Resume it in the background: bg%1

- When a terminal is closed, the proces is automatically killed. If we want to keep a process even when terminal is killed we run nohup command, eg:
  nohup ifconfig

* In this case, once the parent process (shell command) is killed, ifconfig is "adopted" by Linux
