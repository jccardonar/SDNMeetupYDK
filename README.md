# Introduction
This repository contains the instructions and code for the workshop [Controlando dispositivos con Python y YDK](https://www.meetup.com/es-ES/SDN-and-Network-Programmability-Meetup-in-Barcelona/events/248055664/)  presented in the [SDN and Network Programmability Meetup in Barcelona](https://www.meetup.com/es-ES/SDN-and-Network-Programmability-Meetup-in-Barcelona).

# Requirements
This code was designed to be used with the session "A Practical Approach to SP Programmability Lab v1" from [the Cisco dCloud](https://dcloud.cisco.com/). Participants to the workshop will get access to this session in the meetup. 

For use outside of the meetup, please try to schedule your own session (you must be registered). Alternatively, get access to a virtual XR router, enable netconf on it, and change any connectivity variables in the notebooks.

**Note:** The code in this repository serves as an alternative set of instructions to the ones provided in the session. We recommend that people also try the original notebooks of the session.

# Instructions

The lab consists on a server which runs the [Jupyter](http://jupyter.org/) server, and the router. The scheme of the lab is included in the slides.

The guide for the workshop is contained in the different Jupyter notebooks within this repository. The objective of each notebook is to do a configuration of different aspects of the router. 

The recommend order for notebooks is:
1. Start with Introduction.ipynb.
2. Continue with the StaticRoute/staticRoute.ipynb. 
  * Note that this part includes an optional exercise with ansible.
3. After that, choose any of the notebooks in the folders BGP, OSPF or ISIS.

For each notebook, you should check in the router that whatever you configured is reflected in the configuration. Optionally, you can configure a quagga router in the server to test that your configuration works with other devices. To do this, just follow the instructions on the quagga folder. 

## How to run the notebooks

Get connectivity access to the lab using anyconnect, or the remote desktop option (see slides). 

Access the server using the instructions in the next section. After that, configure the DNS in the server using:

`sudo vim /etc/resolv.conf` 

Add the line `nameserver 198.18.133.1`.

Enter the Jupyter folder and Download this repo to the server: 
* `cd /home/vagrant/local_notebook`
* `git clone https://github.com/jccardonar/SDNMeetupYDK.git`

## How to access the Lab elements.

To access the Jupyter hub, enter the address http://198.18.128.101:8888/tree in a browser. Enter in the local_notebook folder.

For access to the server:
* SSH IP 198.18.128.101 Port 2015. Use "vagrant" as u. and p.
* Use the "Program. VM" icon in the remote desktop.

To get access to the router:
* SSH 198.18.128.101 Port 2014. Use "vagrant" as u. and p.
* If using remote, use the "XR VM" icon in the desktop.
