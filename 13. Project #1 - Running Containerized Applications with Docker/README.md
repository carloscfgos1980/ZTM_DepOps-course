## Chapter 13. Project #1 - Running Containerized Applications with Docker

# Lesson 1. Project Overview

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32891304

# Lesson 2. What is Docker? Why use it?

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32891305

- Check <virtual machine and docker> diagram

# Lesson 3. Installing Docker

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32891307

- I follow this tutorial instead!
  https://www.youtube.com/watch?v=cqbh-RneBlk

# Lesson 4. The Docker Client

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32891308

- Docker version
  docker --version

\_Get help in Docker
docker --help

# Lesson 5. Pulling Images and Running Containers

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32891310

# Lesson 6. Lab: Running a Web Server in a Docker Container

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32891311

# Lesson 7. Listing Images and Containers

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32891313

# Lesson 8. Removing Images and Containers

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32891314

- Remove all not used containers
  docker system prune

* There is also the explanation how to remove a single container

# Lesson 9. Getting Shell Access to a Container

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32891316

# Lesson 10. Executing Commands in a Running Container

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32891317

# Lesson 11. Getting Information about the Running Containers

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32891319

- Remove all the containers from docker:
  sudo docker container rm -f $(docker container ls -a -q)

- Start nginx server:
  sudo docker container run -d -p 8080:80 --name=mysite nginx

- Check the container's port
  duo docker container port gnix

- Check the local internet conection:
  ip a

* Copy the address: 192.178.168.72

Check the docker image in a browser:
192.178.168.72:80

- Check the logs:
  sudo docker container logs mysite

- Check the logs in real time:
  sudo docker container logs -f mysite

- Check the process:
  sudo docker container top mysite

- Real time info about all running containers:
  sudo docker container stats

- Getting container ip address:
  sudo docker container inspect | grep -i ipaddress

# Lesson 12. Committing Container Changes into a New Image

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32891321

- Check all the containers (running or stopped)
  sudo container ls -a

- Commit the change:
  sudo docker commit -m "file created" -a "Carlos Infante" 8f50 carlosinfante1980/my_centos:latest

[8f50] are the first 4 digits of the container Id

- Name of my docker profile:
  carlosinfante1980

# Lesson 13. Tagging and Pushing Custom Images to Docker Hub

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32891322

- Change a tag:
  sudo docker image tag carlosinfante1980/my_centos:latest carlosinfante1980/my_centos:1.0

* The tag is changed into 1.0. I need to provide the current image name and tag as first argument anf then the new one as second argument

- Push an image:

1. Login:
   sudo docker login

- enter user and password

2. push the image
   sudo docker image push carlosinfante1980/my_centos:1.0

- Image is there. Checked!

# Lesson 14. Image Structure and Layers

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32891323

# Lesson 15. Creating Custom Images using Dockerfile

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32891325

- Something did not work here. I think it is because I didn't pay shit..hahaha

# Lesson 16. Persistent Data: Volumes

https://academy.zerotomastery.io/courses/devops-bootcamp/lectures/32891334
