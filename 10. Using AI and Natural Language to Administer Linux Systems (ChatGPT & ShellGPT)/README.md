## Chapter 10. Using AI and Natural Language to Administer Linux Systems (ChatGPT & ShellGPT)

# Lesson 1. Project Introduction

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/46250629

# Lesson 2. Installing and Configuring ShellGPT

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/49979118

- Check python version:
  python3 --version

- Install pip:
  sudo apt install python3-pip

- Check pip version
  pip3 --version

- Install venv:
  sudo apt install python3-venv

<venv> => virtual environment

- Create a directory (shellgpt):
  mkdir shellgpt

- Go to this directory:
  cd shellgpt

- run command to create vitual environment for GPT
  python3 -m venv gpt_cli

- Move to gpt_cli
  cd gpt_cli

- Activate:
  source bin/activate

- Install shell gpt
  pip3 install shell-gpt

- Create an account for Chapt GPT:
  Browser:
  https://platform.openai.com/signup

- create environment variable
  export OPENAI_API_KEY=[api_key created openai offitial website]

- Check the variable was created:
  env | grep -i openai

- To keep the variable after closing the section:
  vim ~/.bashrc

# Lesson 3. Using ShellGPT Like a Pro

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/46250631

- Check all commands
  chatgpt
  sgpt --help

- Get answer for the shell, eg:
  sgpt --shell "update my system"

- Execute the command:
  sgpt --shell --execute "update my system"
  sgpt -s -e "update my system"

- Check for code
  sgpt --code "Bash code that prompt user for a directory and then create an archieve of that directory. Also checks if directory exists"

- Check for code and redirect
  sgpt --code "Bash code that prompt user for a directory and then create an archieve of that directory. Also checks if directory exists" > backyp_dir.sh

# Lesson 4. The Chat Feature of ShellGPT

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/46250632

- This shit is not working. I need to pay... and I won't!
