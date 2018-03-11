# Instructions
The purpose of the task is to program a static route to the IP of the lo:2 of the server (1.1.1.1) using YDK. Please create the actual loopback using:

`sudo ifconfig lo:2  1.1.1.1 netmask 255.255.255.255 up`

Open the notebook staticRoute.ipynb on the Jupyter server for the instructions.

# Ansible
We'll use the static route exercise as an example of how to integrate YDK into an Ansible module. 

The task is to fill the module file module_static.py with the code needed to apply a static route to the router. The code is similar to the one in Notebook. You can check the file module_static_solution.py if you want a proposed solution.

## Installing and preparing Ansible
To follow this exercise, please enter the server and install Ansible:

1. Add the DNS to the server (if you haven't already):
  * `sudo vim /etc/resolv.conf`. Add the line nameserver 198.18.133.1 .
2. Install ansible:
  * `sudo apt-add-repository ppa:ansible/ansible`
  * `sudo apt-get update`
  * `sudo apt-get install ansible`
3. `ansible --version` should work.
4. Configure the server as local:
  * `sudo vim /etc/ansible/hosts`
  * Enter: ```
[local]
127.0.0.1
```
5. `export ANSIBLE_LIBRARY=/home/vagrant/notebooks/SDNMeetupYDK/StaticRoute/ansible/`

The file add_loopback_in_server.yml is an Ansible playbook that uses the module to configure a local loopback and configures the static route in the router. 
It then tests that the procedure was successful using a ping. Analyze it if possible.

To run the playbook use:

`ansible-playbook add_loopback_in_server.yml --extra-vars "address=1.1.1.1"`

