The objective of this task is to perform the basic configuration of BGP on the XRv router.

Make sure that there is connectivity between the loopbacks of the server and the router. Run the Introduction and Static Route tasks before this one to make sure that the router can reach the server's loopback. 

**Important!**
You should also add a static route on the server to make sure it can reach the router's loopback:
`sudo ip route add 1.1.1.3/32 via 192.168.10.4 dev eth1`

`ping -I 1.1.1.1 1.1.1.3` must be running fine.

Follow the instructions in the Jupyter notebook for details.

If you want to test your config, you can use quagga in the server. Follow the instructions in the quagga folder.

To check that the configuration on both devices  is correct:

* Enter the BGP daemon (see instructions in the quagga folder)
* `show bgp neighbor` should show the session with the XR router (1.1.1.1) as "Established".
