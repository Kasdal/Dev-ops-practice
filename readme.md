# Microservices Dev-Ops Project.
> Simple python project using multiple VM machines to create a microservices for basic app.
> <hr>

## Table of Contents
* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Features](#features)
* [Step-by-step Instructions](#step-by-step-instructions)
* [Project Status](#project-status)
* [Room for Improvement](#room-for-improvement)


## General Information
- Fairly simple take on microservices running on multiple machines.
- Main purpose is to learn more and familiarize one self with the possibilities of infrastructure as code.
<!-- You don't have to answer all the questions - just the ones relevant to your project. -->


## Technologies Used
- Git
- Vagrant
- Virtual Box, Vmware or other
- Ansible
- Docker 
- Docker Compose
- Docker Swarm


## Features
List the ready features here:
- Infrastructure as code ready to deploy
- Automated software instalation 
- Containerization
- Orchestration
##
### ✅  Step-by-step Instructions
Download the project to your local machine and open it in VSCode, PowerShell or some other IDE.
Open a terminal in VSCode
<hr>
Start by running the following commands

```
"Vagrant init" 
```
to initialise the provisioning of virtual machines.

```
"Vagrant up"
```
to start your machines

```
Vagrant ssh main 
``` 
to access the main host. If it asks for password, password=Vagrant
##

Go into your vagrant folder and do
```
sudo cp host /etc/hosts
``` 
to copy over the the information contained in your local host file to your machine. 
Try to ping your machine
```
ping server1
``` 
you should be able to get a response.
##
While still in "main" machine do 
```
ssh-keygen
```
while creating ssh key leave it without the password.
Once the key is created you will need to copy it to other 3 servers.
```
ssh-copy-id server1 && ssh-copy-id server2 && ssh-copy-id server3
```
this will copy over the public key from main.
Once copied, test that you have ssh access to servers.
```
ssh vagrant@server1
```
it should connect to it without asking for password.
##
Now we can install and test our ansible capabilites
```
sudo apt install ansible
```
change directory to ansible 
```
cd ansible
```
##
run
```
ansible servers -i thehosts -m command -a hostname
``` 
You should get a response that it found "main" and get all 3 responses from servers
##
![img1](https://user-images.githubusercontent.com/36207533/134399268-1be85e24-5caf-4613-adf7-bc96c3a657ed.png)
##
If all of the tests passed, let's now have some fun and explore the power of ansible.
##
run
```
ansible servers -i thehosts -m command -a 'sudo apt-get -y install python-simplejson
``` 
Which will install python and json on all our servers allowing us to have more capabilities on those machines.
##
![img2](https://user-images.githubusercontent.com/36207533/134399272-11fef3e3-3349-40ee-bbe8-65ee45b0fd9f.png)
##
Ok so, let's run our ansible playbook and install docker on all 3 servers.
Running the following command on your "main" will do just that. 
```
ansible-playbook -i thehosts -K playbook1.yaml
```
##
![img4](https://user-images.githubusercontent.com/36207533/134399276-7a813231-2685-4bbd-9266-d23b9d6a70a5.png)

After we can run a quick script to make sure docker was properly installed.
Ssh into all servers and run 
```
docker run hello-world
```

Next we can fork this project https://github.com/nextrevision/ansible-swarm-playbook to get docker swarm on our system.
You will need to adjust couple of things to make it work, mainly the host inventory file and add a manager and worker node to it.
Also required is to change eth0 interface in swarm.yaml to eth1
##
![ansible-swarm](https://user-images.githubusercontent.com/36207533/134399263-e8782b0d-c767-4aee-b352-738fc9da8ef4.png)

Now we can go to one of the servers and verify that the cluster is created.
##
![swarm-rdy](https://user-images.githubusercontent.com/36207533/134399265-f621fd7e-88e9-4d10-a9fb-7f509ac3d2b1.png)

With all that done we can now run 
```
docker-stack deploy -- compose-file docker compose yaml myapp
```
Once the service is compiled you can check it's status 
```
docker service ps myapp_web
```
Next, let's now scale our application which is the main goal of this exercise.
Run
```
docker service scale myapp_web=10
```
this will scale our app to 10 containers spread over all 3 servers. 
And you can easily scale this up to 1000+ provided that your machines can hadle the load.
##
![End](https://user-images.githubusercontent.com/36207533/134399267-06d8600c-e6d1-4ecc-81a0-549725c52125.png)

Now go open another PowerShell, Terminal etc.. and ssh into main, 
```
cd /vagrant/ansible
```
and test that your services are actually running in multiple containers.
You can run curl server1:5000 or any other server and you can see that every time you run that command you will likely get a response from a container with different id.
#
![Test1](https://user-images.githubusercontent.com/36207533/134539052-23fee95f-4a4b-41ef-a3de-0f74de7472c4.png)
<hr>
You can adapt this project to run any other app by editing Dockerfile with your variation, make changes to requirements.txt, and docker-compose.yaml
You can then use the Dockerfile to build the image and host it on Dockerhub or similar service.

Enjoy!


<!--What are the project requirements/dependencies? Where are they listed? A requirements.txt or a Pipfile.lock file perhaps? Where is it located?

Proceed to describe how to install / setup one's local environment / get started with the project.-->



## Project Status
Project is: mostly done. 


## Room for Improvement

Room for improvement:
- Add monitoring by implementing Grafana, Prometheous or similar.
