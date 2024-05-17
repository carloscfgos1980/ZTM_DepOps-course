## Chapter 12. Setting Up the Environment for the Hands-On Projects

# Lesson 1. Running a Linux Server in the Cloud

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32890788

- I probably need to creat an account in this website. It is not free. It is a virtual private service in Virtual service cloud:
  https://cloud.digitalocean.com/login

# Lesson 2. Securing SSH with Key Authentication

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32890790

- Generate a ssh key
  ssh-keygen -t rsa -b 2048 -C 'key generated in 2024'

[-t rsa] => type of key
[-b 2048] => size. Amount of bits
[-C 'key generated in 2024'] => Comment

- Private key has been saved in: /home/carlosinfante/.ssh/id_rsa
- Public key has been saved in: /home/carlosinfante/.ssh/id_rsa.pub

- to check the ssh-key
  ls .ssh

* Later I had to add the ssh key
