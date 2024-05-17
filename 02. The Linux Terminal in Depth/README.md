## Capter 02. The Linux Terminal in Depth

# Lesson 1. Terminals, Consoles, Shells and Commands

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32682145

# Lesson 2. Linux Command Structure

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32682147

# Lesson 3. Getting Help, Man Pages (man, type, help, apropos)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32682148

Man Pages => stands for Manual Page

Terminator:

- Display help:
  man ls
- Get additional help:
  h
- Leave this screen:
  q
- LEave man ls:
  q

- Example of help syntax:
  ls [OPTION]...[FILE]
  N: The brackets means that it could be left out (not mandatory), ... means that could be more than one

- Check <help commands> diagram:
  When something is in bold, it shold be type exactly, when is underline or italic, then it must substitute with something appropiated

- Navegation:

1. line by line: arrow up or down to do it
2. window forward: tab
3. window backward: control + b
4. very beginning: g
5. very ending: G

- to find something based in a criteria I type: / followed by the criteria, eg:
  /sort
  Then you can navegate between matches, "n" to the next match and shitf+n (uppercaase of n) to the previous one.

- To check if a command exist, use type followed by the command, eg:
  type df

- To see the celp:
  help cd

- To get help about a command, we type the name of the command --help, eg:
  rm --help

- Check if "ifconfig" command is available, if not install it... I just did!

- to look for a command in the man page, there are 2 ways:
  man -k (name of the command), eg: man -k ifconfig
  apropos (name of the command), eg: apropos ifconfig

# Lesson 4. Mastering the Terminal: The TAB Key

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32682151

- Use the <tab> key for auto complition

For example, if It type ifc and tab it will auto complete ifconfig. But it there is more than one match then nothing happens, we need to pres <tab> again and it will show a list of the match commands

# Lesson 5. Mastering the Terminal: Keyboard Shortcuts

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32682152

Control + l => Clear
Control +d => Exit the Bash Shell
arrow up key => record previous command
control + a => Move the cursor to the beginning to the line
control + e => Move the cursor to the end of the line
control + u => delete the whole command line
control + c => stop a process (eg: download a large file)
control + z => continue a process that has halted

# Lesson 6. Mastering the Terminal: the Bash History

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32682154

- History
  cat .bash_history

- History File. This return 2000
  echo $HISTFILESIZE

- Print all the bash commands:
  history

- Print bash commands in memory. This return 1000
  echo $HISTSIZE

* So it will save 2000 commands in a file and 1000 in memory

- To run certain command, we can check the history and type !+number of that command

# Lesson 7. Running Commands Without Leaving a Trace

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32682157

# Lesson 8. Recording the Date and Time for Each Line in History

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/49979114

- Type this command in the bash shell, in order to show the timestand:
  HISTTIMEFORMAT="%d/%m/%y %T"

- Persist this format:
  echo 'HISTTIMEFORMAT="%d/%m/%y %T"' >> .bashrc

# Lesson 9. root vs. non-Privileged Users. Getting root Access (sudo, su, passwd)

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32682159
