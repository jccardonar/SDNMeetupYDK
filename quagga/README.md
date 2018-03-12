# Installing Quagga

Access the server using the instructions in the root folder of the repository.

Add the DNS to the server, if not present.

```
sudo apt-get update	
sudo apt-get install quagga
```

Enable the daemons:
`sudo vim /etc/quagga/daemons` 
Set zebra, isisd, ospfd, and bgpd to yes.

Copy the configuration files in the quagga folder:
```
sudo cp zebra.conf /etc/quagga/
sudo cp isisd.conf /etc/quagga/
sudo cp ospfd.conf /etc/quagga/
sudo cp bgpd.conf  /etc/quagga/
```

Restart the quagga service using:
`sudo /etc/init.d/quagga restart`

Access the different daemons using (the ports can be found in /etc/services):
* `telnet 127.0.0.1 2608` for ISIS
* `telnet 127.0.0.1 2604` for OSPF
* `telnet 127.0.0.1 2605` for BGP 
Password is sdn for all daemons (see config files).

