# Microservices Dev-Ops Project.
> Simple python project using multiple VM machines to create a microservices for basic app.
> <hr>

## Table of Contents
* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Features](#features)
* [Screenshots](#screenshots)
* [Setup](#setup)
* [Usage](#usage)
* [Project Status](#project-status)
* [Room for Improvement](#room-for-improvement)
* [Contact](#contact)


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
## Setup
Download the project to your local machine and open it in VSCode, PowerShell or some other IDE.
Open a terminal in VSCode
<hr>
Start by running the following commands

```"Vagrant init" ``` to initialise the provisioning of virtual machines.

```"Vagrant up"``` to start your machines

```Vagrant ssh main ``` to access the main host. If it asks for password, password=Vagrant
##

Go into your vagrant folder and do ```sudo cp host /etc/hosts``` to copy over the the information contained in your local host file to your machine. 
Try to ping your machine ```ping server1``` you should be able to get a response.
##
While still in "main" machine do ```"ssh-keygen" ``` while creating ssh key leave it without the password.
Once the key is created you will need to copy it to other 3 servers.
```ssh-copy-id server1 && ssh-copy-id server2 && ssh-copy-id server3``` this will copy over the public key from main.
Once copied, test that you have ssh access to servers. ```ssh vagrant@server1``` it should connect to it without asking for password.
##
Now we can install and test our ansible capabilites
```sudo apt install ansible```
change directory to ansible ```cd ansible```
##
run ```ansible servers -i thehosts -m command -a hostname``` 
You should get a response that it found "main" and get all 3 responses from servers
##
![img1](https://user-images.githubusercontent.com/36207533/134399268-1be85e24-5caf-4613-adf7-bc96c3a657ed.png)
##
If all of the tests passed, let's now have some fun and explore the power of ansible.
##
![img2](https://user-images.githubusercontent.com/36207533/134399272-11fef3e3-3349-40ee-bbe8-65ee45b0fd9f.png)
##
run ```ansible servers -i thehosts -m command -a 'sudo apt-get -y install python-simplejson'``` 
which will install python and json on all our servers allowing us to have more capabilities on those machines.
##
![img3](https://user-images.githubusercontent.com/36207533/134399273-a1243212-6d6f-43bb-91db-6f57cfe6c90a.png)
##

## Screenshots


##
![img4](https://user-images.githubusercontent.com/36207533/134399276-7a813231-2685-4bbd-9266-d23b9d6a70a5.png)
##
![img5](https://user-images.githubusercontent.com/36207533/134399254-4ebe4010-8de4-4630-b9cd-e8a28a789f90.png)
##
![img6](https://user-images.githubusercontent.com/36207533/134399256-4eadd491-fb11-42dc-870c-6bf91f52532f.png)
##
![img7](https://user-images.githubusercontent.com/36207533/134399258-fd5e216e-0365-467f-8034-4afc5de695b5.png)
##
![img8](https://user-images.githubusercontent.com/36207533/134399261-d17b36a7-d41b-46d1-bdc0-50c2a65a7d86.png)
##
![img9](https://user-images.githubusercontent.com/36207533/134399262-93804294-ac79-4cc6-88bf-dd469c7e36f2.png)
##
![ansible-swarm](https://user-images.githubusercontent.com/36207533/134399263-e8782b0d-c767-4aee-b352-738fc9da8ef4.png)
##
![swarm-rdy](https://user-images.githubusercontent.com/36207533/134399265-f621fd7e-88e9-4d10-a9fb-7f509ac3d2b1.png)
##
![End](https://user-images.githubusercontent.com/36207533/134399267-06d8600c-e6d1-4ecc-81a0-549725c52125.png)
<hr>

<!--What are the project requirements/dependencies? Where are they listed? A requirements.txt or a Pipfile.lock file perhaps? Where is it located?

Proceed to describe how to install / setup one's local environment / get started with the project.-->


<!--## Usage
How does one go about using it?
Provide various use cases and code examples here.

`write-your-code-here`-->


## Project Status
Project is: _in progress_


<!-- ## Room for Improvement
Include areas you believe need improvement / could be improved. Also add TODOs for future development.

Room for improvement:
- Improvement to be done 1
- Improvement to be done 2

To do:
- Feature to be added 1
- Feature to be added 2 


## Contact
Created by -->
