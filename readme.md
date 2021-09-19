```"Vagrant init" ``` to initialise the provisioning of virtual machines.

```"Vagrant up"``` to start your machines

```Vagrant ssh main ``` to access the main host. If it asks for password, password=Vagrant

Go into your vagrant folder and do ```sudo cp host /etc/hosts``` to copy over the the information contained in your local host file to your machine. 
Try to ping your machine ```ping server1``` you should be able to get a response.

