Simple project using multiple VM machines to create a microservices for basic app. 
Tools utilized in this project include: Git, Virtual Box, Vagrant, Ansible, Docker, Docker Compose, Docker Swarm.
<hr>

Start by running the following commands

```"Vagrant init" ``` to initialise the provisioning of virtual machines.

```"Vagrant up"``` to start your machines

```Vagrant ssh main ``` to access the main host. If it asks for password, password=Vagrant
<br>

Go into your vagrant folder and do ```sudo cp host /etc/hosts``` to copy over the the information contained in your local host file to your machine. 
Try to ping your machine ```ping server1``` you should be able to get a response.

While still in "main" machine do ```"ssh-keygen" ``` while creating ssh key leave it without the password.
Once the key is created you will need to copy it to other 3 servers.
```ssh-copy-id server1 && ssh-copy-id server2 && ssh-copy-id server3``` this will copy over the public key from main.
Once copied, test that you have ssh access to servers. ```ssh vagrant@server1``` it should connect to it without asking for password.


# Project Name
> Simple project using multiple VM machines to create a microservices for basic app.

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
- Main purpose is to learn more and familirize one with the possibilities of infrastructure as code.
- Why did you undertake it?
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
- Awesome feature 1
- Awesome feature 2
- Awesome feature 3


## Screenshots
![Example screenshot](./img/screenshot.png)
<!-- If you have screenshots you'd like to share, include them here. -->


## Setup
What are the project requirements/dependencies? Where are they listed? A requirements.txt or a Pipfile.lock file perhaps? Where is it located?

Proceed to describe how to install / setup one's local environment / get started with the project.


## Usage
How does one go about using it?
Provide various use cases and code examples here.

`write-your-code-here`


## Project Status
Project is: _in progress_ / _complete_ / _no longer being worked on_. If you are no longer working on it, provide reasons why.


## Room for Improvement
Include areas you believe need improvement / could be improved. Also add TODOs for future development.

Room for improvement:
- Improvement to be done 1
- Improvement to be done 2

To do:
- Feature to be added 1
- Feature to be added 2


## Contact
Created by
