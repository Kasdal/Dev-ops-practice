Start by running the following commands

```"Vagrant init" ``` to initialise the provisioning of virtual machines.

```"Vagrant up"``` to start your machines

```Vagrant ssh main ``` to access the main host. If it asks for password, password=Vagrant
br>

Go into your vagrant folder and do ```sudo cp host /etc/hosts``` to copy over the the information contained in your local host file to your machine. 
Try to ping your machine ```ping server1``` you should be able to get a response.

While still in "main" machine do ```"ssh-keygen" ``` while creating ssh key leave it without the password.
Once the key is created you will need to copy it to other 3 servers.
```ssh-copy-id server1 && ssh-copy-id server2 && ssh-copy-id server3``` this will copy over the public key from main.
Once copied test that you have ssh access to servers. ```ssh vagrant@server1``` it should connect to it without asking for password.
